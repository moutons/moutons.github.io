#!/usr/bin/env ruby
# jekyll Rakefile
# Config variables above those defined in _config.yml
post_ext = '.md'
post_dir = '_posts/'
git_check = true
# load from configuration file if present
load '_rake-configuration.rb' if File.exist?('_rake-configuration.rb')
load '_rake_configuration.rb' if File.exist?('_rake_configuration.rb')
#
# OK now starting main engines
#
# Specify default values for variables NOT set by the user

post_ext ||= '.md'
post_dir ||= '_posts/'
git_check ||= true
git_autopush ||= false
#

desc 'Test site using HTML::Proofer'
task :proof_sitedir do
  system 'bundle exec jekyll build'
  # system 'bundle exec htmlproofer --allow-hash-href --assume-extension ./_site'
  HTMLProofer.check_directory(
    "./_site/",
    {
      :allow_hash_href => true,
      :assume_extension => true
    }
  ).run
end
#
# and the rest
#
desc 'Clean up generated site'
task :clean do
  cleanup
end

desc 'Preview on local machine'
task :preview => :clean do
  jekyll('serve --watch')
end
task :serve => :preview

desc 'Build for deployment'
task :build => :clean do
  if rake_running
    puts "\n\n****WARNING: An instance of rake is running.\n"
    puts "****WARNING: Building while running other tasks (preview!) might create a site with broken links.\n\n"
    puts "Are you certain you want to continue? [Y|n]"

    ans = STDIN.gets.chomp
    exit if ans != 'Y'
  end
  jekyll("build --config _config.yml")
end

desc 'Build and deploy to github'
task :deploy_github => :build do |t, args|
  args.with_defaults(:deployment_configuration => 'deploy')
  config_file = "_config_#{args[:deployment_configuration]}.yml"

  if git_requires_attention('master')
    puts "\n\nWarning! It seems that the local repository is not in sync with the remote.\n"
    puts "This could be ok if the local version is more recent than the remote repository.\n"
    puts "Deploying before committing might cause a regression of the website (at this or the next deploy).\n\n"
    puts "Are you sure you want to continue? [Y|n]"

    ans = STDIN.gets.chomp
    exit if ans != 'Y'
  end

  `git add -A && git commit -m "autopush by Rakefile at #{time}" && git push origin gh_pages` if git_autopush

  time = Time.new
  File.open('_last_deploy.txt', 'w') { |f| f.write(time) }
end

desc 'Create a post'
task :create_post, [:date, :title, :category, :content] do |t, args|
  if args.title.nil?
    puts "Error! title is empty"
    puts "Usage: create_post[date,title,category,content]"
    puts "DATE and CATEGORY are optional"
    puts "DATE is in the form: YYYY-MM-DD; use nil or empty for today's date"
    puts "CATEGORY is a string; nil or empty for no category"
    exit 1
  end

  if (args.date != nil && args.date != "nil" && args.date != "" && args.date.match(/[0-9]+-[0-9]+-[0-9]+/) == nil)
    puts "Error: date not understood"
    puts "Usage: create_post[date,title,category,content]"
    puts "DATE and CATEGORY are optional"
    puts "DATE is in the form: YYYY-MM-DD; use nil or the empty string for today's date"
    puts "CATEGORY is a string; nil or empty for no category"
    puts ""

    title = args.title || "title"

    puts "Examples: create_post[\"\",\"#{args.title}\"]"
    puts "          create_post[nil,\"#{args.title}\"]"
    puts "          create_post[,\"#{args.title}\"]"
    puts "          create_post[#{Time.new.strftime("%Y-%m-%d")},\"#{args.title}\"]"
    exit 1
  end

  post_title = args.title
  post_date = (args.date != '' and args.date != 'nil') ? args.date : Time.new.strftime("%Y-%m-%d %H:%M:%S %Z")

  # the destination directory is <<category>>/$post_dir, if category is non-nil
  # and the directory exists; $post_dir otherwise (a category tag is added in
  # the post body, in this case)
  post_category = args.category
  if post_category and Dir.exist?(File.join(post_category, post_dir))
    post_dir = File.join(post_category, post_dir)
    yaml_cat = nil
  else
    post_dir = post_dir
    yaml_cat = post_category ? "category: #{post_category}\n" : nil
  end

  def slugify(title)
    # strip characters and whitespace to create valid filenames, also lowercase
    return title.downcase.strip.tr(' ', '-').tr(/[^\w-]/, '')
  end

  filename = post_date[0..9] + '-' + slugify(post_title) + post_ext

  # generate a unique filename appending a number
  i = 1
  while File.exist?(post_dir + filename)
    filename = post_date[0..9] + '-' +
               File.basename(slugify(post_title)) + "-" + i.to_s +
               post_ext
    i += 1
  end

end

desc 'Create a post listing all changes since last deploy'
task :post_changes do |t, args|
  content = list_file_changed
  Rake::Task['create_post'].invoke(Time.new.strftime("%Y-%m-%d %H:%M:%S"), 'Recent Changes', nil, content)
end

desc 'Show the file changed since last deploy to stdout'
task :list_changes do |t, args|
  content = list_file_changed
  puts content
end

def list_file_changed
  content = "Files changed since last deploy:\n"
  IO.popen('find * -newer _last_deploy.txt -type f') do |io|
    while (line = io.gets)
      filename = line.chomp
      if user_visible(filename)
        content << "* \"#{filename}\":{{site.url}}/#{file_change_ext(filename, '.html')}\n"
      end
    end
  end
  content
end

# this is the list of files we do not want to show in changed files
EXCLUSION_LIST = [/.*~/,
                  /_.*/,
                  'javascripts?',
                  'js',
                  /stylesheets?/,
                  'css',
                  'Rakefile',
                  'Gemfile',
                  /s[ca]ss/,
                  /.*\.css/,
                  /.*.js/,
                  'bower_components',
                  'config.rb']

# return true if filename is "visible" to the user (e.g., it is not javascript, css, ...)
def user_visible(filename)
  exclusion_list = Regexp.union(EXCLUSION_LIST)
  !filename.match(exclusion_list)
end

def file_change_ext(filename, newext)
  if File.extname(filename) == '.textile' || File.extname(filename) == '.md'
    filename.sub(File.extname(filename), newext)
  else
    filename
  end
end

#
# General support functions
#

# remove generated site
def cleanup
  jekyll('clean')
end

# launch jekyll
def jekyll(directives = '')
  system 'bundle exec jekyll ' + directives
end

# check if there is another rake task running (in addition to this one!)
def rake_running
  `pgrep rake | wc -l`.to_i > 1
end

def git_local_diffs
  `git diff --name-only` != ''
end

def git_remote_diffs(branch)
  `git fetch`
  `git rev-parse #{branch}` != `git rev-parse origin/#{branch}`
end

def git_repo?
  `git status` != ''
end

def git_requires_attention(branch)
  git_check && git_repo? && git_remote_diffs(branch)
end

#
# default task stuff
#
require 'rake'
require 'html-proofer'
require 'rubocop/rake_task'

RuboCop::RakeTask.new

desc 'Set default tasks'
task :default => :proof_sitedir
