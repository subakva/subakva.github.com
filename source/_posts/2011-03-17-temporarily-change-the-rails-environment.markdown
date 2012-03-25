---
date: '2011-03-17 14:00:29'
layout: post
slug: temporarily-change-the-rails-environment
status: publish
title: Temporarily Change the Rails Environment
wordpress_id: '3923566388'
categories:
- regular
---

A helper method to change the Rails environment within a block. I use this for testing isolated, environment-specific methods. Obviously, I wouldn't suggest using this outside of test code. You could easily do something very stupid.


    
    
    <code>
    def with_rails_env(environment, &block)
      begin
        original_env = Rails.env
        Rails.instance_variable_set(:@_env, environment)
        yield if block_given?
      ensure
        Rails.instance_variable_set(:@_env, original_env)
      end
    end
    </code>
    
