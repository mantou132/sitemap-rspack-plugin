[![npm version](https://badge.fury.io/js/sitemap-webpack-plugin.svg)](https://badge.fury.io/js/sitemap-webpack-plugin) [![CircleCI](https://circleci.com/gh/schneidmaster/sitemap-webpack-plugin.svg?style=shield)](https://circleci.com/gh/schneidmaster/sitemap-webpack-plugin) [![Coverage Status](https://coveralls.io/repos/github/schneidmaster/sitemap-webpack-plugin/badge.svg)](https://coveralls.io/github/schneidmaster/sitemap-webpack-plugin)

# sitemap-webpack-plugin

Webpack plugin to generate a sitemap. Designed to work with [static-site-generator-webpack-plugin](https://github.com/markdalgleish/static-site-generator-webpack-plugin/) (although it also works great by itself).

## Installation

    npm install sitemap-webpack-plugin --save-dev

## Usage

Add to your webpack config -- see below for an example. The plugin signature is:

    new SitemapPlugin(base, paths, filename)

* `base` is the root URL of your site (e.g. 'https://mysite.com')
* `paths` is the array of locations on your site -- this can be the same one you pass to `static-site-generator-webpack-plugin`
* `filename` is the name of the output file -- the default is `sitemap.xml`

### Options

* `lastMod` [boolean] default `false`
* `priority` [number] default `null`
* `changeFreq` [string] default `null`, list of applicable values based on [sitemaps.org](http://www.sitemaps.org/protocol.html)

```
always
hourly
daily
weekly
monthly
yearly
never
```

### webpack.config.js

```js
var SitemapPlugin = require('sitemap-webpack-plugin');

var paths = [
  '/foo/',
  '/bar/'
];

module.exports = {

  /* snip */

  plugins: [
    new SitemapPlugin('https://mysite.com', paths, 'map.xml')
  ]

  /* with options */

  plugins: [
    new SitemapPlugin(
      'https://mysite.com',paths, 'map.xml',
      {
        lastMod: true,
        changeFreq: 'monthly',
        priority: 0.4,
      }
    )
  ]

};
```



## Contributing

1. Fork it ( https://github.com/schneidmaster/sitemap-webpack-plugin/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
