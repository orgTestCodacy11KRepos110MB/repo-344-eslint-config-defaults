***
# NOTICE:

## This repository has been archived and is not supported.

[![No Maintenance Intended](http://unmaintained.tech/badge.svg)](http://unmaintained.tech/)
***
NOTICE: SUPPORT FOR THIS PROJECT HAS ENDED 

This projected was owned and maintained by Walmart. This project has reached its end of life and Walmart no longer supports this project.

We will no longer be monitoring the issues for this project or reviewing pull requests. You are free to continue using this project under the license terms or forks of this project at your own risk. This project is no longer subject to Walmart's bug bounty program or other security monitoring.


## Actions you can take

We recommend you take the following action:

  * Review any configuration files used for build automation and make appropriate updates to remove or replace this project
  * Notify other members of your team and/or organization of this change
  * Notify your security team to help you evaluate alternative options

## Forking and transition of ownership

For [security reasons](https://www.theregister.co.uk/2018/11/26/npm_repo_bitcoin_stealer/), Walmart does not transfer the ownership of our primary repos on Github or other platforms to other individuals/organizations. Further, we do not transfer ownership of packages for public package management systems.

If you would like to fork this package and continue development, you should choose a new name for the project and create your own packages, build automation, etc.

Please review the licensing terms of this project, which continue to be in effect even after decommission.

## This project is DEPRECATED. It has been replaced by more specific projects.

When I started this project, I wanted `eslint-config-defaults` to be the easiest way to get started with eslint and as a part of that I wanted to have lots of options for people. At the time the `extends` feature was brand new and very few people were using it and some of this config, like Google's was not available in other places. Since then, many many companies including eslint itself began publishing their own `eslint-config-<name>`. I think this project served it’s purpose (promoting eslint and the use of the extention feature) but now we don’t need a one stop shop. This project is no longer maintained. Updated config can be grabbed at the individual project repos.

* https://github.com/walmartlabs/eslint-config-walmart
* https://github.com/google/eslint-config-google
* https://github.com/airbnb/javascript
* https://github.com/gulpjs/eslint-config-gulp
* https://github.com/FormidableLabs/eslint-config-formidable

***

<h1 align="center">eslint-config-defaults</h1>

<p align="center">
  <a title='npm version' href="https://npmjs.org/package/eslint-config-defaults">
    <img src='http://img.shields.io/npm/v/eslint-config-defaults.svg' />
  </a>
  <a title='License' href="https://opensource.org/licenses/MIT">
    <img src='https://img.shields.io/badge/license-MIT-blue.svg' />
  </a>
  <a title='Build Status' href='https://travis-ci.org/walmartlabs/eslint-config-defaults'>
    <img src='https://api.travis-ci.org/walmartlabs/eslint-config-defaults.svg?branch=master' />
  </a>
</p>

<h4 align="center">
  A composable set of ESLint configurations.
</h4>

***

## Installation

Install this config package and ESLint:

```bash
$ npm install --save-dev eslint eslint-config-defaults
```

## Usage

### Full Configurations

This package includes the following complete and ready to use configurations:

- `defaults` - The config [recommended](https://github.com/eslint/eslint/blob/master/conf/eslint.json) by ESLint
- `defaults/configurations/eslint` - The config [recommended](https://github.com/eslint/eslint/blob/master/conf/eslint.json) by ESLint
- `defaults/configurations/google` - The [Google JavaScript Style Guide](https://google.github.io/styleguide/javascriptguide.xml)
- `defaults/configurations/gulp` - The [Gulp ESLint config](https://github.com/gulpjs/eslint-config-gulp)
- `defaults/configurations/node-runtime` - The config [used for the Node.js runtime](https://github.com/nodejs/node/blob/master/.eslintrc)
- `defaults/configurations/off` - Disable all rules (ESLint's default at 1.0.0+)
- `defaults/configurations/airbnb/es5` - Config from the [AirBnB Style Guide](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb)
- `defaults/configurations/airbnb/es6-react` - Config from the [AirBnB Style Guide](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb)
- `defaults/configurations/airbnb/es6` - Config from the [AirBnB Style Guide](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb)
- `defaults/configurations/walmart/es5-browser` - Walmart ES5 + browser
- `defaults/configurations/walmart/es5-node` - Walmart ES5 + node < 4.x
- `defaults/configurations/walmart/es5-test` - Walmart ES5 + test
- `defaults/configurations/walmart/es5` - Walmart ES5 config
- `defaults/configurations/walmart/es6-browser` - Walmart ES6 + browser
- `defaults/configurations/walmart/es6-node` - Walmart ES6 + node 4.x
- `defaults/configurations/walmart/es6-react-test` - Walmart ES6 + react + test
- `defaults/configurations/walmart/es6-react` - Walmart ES6 + react
- `defaults/configurations/walmart/es6-test` - Walmart ES6 + test
- `defaults/configurations/walmart/es6` - Walmart ES6 config

###### Dependencies

- Any Walmart config (`defaults/configurations/walmart/<suffix>`) - [eslint-plugin-filenames](https://github.com/selaux/eslint-plugin-filenames)
- Any React config (`<prefix>-react`) - [eslint-plugin-react](https://www.npmjs.com/package/eslint-plugin-react), [babel-eslint](https://github.com/babel/babel-eslint)
- Any ES-next config (`es6-<suffix>`) - [babel-eslint](https://github.com/babel/babel-eslint)

To consume and extend a config in ESLint just add the extends attribute to your `.eslintrc`. For
more details about how shareable configs work, see the
[ESLint documentation](http://eslint.org/docs/developer-guide/shareable-configs).

```yaml
---
"extends":
  - "defaults"
```

```yaml
---
"extends":
  - "defaults/configurations/walmart/es6-browser"
```

**NOTE:** Extending multiple complete configs can cause unexpected results, if you need to do this you should consider a piecemeal config as explained below. See https://github.com/walmartlabs/eslint-config-defaults/issues/38 for details.

### Piecemeal Configurations

ESLint configuration is broken apart in `./rules` containing ESLint's rules and rules for specific ESLint plugins. The full set of ESLint rules (`./rules/eslint`) are broken into categories that mirror ESLint's documentation. Under each rule type there are sets of configuration as well as an `off.js` file which turns off every rule in the category.

###### Examples

```yaml
---
"extends":
  - "defaults/rules/eslint/best-practices/walmart",
  - "defaults/rules/eslint/errors/airbnb"

  - "defaults/rules/eslint/es6/off"
  - "defaults/rules/eslint/node/off"

"env":
  "phantom": true
```

## Limitations

Due to an issue with ESLint, config extension cannot be called from a globally installed (`npm install -g eslint`) eslint. It can however be run properly using eslint installed directly to your package's `node_modules`. This can be done by either calling it directly (`./node_modules/.bin/eslint .`) or from within an npm script since they automatically check local `node_modules` first. This will be tracked in issue [#43](https://github.com/walmartlabs/eslint-config-defaults/issues/43).

### This package tracks config in the following versions:

- [ESLint](https://github.com/eslint/eslint) 1.10.3
- [eslint-plugin-react](https://www.npmjs.com/package/eslint-plugin-react) 3.12.0
- [eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb) 5.0.0
- [eslint-config-gulp](https://github.com/gulpjs/eslint-config-gulp) 2.0.0
- [Google JavaScript Style Guide](https://github.com/google/styleguide/tree/43d738ab8bb0c797f78506945729946aacbab17d) 43d738ab8b
- [eslint-plugin-filenames](https://www.npmjs.com/package/eslint-plugin-filenames) 0.2.0
- [Node.js](https://github.com/nodejs/node/tree/a84bf2ce68a1ffd5c09c9ff297a56814cd79923f) a84bf2ce68a1ffd5c09c9ff297a56814cd79923f

## And A Special Thanks To

* [Nicholas C. Zakas](https://github.com/nzakas) for all the amazing work on [ESLint](https://github.com/eslint/eslint)
* [Keith Cirkel](https://github.com/keithamus) for painstakingly formatting all of ESLint's rules into JSON in [eslint-config-strict](https://github.com/keithamus/eslint-config-strict)
* [AirBnB](https://github.com/airbnb/javascript) for sharing all of their config in [JavaScript Style Guide](https://github.com/airbnb/javascript)
* [Google](https://google.github.io/styleguide/javascriptguide.xml) for sharing their styleguide
* [ES-Next Compat Table](https://github.com/kangax/compat-table) for the [excellent docs on node features](https://kangax.github.io/compat-table/es6/#node4)

***

## License

[MIT License](http://opensource.org/licenses/MIT)
