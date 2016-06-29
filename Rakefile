#!/usr/bin/env ruby
# jekyll Rakefile
require 'rake'
require 'html-proofer'

desc 'Set default tasks'
task :default => [:proof_sitedir]

desc 'Test site using HTML::Proofer'
task :proof_sitedir do
  system 'bundle exec jekyll build'
  #system 'bundle exec htmlproofer --allow-hash-href --assume-extension ./_site'
  HTMLProofer.check_directory("./_site/", {
    :allow_hash_href => true,
    :assume_extension => true
  }).run
end
