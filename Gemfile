source "http://rubygems.org"

# Always is compitable with Github Pages gem versions
require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem 'github-pages', versions['github-pages']
gem "jekyll", versions['jekyll']


# Gems for developement
gem 'rake'
gem 'iconv'
gem 'term-ansicolor'
gem 'directory_watcher'