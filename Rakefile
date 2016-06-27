#!/usr/bin/env ruby
# jekyll Rakefile
require 'rake'
require 'html/proofer'

desc 'Set default tasks'
task :default => [:proof_sitedir]

desc 'Test site using HTML::Proofer'
task :proof_sitedir do
  system 'bundle exec jekyll build'
  #system 'bundle exec htmlproof --url-ignore "/#.*/" ./_site'
#  HTML::Proofer.new("./_site").run
end
