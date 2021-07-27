_This repository is discontinued: See https://github.com/vault12/glow.ts for the new reference client library implementation._

# Glow [![Build Status](https://travis-ci.org/vault12/glow.svg?branch=master)](https://travis-ci.org/vault12/glow)
Glow is a reference client library for interacting with [Zax](https://github.com/vault12/zax), a [NaCl-based Cryptographic Relay](https://s3-us-west-1.amazonaws.com/vault12/zax_infogfx.jpg). You can read the full technical specification [here](http://bit.ly/nacl_relay_spec). This reference implementation is in [CoffeeScript](http://coffeescript.org). We will add links to other implementations in different languages as they become available.

## Version 4.0 Update
Glow 4.0 introduces support for Zax 2.0 [file exchange api](https://github.com/vault12/zax/wiki/Zax-2.0-File-Commands). Full documentation is avaiable [here](https://github.com/vault12/zax/blob/master/README.md)

## Test Dashboard
 Glow powers a test [Dashboard](https://github.com/vault12/zax-dash) app to provide user-friendly access point to given relay internal mailboxes. We maintain live [Test Server](https://zax-test.vault12.com) that runs our latest build. For testing purposes expiration on that relay is set for 30 minutes.

## Installation
Glow can be easily installed via `npm`, which is included when you install [Node.js](https://nodejs.org/).
In a terminal, navigate to the directory in which you'd like to install Glow and type the following:
```Shell
npm install theglow
```
The built version of Glow will be available in `dist` subdirectory, along with the minified copy.

NOTE: if you're going to use Glow in CLI mode, consider installing it globally: `npm install -g theglow`.

## Command-line interface
To see commands that Glow utility provides, type in the terminal `./bin/glow.js` (or just `glow` if you've installed it globally).
Currently supported commands are:

```
glow clean <relay_url> <guest_public_key>                delete all files in mailbox on the relay
glow count <relay_url> <guest_public_key> [options]      show number of pending files on the relay
glow download <relay_url> <guest_public_key> [options]   download file(s) from the relay
glow key [options]                                       show public key or h2(pk), set/update private key
glow upload <relay_url> <guest_public_key> <file_url>    upload file to the relay
glow help [cmd]                                          display help for [cmd]
```

Use `glow help [cmd]` to learn more about supported options for each command. Note that private key must be set with `glow key` prior to any relay requests.

## Running the tests
By default, unit tests connect to a local [Zax](https://github.com/vault12/zax) Cryptographic Relay Server on `http://localhost:8080`.
You may also run tests on our maintained test server by modifying the code in [tests/helper.coffee#L37](tests/helper.coffee#L37), or set your own remote relay URL in [tests/helper.coffee#L42](tests/helper.coffee#L42):

```CoffeeScript
host: 'https://zax-test.vault12.com'
```
To create a build and run the tests, navigate to the glow directory and type the following in a terminal:

```Shell
node_modules/gulp/bin/gulp.js
```

Note that if you have [Gulp](https://github.com/gulpjs/gulp) installed globally, you can also simply type `gulp`.

Note that only one instance of tests can be run at the same time, since test keys are derived from the same seeds. Running multiple instances simultaneously may cause unpredicted behavior.

##### Source maps
By default, the build generates source maps and places them in the `build` directory.

If you are new to using source maps to debug, here's an overview:

Chrome: [Source Maps on Chrome](https://developer.chrome.com/devtools/docs/javascript-debugging#source-maps)

Safari: [Source Maps on Safari](https://developer.apple.com/library/mac/documentation/AppleApplications/Conceptual/Safari_Developer_Guide/ResourcesandtheDOM/ResourcesandtheDOM.html)

Firefox: [Source Maps on Firefox](https://developer.mozilla.org/en-US/docs/Tools/Debugger/How_to/Use_a_source_map)

##### Running the tests at the command line
To run the command line tests, navigate to the glow directory and type the following in a terminal:

```Shell
node_modules/gulp/bin/gulp.js test
```

## Release Builds

Generate production-ready build via the command line:

```Shell
node_modules/gulp/bin/gulp.js dist
```

This will create the appropriate files in the following directory: `dist`

## Demo
To see Glow and Zax in action, check out the [Live Demo](https://zax-test.vault12.com). This is a test project included in Zax called [Zax-Dash](https://github.com/vault12/zax-dash).

## Contributing
We encourage you to contribute to Glow using [pull requests](https://github.com/vault12/glow/pulls)! Please check out the [Contributing to Glow Guide](CONTRIBUTING.md) for guidelines about how to proceed.

## Slack Community [![Slack Status](https://slack.vault12.com/badge.svg)](https://slack.vault12.com)
We've set up a public slack community [Vault12 Dwellers](https://vault12dwellers.slack.com/). Request an invite by clicking [here](https://slack.vault12.com/).

## License [![License](https://img.shields.io/github/license/vault12/glow.svg)](http://opensource.org/licenses/MIT)
Glow is released under the [MIT License](http://opensource.org/licenses/MIT).

## Legal Reminder
Exporting/importing and/or use of strong cryptography software, providing cryptography hooks, or even just communicating technical details about cryptography software is illegal in some parts of the world. If you import this software to your country, re-distribute it from there or even just email technical suggestions or provide source patches to the authors or other people you are strongly advised to pay close attention to any laws or regulations which apply to you. The authors of this software are not liable for any violations you make - it is your responsibility to be aware of and comply with any laws or regulations which apply to you.
