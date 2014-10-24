---
layout: post
title: "Using Jekyll with Rake"
date: "2014-10-27"
tags: rake ruby jekyll
---

### Jekyll

Jekyll is a blogging platform, actually you are seeing it in action right now.
This whole site is build on top of jekyll.

Jekyll uses partials and layouts like Rails does, but its especially good with blog posts.
It supports sass and liquid so you can make and style pages with ease.
Jekyll compiles all your web-logic to a folder named `_site` from there it is a static site.
Ready to be deployed anywhere.

GitHub pages supports Jekyll that means you can easily upload your Jekyll site to a repository
and GitHub will host it for you.

However Jekyll lacks some functionality, like what if you want to include tags in your posts,
Or what if you want
This is where Rake comes to play.
If

### Rake

Rake is a Make implementation in Ruby. What it actually is, is a tasks manager,
you tell Rake what you want to do and how, and it will do it for you, whenever you
ask. That can be extremely usefull when you want to automate certain tasks for your
website (or any tasks that is).

Rake knows how to use shell commands and (ofcourse) knows ruby. Lets see what we can do
with these tools.

### Jekyll and Rake

To give you an idea of how you can automate task for your benefit in Jekyll I will walk you
through some code I found when I wanted to implement tags in Jekyll.
The code was written by Leon Bradley so I claim no copywrite.

First lets see the whole code.


{% highlight ruby %}
{% raw %}
desc 'Generate tags pages'
task :tags => :tag_cloud do
  puts "Generating tags..."
  require 'rubygems'
  require 'jekyll'
  include Jekyll::Filters

  options = Jekyll.configuration({})
  site = Jekyll::Site.new(options)
  site.read_posts('')

  FileUtils.rm_rf("tag")

  site.tags.sort.each do |tag, posts|
    html = <<-HTML
---
layout: tag
title: "#{tag}"
---
{% for post in site.posts %}
  {% for tag in post.tags %}
    {% if tag == "#{tag}" %}
      {% include teaser.html %}
    {% endif %}
  {% endfor %}
{% endfor %}
HTML
    FileUtils.mkdir_p("tag/#{tag}")
    File.open("tag/#{tag}/index.html", 'w+') do |file|
      file.puts html
    end
  end
  puts 'Done.'
end

desc 'Generate tags pages'
task :tag_cloud do
  puts 'Generating tag cloud...'
  require 'rubygems'
  require 'jekyll'
  include Jekyll::Filters

  options = Jekyll.configuration({})
  site = Jekyll::Site.new(options)
  site.read_posts('')

  html = "<ul class=\"tag-cloud\">\n"
  max_count = site.tags.map{|t,p| p.count}.max
  site.tags.sort.each do |tag, posts|
    s = posts.count
    font_size = ((2 - 0.8*(max_count-s)/max_count)*2).to_i/2.0
    html << "\t<li><a href=\"/tag/#{tag}\" title=\"Posts tagged with #{tag}\" style=\"font-size: #{font_size}em; line-height:#{font_size}em\">#{tag}</a></li>\n"
  end
  html << '</ul>'
  File.open('_includes/tag-cloud.html', 'w+') do |file|
    file.puts html
  end
  puts 'Done.'
end
{% endraw %}
{% endhighlight %}
