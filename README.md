Heroku buildpack: Ruby for RhoConnect apps
==========================================

This is a fork of [Heroku buildpack](https://github.com/Luxhaven/heroku-buildpack-ruby) for RhoConnect Ruby and JavaScript apps.
It includes the following vendored binaries: nodejs v0.10.20, bundler v1.3.5, ruby-1.9.3-p448, and ruby 2.0.0-p247.

Usage
-----

Example Usage:

    $ ls
    Gemfile   README    config.ru public    spec
    Gemfile.lock  Rakefile  controllers settings

    $ heroku create --buildpack https://github.com/rhomobile/heroku-buildpack-ruby

    $ git push heroku master
    ...
    -----> Fetching custom git buildpack... done
    -----> Ruby/Rack app detected
    -----> Using Ruby version: ruby-1.9.3
    -----> Installing dependencies using Bundler version 1.3.5
          Running: bundle install --without development:test --path vendor/bundle --binstubs vendor/bundle/bin --deployment
          Using rake (10.0.4)
          Using rack (1.5.2)
          ...
          Your bundle is complete!
          Gems in the groups development and test were not installed.
          It was installed into ./vendor/bundle
          Cleaning up the bundler cache.
    -----> WARNINGS:
          You have not declared a Ruby version in your Gemfile.
          To set your Ruby version add this line to your Gemfile:
          ruby '1.9.3'
          # See https://devcenter.heroku.com/articles/ruby-versions for more information."
    -----> Discovering process types
          Procfile declares types     -> (none)
          Default types for Ruby/Rack -> console, rake, web


The buildpack will detect your RhoConnect app as Rack as it has a `Gemfile` and `Gemfile.lock` files in the root directory. It will then proceed to run `bundle install` after setting up the appropriate environment for [ruby](http://ruby-lang.org) and [Bundler](http://gembundler.com). By default, it uses ruby `1.9.3`, unless you specify a particular version of Ruby in your app’s `Gemfile`. Also, binaries of nodejs `v0.10.20` will installed and be accessible by app at run time.

