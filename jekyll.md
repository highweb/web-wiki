---
layout: base
title: Jekyll howtos
---

```sh
# Build and watch:
jekyll build --watch
```


## Using a theme

`_config.yml`:
```
theme: THEME
```

`Gemfile`:
```
source 'https://rubygems.org' do
  gem 'jekyll'
end

gem 'THEME', :path => './theme'
```


## Creating a theme

`Gemfile`:
```
source "https://rubygems.org"
gemspec
```

`THEME.gemspec`:
```rb
# coding: utf-8

Gem::Specification.new do |spec|
  spec.name          = "THEME"
  spec.version       = "0.1.0"
  spec.authors       = ["AUTHOR"]
  spec.email         = ["EMAIL"]

  spec.summary       = "THEME"
  spec.homepage      = "https://..."
  spec.license       = "MIT"

  spec.files         = `git ls-files -z`.split("\x0").select { |f| f.match(%r{^(assets|_layouts|_includes|_sass|LICENSE|README)}i) }

  spec.add_development_dependency "jekyll", "~> 3.3"
  spec.add_development_dependency "bundler", "~> 1.12"
  spec.add_development_dependency "rake", "~> 10.0"
end
```
