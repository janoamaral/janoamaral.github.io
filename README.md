# Alejandro Amaral

Jekyll source for [janoamaral.github.io](https://janoamaral.github.io/).

## Development

Install the locked Ruby and Node dependencies:

```sh
bundle install
npm ci
```

Build exactly as GitHub Pages does:

```sh
JEKYLL_ENV=production bundle exec jekyll build
```

Serve locally with PostCSS enabled:

```sh
JEKYLL_ENV=production bundle exec jekyll serve
```

`JEKYLL_ENV=production` is required by the pinned `jekyll-postcss` version so it uses its one-shot compiler instead of the development socket server.
