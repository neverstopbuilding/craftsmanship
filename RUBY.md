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

##Code Quality Checking

###Rubucop
All projects should run an installation of the fantastic [Rubocop](https://github.com/bbatsov/rubocop) gem to check for code quality.

Add this to your `Gemfile` to get the latest version:

    gem 'rubocop', git: 'https://github.com/bbatsov/rubocop.git', branch: 'master'

Add this to your `Rakefile`

```Ruby
require 'rubocop/rake_task'

Rubocop::RakeTask.new
```

Prefered configuration on `.rubocop.yml`:

```YAML
LineLength:
  Enabled: false

MethodLength:
  Max: 30

SymbolName:
  AllowCamelCase: false
```

###Flog
Use [Flog](https://github.com/seattlerb/flog) to report code complexity:

```Ruby
require 'flog_task'


# Fail if total score is greater than 200
FlogTask.new :flog_total, 200 do |t|
  t.method = :total_score
  t.verbose = true
end

# Fail if average score is greater than 10
FlogTask.new :flog_average, 10 do |t|
  t.method = :average
  t.verbose = true
end
```

###Flay
Use[Flay](https://github.com/seattlerb/flay) to check for code duplication:

```Ruby
require 'flay_task'

# Fail if total score is greater than 200
FlayTask.new :flay, 200 do |t|
  t.verbose = true
  t.diff = true
end
```

###Reek
Use [Reek](https://github.com/troessner/reek) to check for code smells:

```Ruby
require 'reek/rake/task'

Reek::Rake::Task.new do |t|
    t.fail_on_error = true
    t.verbose = false
    t.reek_opts = '--quiet'
end
```
