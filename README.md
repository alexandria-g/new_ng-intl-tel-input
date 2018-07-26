# alexandria-g's fork of betsol-ng-intl-tel-input

### This fork has been adapted for optional two-way binding for Angular.js (`^1.3`), accessible in $scope.watch().

This module for Angular.js (`^1.2.29`) provides integration
for the great [intl-tel-input] jQuery plugin (version 7-8 are supported).

For more information, view the OG fork:
https://github.com/betsol/ng-intl-tel-input

### Enabling two-way binding watch for Angular.js (^1.3)


```html
<COMPONENT-NAME phone-number="user.fullphone" formatted-number="user.mobile" country-code="user.dialcode" valid-number="user.validphone"></COMPONENT-NAME>
```

```component template html
<input
    type="tel"
    ng-model="phoneNumber"
    value="{{phoneNumber}}"
    id="mobileInput"
    intl-tel-input
    intl-tel-input-options="{watch:true, ...}"
>
```


## Installation

### Install integration library within package.json

- include the following in your package.json file:
@todo


### Add integration library to your page

Make sure, that module is added to your page either as a part of automatically built bundle
or manually using the code like this:

``` html
<script src="../betsol-ng-intl-tel-input/dist/betsol-ng-intl-tel-input.js"></script>
```

You should use minified version (`betsol-ng-intl-tel-input.min.js`) in production.

### Notes for Angular js users

May need to also include the following scripts:
@todo


### Add dependency in your application's module definition

``` javascript
var application = angular.module('application', [
  // ...
  'betsol.intlTelInput'
]);
```

### Introduce the directive

To add the plugin to any input field please use the `intl-tel-input` directive:

`<input type="tel" ng-model="user.phoneNumber" intl-tel-input>`


## Configuration

### Global

You can configure the plugin by changing the global object `intlTelInputOptions`.
This will apply specified changes across all plugin instances in your application.
All configuration options could be found in the [original plugin documentation].

#### Global Configuration Example

```javascript
angular
  .module('app', ['betsol.intlTelInput'])
  .config(function (intlTelInputOptions) {
    angular.extend(intlTelInputOptions, {
      nationalMode: false,
      utilsScript: '/vendor/intl-tel-input/utils.js',
      defaultCountry: 'auto',
      preferredCountries: ['ru', 'kz'],
      autoFormat: true,
      autoPlaceholder: true
    });
  })
;
```

### Custom instance configuration

You can configure each input field individually by
specifying the configuration options via `intl-tel-input-options` attribute.

#### Instance Configuration Example

```html
<input
    type="tel"
    ng-model="user.phoneNumber"
    intl-tel-input
    intl-tel-input-options="{ excludeCountries: ['us', 'de'] }"
>
```

## API

You can use `intl-tel-input-controller` attribute to specify an object
that will be populated with the directive's API functions.

### API Usage Example

```javascript
angular
  .module('app', ['betsol.intlTelInput'])
  .controller('MyCtrl', function ($scope) {
    $scope.myIntlTelInputCtrl;
    $scope.changeCountryToRussia = function () {
      $scope.myIntlTelInputCtrl.setCountry('ru');
    };
  })
;
```

```html
<input
    type="tel"
    ng-model="user.phoneNumber"
    intl-tel-input
    intl-tel-input-controller="myIntlTelInputCtrl"
>
<button ng-click="changeCountryToRussia()">
    Change Country to Russia
</button>
```


### List of Supported API Functions:

- `setCountry({string} countryCode)`

## Changelog

Please see the [changelog] for list of changes.


## Feedback

If you have found a bug or have another issue with the library —
please [create an issue].

If you have a question regarding the library or it's integration with your project —
consider asking a question at [StackOverflow] and sending me a
link via [E-Mail]. I will be glad to help.

Have any ideas or propositions? Feel free to contact me by [E-Mail].

Cheers!


## Developer guide

Fork, clone, create a feature branch, implement your feature, cover it with tests, commit, create a PR.

Run:

- `npm i` to initialize the project
- `npm i -g gulp` to install Gulp
- `gulp build` to re-build the dist files
- `gulp test` or `karma start` to test the code
- `gulp start` to run demo server and watches
- `gulp demo:deploy` to deploy the demo on GitHub Pages

Do not add dist files to the PR itself.
We will re-compile the module manually each time before releasing.


## Support

If you like this library consider to add star on [GitHub repository][repo-gh].

Thank you!


## License

The MIT License (MIT)

Copyright (c) 2016 Slava Fomin II, BETTER SOLUTIONS

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
