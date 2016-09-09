# E2E Testing

## Intro

[Unit Test Gif](http://67.media.tumblr.com/3d4c0c08b7ee1787b4cf229251632da9/tumblr_inline_no7oigASv41raprkq_500.gif)
> All unit tests passed.

> I don’t care if it works on your machine!  We are not shipping your machine! (Vidiu Platon)

[Visual](https://quickleft.com/wp-content/uploads/PM_Build_Swing1.gif)

Testing view

Testing user scenarios

## Nightwatch

### Installation

```bash
npm install -g nightwatch

npm install -g webdriver-manager

brew doctor
brew update
brew install selenium-server-standalone
```

### Config File

/e2e/nightwatch.json

```json
{
  "src_folders" : ["e2e"],
  "output_folder" : "reports",
  "custom_commands_path" : "",
  "custom_assertions_path" : "",
  "page_objects_path" : "",
  "globals_path" : "",

  "selenium" : {
    "start_process" : false,
    "server_path" : "",
    "log_path" : "",
    "host" : "127.0.0.1",
    "port" : 4444,
    "cli_args" : {
      "webdriver.chrome.driver" : ""
    }
  },

  "test_settings" : {
    "default" : {
      "launch_url" : "http://localhost",
      "selenium_port"  : 4444,
      "selenium_host"  : "localhost",
      "silent": true,
      "screenshots" : {
        "enabled" : false
      },
      "desiredCapabilities": {
        "browserName": "chrome",
        "javascriptEnabled": true,
        "acceptSslCerts": true
      }
    }
  }
}
```

Note: points to "e2e" directory. `"src_folders" : ["e2e"],`


### Babel

Move "nightwatch.json" into "e2e".

.babelrc

```
{
  presets: ["es2015"],
  plugins: ["add-module-exports"]
}
```

```shell
npm i babel-plugin-add-module-exports --save-dev
```

Your directory

```
e2e
  |- nightwatch.json
  |- main.js
package.json
nightwatch.conf.js
```


/nightwatch.conf.js

```js
require('babel-core/register');

module.exports = require('./e2e/nightwatch.json');
```  


### Running E2E Tests

1. run your app
2. run a selenium server
3. run nightwatch


/ package.json

```json
"scripts": {
  "e2e-setup": "concurrently 'npm start' 'webdriver-manager start'",
  "e2e": "nightwatch"
}
```

1. npm run e2e-setup
2. switch to a new window
3. npm run e2e


## Demo

1. open a browser

/e2e/demo.js

```js
module.exports = {
  'Demo test' : function (browser) {
    browser
      .url('http://www.google.com')
  }
};
```

2. open a browser and do something

/e2e/demo.js

```js
module.exports = {
  'Demo test' : function (browser) {
    browser
      .url('http://www.google.com')
      .waitForElementVisible('body', 1000)
      .setValue('input[type=text]', 'nightwatch')
      .waitForElementVisible('button[name=btnG]', 1000)
      .click('button[name=btnG]')
  }
};
```

3. open a browser, do something, and expect something

/e2e/demo.js

```js
module.exports = {
  'Demo test' : function (browser) {
    browser
      .url('http://www.google.com')
      .waitForElementVisible('body', 1000)
      .setValue('input[type=text]', 'nightwatch')
      .waitForElementVisible('button[name=btnG]', 1000)
      .click('button[name=btnG]')
      .pause(1000)
      .assert.containsText('#main', 'Night Watch')
      .end();
  }
};
```

4. Always `browser.end()` your tests to close the browser.

## First Test

/e2e/main.js

```js
const url = 'http://localhost:3000';

module.exports = {
  'Loads page with title': (browser) => {
    browser
      .url(url)
      .waitForElementVisible('body', 1000)
      .assert.containsText('h1', 'Worst Pokemon')
      .end();
  }
};
```

## Second Test

/e2e/main.js

```js
{
 'Loads list of pokemon': (browser) => {
    browser
      .url(url)
      .waitForElementVisible('ol', 1000)
      .elements('tag name', 'li', (result) => {
        browser.assert.equal(result.value.length, 3)
      })
      .end();
  }
}
```

## Third Test

Test if the first button has a value of 2.

/e2e/main.js

```js
'Votes item up once on click': (browser) => {
    browser
      .url(url)
      .waitForElementVisible('ol', 1000)
      .assert.containsText('.btn', '2')
      .end();
}
```

Test if clicking on the button changes the value to 3.


/e2e/main.js

```js
'Votes item up once on click': (browser) => {
    browser
      .url(url)
      .waitForElementVisible('ol', 1000)
      .assert.containsText('.btn', '2')
      .click('.btn')
      .assert.containsText('.btn', '3')
      .end();
}
```

Test if clicking on the button again doesn't change the value.

/e2e/main.js

```js
'Votes item up once on click': (browser) => {
    browser
      .url(url)
      .waitForElementVisible('ol', 1000)
      .assert.containsText('.btn', '2')
      .click('.btn')
      .assert.containsText('.btn', '3')
      .click('.btn')
      .assert.containsText('.btn', '3')
      .end();
```


## Snapshot Error Testing

Show a snapshot when your test fails.

/e2e/nightwatch.json

```json
 "test_settings" : {
    "default" : {
      "screenshots" : {
        "enabled" : true,
        "on_failure" : true,
        "on_error" : false,
        "path" : "e2e/screenshots/fail",
      },
```

## Snapshot Size Testing

/e2e/main.js

```js
const viewport_widths = [240, 320, 360, 568, 603, 640, 768, 800, 960, 1024, 1280, 1400, 1600, 1920];
const imageDir = name => __dirname + '/screenshots/sizes/' + name + '.png';


module.exports = {
'Loads page with title': (browser) => {
    browser
      .url(url)
      .waitForElementVisible('body', 1000);

    viewport_widths.forEach(width => {
      browser
        .resizeWindow(width, 300)
        .saveScreenshot(imageDir(`page-${width}`));
    });
    
    browser.end();
  }
};
```

## Multiple Browser Testing

Add a browser to "test_settings" in "nightwatch.json".

/e2e/nightwatch.json

```json
"firefox" : {
  "desiredCapabilities": {
    "browserName": "firefox",
    "javascriptEnabled": true,
    "acceptSslCerts": true
  }
}
```

You may have to add a link to the browser driver for selenium.

/e2e/nightwatch.json

```json
"selenium" : {
    "cli_args" : {
      "webdriver.chrome.driver" : "",
      "webdriver.firefox.driver": "",
      "webdriver.safari.driver": ""
    }
  }
```

In your "package.json" create a script to run multiple browser tests.

/package.json

```json
"scripts": {
  "e2e-all": "nightwatch -e chrome,firefox"
}
```

Note: Safari requires an app developer account.

We should now also adjust our snapshot code.

```js
const browserName = browser.options.desiredCapabilities.browserName;    

viewport_widths.forEach(width => {
  browser
    .resizeWindow(width, 300)
    .saveScreenshot(imageDir(`page-${browserName}-${width}`));
});
```

## Page Objects

Configure [page objects](https://github.com/nightwatchjs/nightwatch-docs/blob/master/guide/working-with-page-objects/using-page-objects.md)

/e2e/nightwatch.json

```js
{
  "page_objects_path": "e2e/pages/"
}
```

Directory structure:

```
e2e
  |- nightwatch.json
  |- main.js
  |- screenshots
      |- image.png
  |- pages
      |- main.js 
package.json
nightwatch.conf.js
```

/e2e/pages/main.js

```js
module.exports = {  
  url: 'http://localhost:3000',
  widths: [800],
  elements: {
    title: 'h1',
    pokemonList: 'ol',
    pokemon: 'li',
    vote: '.btn',
  }
};
```

/e2e/main.js

```js
'Loads page with title': (browser) => {
  // before
  // browser
  //   .url('http://localhost:3000')
  //   .waitForElementVisible('body', 1000)
  //   .assert.containsText('h1', 'Worst Pokemon')
  //   .end();


  // with page objects
  let main = browser.page.main();

  main
    .navigate()
    .waitForElementVisible('body', 1000)
    .assert.containsText('@title', 'Worst Pokemon');

  browser.end();
}
```

Notice how we can reference page objects with `browser.page.FILE_NAME()`.

Notice how we call page objects with "@ELEMENT_NAME". 
Page objects must be included under a key of "elements" or "section".

/e2e/main.js

```js
'Votes item up once on click': (browser) => {

    let main = browser.page.main();

    main
      .navigate()
      .waitForElementVisible('@pokemonList', 1000)
      .assert.containsText('@vote', '2')
      .click('@vote')
      .assert.containsText('@vote', '3')
      .click('@vote')
      .assert.containsText('@vote', '3');
      
    browser.end();
  }
```

Note of frustration.

/e2e/main.js

```js
'Loads list of pokemon': (browser) => {

  // cannot use page "elements" with a page object,
  // as it part of the "selenium" api and tied to "browser

},
```