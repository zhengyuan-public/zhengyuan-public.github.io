# frozen_string_literal: true

source "https://rubygems.org"

# Use the latest Chirpy theme version
gem "jekyll-theme-chirpy", "~> 7.5"

# Testing and development tools
gem "html-proofer", "~> 5.0", group: :test
gem "webrick", "~> 1.8"
gem "rack"
gem "rackup"

# Custom plugins for your site functionality
group :jekyll_plugins do
  gem "jemoji"
  gem "jekyll-pdf-embed"
  gem "jekyll-scholar"
  gem "jekyll-latex"
  gem "jekyll-asciinema"
end

# Support for specific data processing
gem "csv"
gem "observer"

# Windows and JRuby support (Updated v7.5.0 logic)
platforms :windows, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# Performance-booster for watching directories on Windows
gem "wdm", "~> 0.2.0", :platforms => [:windows]

# Compatibility for JRuby builds
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
