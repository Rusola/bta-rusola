# WebDriver I/O from scratch
## 1. Prerequisites
#### 1.1. Node.js:
Install the latest Node.js from
https://nodejs.org/en/
#### 1.2. Git:
Install the latest Git from 
https://git-scm.com/

===

for Windows:
#### 1.3. Node Version Manager (nvm-windows):
Install the nvm-windows from
https://github.com/coreybutler/nvm-windows/releases
#### 1.4. Install all the required tools and configurations using Microsoft's windows-build-tools:
Open Command Prompt and run the following script:
````
npm install --global --production windows-build-tools
````

## 2. Creating project
#### 2.1. Create project folder:
Open terminal and navigate to desired folder where you're going to store all of your projects. For example `projects` folder:
````
cd projects/
````
Create a folder for automation project. For example, `automation-webdriverio`:
````
mkdir automation-webdriverio
````
And navigate to the created folder:
````
cd automation-webdriverio
````
#### 2.2. Initialize your project:
````
 npm init
````
Click 'Enter' for every item to accept default values or specify whatever you like.
This action creates `package.json` file.

## 3. Modules installation and configuration
#### 3.1. Install webDriver I/O:
````
 npm i --save-dev webdriverio
````
#### 3.3. Install Selenium:
````
 npm i --save-dev selenium-standalone
````
#### 3.3. Create WebDriver I/O configuration:
````
 ./node_modules/.bin/wdio config
````
Click `Enter` for the following items:
````
Where do you want to execute your tests?:
On my local machine
````
````
Which framework do you want to use?:
mocha 
````
Type `Y` and click `Enter` for the following:
````
Shall I install the framework adapter for you? (Y/n):
Y
````
Type `./test/**/*.js` and click `Enter` for the following:
````
Where are your test specs located?
./test/**/*.js
````
Just click `Enter` for the following items:
````
Which reporter do you want to use?
````
````
Do you want to add a service to your test setup?
````
````
Do you want to add a service to your test setup?
````
````
Level of logging verbosity
````
````
In which directory should screenshots gets saved if a command fails? (./errorShots/)
````
Type `https://artsenius.github.io/Bug-Tracker/` and click `Enter` for the following:
````
What is the base url?
https://artsenius.github.io/Bug-Tracker/
````
Wait till the end of the installation process.

## 4. Creating the first test
#### 4.1. Create `test` folder and open it:
````
mkdir test
cd test
````
#### 4.2. Create `test.js` file and open it:
````
touch test.js
open test.js
````
#### 4.3. Add the first test:
````
describe('Page opening', function () {
  it('get title', function(){
    browser.url('/Bug-Tracker/');
    let title = browser.getTitle();
    browser.pause(5000);
    console.log(title);
  })
});
````

## 5. Selenium Server and WebDriver I/O initial configuration
#### 5.1. Initial installation:
````
./node_modules/.bin/selenium-standalone install
````
Wait till the end of the installation process.
#### 5.2. Add a script for starting Selenium Server:
Open `package.json` and add new entry to the `scripts` object:
````
"start": "selenium-standalone start"
````
Now you can start selenium server using `npm start` script.
#### 5.3. Add a script for running WebDriver I/O tests:
Open `package.json` and modify `test` script:
````
"test": "wdio wdio.conf.js",
````
Now you can start Selenium Server using `npm start` script and run tests using `npm test`.

## 6. Running the first test
#### 6.1. Start Selenium Server:
````
npm start
````
#### 6.2. Open new tab in Terminal and run the first test:
````
npm test
````
Wait until test is finished. 
You should see the message that 1 test passed.

## 7. Install additional reporters
#### 7.1. Spec reporter:
````
npm install wdio-spec-reporter --save-dev
````
#### 7.2. Allure reporter:
````
npm install wdio-allure-reporter --save-dev
````

## 8. `wdio.conf.js` configuration
#### 8.1. Turn on sync mode:
`sync: false` => `sync: true`
#### 8.2. Configure browser:
`browserName: 'firefox'` => `browserName: 'chrome'`
#### 8.3. Configure reporters:
uncomment `// reporters: ['dot'],`
and then:
````
reporters: ['dot', 'spec', 'allure'],
  reporterOptions: {
    allure: {
      outputDir: 'allure-results'
    }
  },
````


## TODO:
.gitignore