# jekyll Rakefile
require 'rake'

desc 'Set default tasks'
task :default => [:proof_sitedir]

desc 'Test site using HTML::Proofer'
task :proof_sitedir do
  require 'htmlproofer'
  system 'bundle exec jekyll build'
  HTML::Proofer.new("./_site").run
end
