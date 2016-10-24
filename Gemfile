source "http://rubygems.org"
ruby '2.3.0'

# Always is compitable with Github Pages gem versions
require 'json'
require 'open-uri'
begin
  versions = JSON.parse(open('https://pages.github.com/versions.json').read)
rescue
  versions = {
    'github-pages': '98',
    'jekyll': '3.2.1'
  }
end

gem 'github-pages', versions['github-pages']
gem "jekyll", versions['jekyll']
gem 'rdiscount'


# Gems for developement
gem 'bourbon'
gem 'neat'
gem 'rake'
gem 'iconv'
gem 'term-ansicolor'
gem 'directory_watcher'
