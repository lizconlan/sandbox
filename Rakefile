# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require 'rake'
require 'rake/testtask'
require 'rake/rdoctask'

namespace :tags do
  desc 'Generates a page for each tag used on the site in the /tags folder'
  task :generate do
    puts 'Generating tags...'
    require 'rubygems'
    require 'jekyll'
    include Jekyll::Filters

    options = Jekyll.configuration({})
    site = Jekyll::Site.new(options)
    site.read_posts('')

    site.categories.sort.each do |category, posts|
      
      puts "generating tag: #{category}"
      
      html =<<-HTML
---
layout: default
title: Posts tagged #{category}
---

  <h2>Posts tagged #{category}</h2>

      HTML

      html << "<ul>"
    
      posts.each do |post|
        post_data = post.to_liquid
        html << <<-HTML
          <li>
            <div>#{date_to_string post.date}</div>
            <a href="#{post.url}">#{post_data['title']}</a>
          </li>
        HTML
      end
      html << '</ul>'

      File.open("tags/#{category}.html", 'w+') do |file|
        file.puts html
      end
    end
    puts 'Done.'
  end
end
