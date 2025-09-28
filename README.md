# blog

A repository of my blog posts over the last 20 years.

Uses a pre-commit hook to set `last_modified_at` front-matter.

```
git config --local core.hooksPath .githooks/
chmod ug+x .githooks/*
```

To run the blog locally, run

```
bundle exec jekyll serve --livereload
```