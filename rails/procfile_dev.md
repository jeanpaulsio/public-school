# Using a Procfile.dev file with Foreman

## Problem

I have a bunch of servers that I need to start and so I end up opening
multiple tabs in iTerm for

- rails server
- redis server
- sidekiq
- webpack

## Solution

Procfile + Foreman

```bash
# Make sure you have foreman
# The docs say not to include it in your project's Gemfile
gem install foreman

# Create a Procfile specific for your dev env
touch Procfile.dev
```

Procfile contents:

```
web: bin/rails server -p 3000
webpack: yarn start
redis: redis-server
worker: bundle exec sidekiq -C config/sidekiq.yml
```

To start your servers in a single tab, just run the following:

```bash
foreman start -f Procfile.dev
```
