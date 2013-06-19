##Ruby Versioning
Use the new style RVM files to specify a specific Ruby version and Gemset on a per project basis as detailed [here](https://rvm.io/workflow/projects).

Example:

    rvm --create --ruby-version use 1.9.3@my-project-name

##Gemfiles
Gemfiles should include the Ruby version and lock down the Gem version as much as possible. Running `bundle update` should always be predictable and never break existing code.

Example:

    source 'https://rubygems.org'
    ruby '1.9.3'

    gem 'sinatra', '~> 1.4.3'
