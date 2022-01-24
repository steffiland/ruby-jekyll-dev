## Basis docker-compose für Ruby Testumgebung

Beispielsweise für Jekyll-Seite Testumgebung

Source: https://anonoz.github.io/tech/2021/01/10/rails-docker-compose-yml.html

## Quick Howto

Now you will need to run bundle install in a separate step to get the gems:

```bash
docker-compose build
docker-compose run --rm web bundle 
##                or      bundle install whatever # to create a Gemfile
##     or /bin/sh  to get shell access
```


### Beispiel Jekyll: 

Gemfile z.B. [das hier](https://raw.githubusercontent.com/maximevaillancourt/maximevaillancourt.com/master/Gemfile) unter `myapp/`ablegen:

```
# frozen_string_literal: true

source "https://rubygems.org"

git_source(:github) {|repo_name| "https://github.com/#{repo_name}" }

gem "jekyll", "~> 4.2"
gem "jekyll-redirect-from", "~> 0.15"
gem "jekyll-last-modified-at"
gem "nokogiri"
```

* Run command  `bundle` to install dependencies from Gemfile into `./bundler_gems`
* Run command `bundle exec jekyll serve --host 0.0.0.0 [--port 4000] [--trace|-t] [-c path/to/_config.yaml]` to build the site and serve it locally  (static site stuff in `./myapp/`)
  * alternativ `docker-compose run -d web <command>`  wenn der richtige Befehl im compose-file steht.
* Browse to http://localhost:4000

