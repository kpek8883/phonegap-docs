---
title: Lesson 1 - Project Setup & Creation
url: references/stockpile-app/1-project-creation
layout: subpage
---

## Create your project
1. Open a terminal window and run the `phonegap create` command below, specifying your desired *folder location*,  *package*, *name* and the [PhoneGap Split-Panel template](https://github.com/phonegap/phonegap-template-vue-f7-split-panel) for the `--template` parameter as shown below:

        phonegap create Stockpile com.phonegap.stockpile Stockpile --template https://github.com/phonegap/phonegap-template-vue-f7-split-panel

  <div class="alert--info">PhoneGap provides starter templates and layouts to help you get started building your apps quickly. The templates vary in the types of frameworks and configurations used, some being more basic and some fully configured with a build process like webpack. To locate the templates you could use with the `--template` parameter upon project creation, go to [npmjs.org](https://www.npmjs.com/search?q=phonegap:template) and use the search term `phonegap:template`.
  </div>

3. Next, change directories into your new Stockpile folder and run the `npm install` command to install the project dependencies:

        cd Stockpile
        npm install

Before moving on, it's important to understand the project structure and specifically what folder you'll be making most of your changes in. Below is the project structure you should see. It is a combination of the Vue

## Project Structure
![Project Structure](/images/stockpile/folder-structure.png)

The PhoneGap Split View template was built using the standard [VueJS Webpack template](https://github.com/vuejs-templates/webpack), which generates the folders and files below in addition to the standard PhoneGap project assets above. 

A quick explanation of what those folders and files are for is below but you can refer to the [Vue Webpack template docs](https://github.com/vuejs-templates/webpack/blob/develop/docs) for specific details. 

```
.
├── build/                      # webpack config files
│   └── ...
├── config/
│   ├── index.js                # main project config
│   └── ...
├── src/
│   ├── main.js                 # app entry file
│   ├── App.vue                 # main app component
│   ├── components/             # ui components
│   │   └── ...
│   └── assets/                 # module assets (processed by webpack)
│       └── ...
├── static/                     # pure static assets (directly copied)
├── test/
│   └── unit/                   # unit tests
│   │   ├── specs/              # test spec files
│   │   ├── index.js            # test build entry file
│   │   └── karma.conf.js       # test runner config file
│   └── e2e/                    # e2e tests
│   │   ├── specs/              # test spec files
│   │   ├── custom-assertions/  # custom assertions for e2e tests
│   │   ├── runner.js           # test runner script
│   │   └── nightwatch.conf.js  # test runner config file
├── .babelrc                    # babel config
├── .postcssrc.js               # postcss config
├── .eslintrc.js                # eslint config
├── .editorconfig               # editor config
├── index.html                  # index.html template
└── package.json                # build scripts and dependencies
```

**IMPORTANT:** In this guide we will be updating the files and folders within the **`src`** folder specifically. Any references to files within the tutorial can be found and updated in the **`src`** folder. 

4. You're now ready to start editing your project to transform it into your own Stockpile app. Open the root `Stockpile` project folder in your favorite code editor.

4. First let's provide a new app name, since **MyApp** is the current name:

    Open `~src/index.html` and change the `<title>` tag value of **MyApp** to **Stockpile.**

		<title>Stockpile</title>

## Framework7 Icons Library
Framework7 provides an icon library that we will want to add to provide more icons and iOS specific icons as we develop our apps, since the standard Framework7 library only contains a few common ones. Follow the steps below to install the [Framework7 Icons] (https://framework7.io/icons/) library.

1. Install the `framework7-icons` package from npm:

		npm install framework7-icons --save

2. In `main.js`, just above the import for the routes, add an import for the icons as shown below:

    	// Import the Framework7 Icons
    	import Framework7Icons from 'framework7-icons/css/framework7-icons.css';
    	
    	// Import Routes
    	...

## Development Workflow Overview

Since this app was built based on webpack, it can be run in development mode or production mode. While building out the app, easiest to run in development mode and test in the browser as long as you can to build out the majority of the functionality until device-specific testing is needed.

#### Development mode
First start the development webpack server with the following command:

	npm run dev

Then open the app in your browser by visiting `localhost:8080`

#### Production mode

	npm run build
	cordova run ios

or

	npm run build
	cordova run android

or

	npm run build
	cordova serve

<div class="alert--tip">The last option with `cordova serve` is particularly useful for debugging [Progressive Web Apps](/references/references/stockpile-app/9-pwa-features). </div>