# Blog: "I must follow, if I can"

A repository of my blog posts over the last 20 years. The blog title comes from a poem in _The Lord of the Rings_: "The Road Goes Ever On and On..."

Uses a pre-commit hook to set `last_modified_at` front-matter.

```
git config --local core.hooksPath .githooks/
chmod ug+x .githooks/*
```

To run the blog locally, run

```
bundle exec jekyll serve --livereload
```

Then navigate to http://localhost:4000.

If you get an SSL error, make sure `openssl` is up-to-date via `brew install openssl`.