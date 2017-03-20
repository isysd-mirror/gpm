
[![gpm](http://i.imgur.com/lU98JRC.png)](#)

# `$ gpm`

 [![Support me on Patreon][badge_patreon]][patreon] [![Buy me a book][badge_amazon]][amazon] [![PayPal][badge_paypal_donate]][paypal-donations] [![Version](https://img.shields.io/npm/v/gpm.svg)](https://www.npmjs.com/package/gpm) [![Downloads](https://img.shields.io/npm/dt/gpm.svg)](https://www.npmjs.com/package/gpm)

> npm + git = gpm - Install NPM packages and dependencies from git repositories.

## :cloud: Installation

You can install the package globally and use it as command line tool:


```sh
$ npm i -g gpm
```


Then, run `gpm --help` and see what the CLI tool can do.


```
$ gpm --help
Usage: gpm [options]

Options:
  -i, --input <name|git>    The NPM package name or git url.
  -u, --url-type <type>     The git url type to use (e.g. `https`, `ssh`).
  -t, --destination <path>  Where to install the package.
  -d, --depth <depth>       The depth value. Default is Infinity.
  -h, --help                Displays this help.
  -v, --version             Displays version information.

Examples:
  gpm -i git-stats # Installs git-stats and its dependencies from git repositories.
  gpm -i git@github.com:IonicaBizau/git-stats.git # Does the same, but providing the git url
  gpm -i . # install the local package dependencies

Documentation can be found at https://github.com/IonicaBizau/gpm
```


For example, if you want to install [`git-stats`](https://github.com/IonicaBizau/git-stats) and its dependencies and subdependencies (recursively), do:

```sh
$ gpm -i git-stats
```

This will create the `git-stats` repository in the current working directory.


## :clipboard: Example


Here is an example how to use this package as library. To install it locally, as library, you can do that using `npm`:

```sh
$ npm i --save gpm
```



```js
// Dependencies
var Gpm = require("gpm");

// Install uls and its Node modules from git
var pack = new Gpm("git@github.com:IonicaBizau/node-ul.git", {

    // Use https
    url_type: "https"

    // Where to install this stuff?
  , dest: __dirname

    // Clone git repositories for the 3 level depth in dependency tree
  , depth: 2
    // ul <- typpy
    //    <- deffy <- *typpy
    //
    // *–this will not be a git repository
});

// Start the install
pack.install(function (err, data) {
    console.log(err || data);
}, function (m) {
    console.log(m);
});
```

## :memo: Documentation

For full API reference, see the [DOCUMENTATION.md][docs] file.

## :yum: How to contribute
Have an idea? Found a bug? See [how to contribute][contributing].


## :sparkling_heart: Support my projects

I open-source almost everything I can, and I try to reply everyone needing help using these projects. Obviously,
this takes time. You can integrate and use these projects in your applications *for free*! You can even change the source code and redistribute (even resell it).

However, if you get some profit from this or just want to encourage me to continue creating stuff, there are few ways you can do it:

 - Starring and sharing the projects you like :rocket:
 - [![PayPal][badge_paypal]][paypal-donations]—You can make one-time donations via PayPal. I'll probably buy a ~~coffee~~ tea. :tea:
 - [![Support me on Patreon][badge_patreon]][patreon]—Set up a recurring monthly donation and you will get interesting news about what I'm doing (things that I don't share with everyone).
 - **Bitcoin**—You can send me bitcoins at this address (or scanning the code below): `1P9BRsmazNQcuyTxEqveUsnf5CERdq35V6`

    ![](https://i.imgur.com/z6OQI95.png)

Thanks! :heart:



## :scroll: License

[MIT][license] © [Ionică Bizău][website]

[badge_patreon]: http://ionicabizau.github.io/badges/patreon.svg
[badge_amazon]: http://ionicabizau.github.io/badges/amazon.svg
[badge_paypal]: http://ionicabizau.github.io/badges/paypal.svg
[badge_paypal_donate]: http://ionicabizau.github.io/badges/paypal_donate.svg
[patreon]: https://www.patreon.com/ionicabizau
[amazon]: http://amzn.eu/hRo9sIZ
[paypal-donations]: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=RVXDDLKKLQRJW
[donate-now]: http://i.imgur.com/6cMbHOC.png

[license]: http://showalicense.com/?fullname=Ionic%C4%83%20Biz%C4%83u%20%3Cbizauionica%40gmail.com%3E%20(https%3A%2F%2Fionicabizau.net)&year=2015#license-mit
[website]: https://ionicabizau.net
[contributing]: /CONTRIBUTING.md
[docs]: /DOCUMENTATION.md
