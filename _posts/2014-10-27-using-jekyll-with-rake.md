---
layout: post
title: "Semi dynamic website with Jekyll and Rake (Unfinished)"
date: "2014-10-27"
tags: blogging
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

However Jekyll lacks some functionality, since it compiles to a static website,
you can not use Ruby for controllers, routers and models. And that poses a problem
if you want some dynamic functionality in your website.

### Rake

Rake is a Make implementation in Ruby. What it actually is, is a tasks manager,
you tell Rake what you want to do and how, and it will do it for you, whenever you
ask. That can be extremely usefull when you want to automate certain tasks for your
webapp (or any tasks that is).

If you have used Rails or some other Ruby framework chances are you already encountered
Rake. Does `rake db:migrate` bring any memories? In fact even `rails generate` uses rake.

Rake knows how to use shell commands and (ofcourse) understands Ruby.
Like Rubygems Rake uses a file name `Rakefile`. Inside the `Rakefile` you write your
tasks, and then you "command" Rake to execute those tasks through your Terminal.

Now lets see what we can do with these two.

### Semi-Dynamic content with Jekyll and Rake

To give you an idea of how you can build semi dynamic content in Jekyll I'll walk you
through some code I found when I wanted to implement tags to this website.
The code was written by Leon Bradley so I claim no copywrite.

Since we want out end result to be static

First lets see the 'snippet' of code that generates tags based on my posts.


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

{% highlight elixir %}
{% raw %}
defmodule Some do
  use other
  
  def sddsa do
  end

end
{% endraw %}
{% endhighlight %}
