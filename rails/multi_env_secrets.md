# Multi Environment Secrets (Rails 6)

- Rails will detect which set of credentials to use for a given environment.
Environment-specific variables take precedence over global ones.

```bash
rails credentials:edit --environment production
```

- This creates a `config/credentials/production.key` file and automatically
appends it to your `.gitignore`. This also creates `config/credentials/production.yml.enc`
which is added to version control.

- Rails will look for either `RAILS_MASTER_KEY` or `RAILS_PRODUCTION_KEY`.
If either of these are set, we don't need a `*.key` file.

- The same is true for Heroku and CircleCI - just set `RAILS_MASTER_KEY`

- To access credentials in your app, you can do:

```bash
Rails.application.credentials
```
