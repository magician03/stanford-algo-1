
[![Gitter](https://badges.gitter.im/sahat/megaboilerplate.svg)](https://gitter.im/sahat/megaboilerplate)
[![Build Status](https://travis-ci.org/sahat/megaboilerplate.svg?branch=master)](https://travis-ci.org/sahat/megaboilerplate)


Getting Started
---------------

### Prerequisites

- [Node.js 6.0](http://nodejs.org)
- [Git](https://git-scm.com/)
- Command Line Tools
 - <img src="http://deluge-torrent.org/images/apple-logo.gif" height="17"> **Mac OS X**: [Xcode](https://developer.apple.com/xcode/download/) or `xcode-select --install`
 - <img src="http://dc942d419843af05523b-ff74ae13537a01be6cfec5927837dcfe.r14.cf1.rackcdn.com/wp-content/uploads/windows-8-50x50.jpg" height="17"> **Windows**: [Visual C++ Build Tools 2015](http://go.microsoft.com/fwlink/?LinkId=691126)
 - <img src="https://lh5.googleusercontent.com/-2YS1ceHWyys/AAAAAAAAAAI/AAAAAAAAAAc/0LCb_tsTvmU/s46-c-k/photo.jpg" height="17"> **Ubuntu**: `sudo apt-get install build-essential`
 - <img src="http://i1-news.softpedia-static.com/images/extra/LINUX/small/slw218news1.png" height="17"> **Fedora**: `sudo dnf groupinstall "Development Tools"`
 - <img src="https://en.opensuse.org/images/b/be/Logo-geeko_head.png" height="17"> **OpenSUSE**: `sudo zypper install --type pattern devel_basis`

### Express
<img src="http://blog.newrelic.com/wp-content/uploads/expresslogo.png" height="70px">

Download and extract the project. Then in your Terminal type the following:

```shell
$ cd megaboilerplate-app

# Install NPM dependencies
$ npm install

# Start the app
$ node server.js

# Express server listening on port 3000
```

**Note**: If you have selected **Gulp** or **NPM** build tool, you may also need to run `npm run build` command.

**Note**: If you have selected a database, please make sure it is up and running. For additional information, see [**Database Setup**](#database-setup).



:top: <sub>[**back to top**](#table-of-contents)</sub>

## Database Setup

- [MongoDB](#mongodb)
- [MySQL](#mysql)
- [PostgreSQL](#postgresql)
- [SQLite](#sqlite)

:top: <sub>[**back to top**](#table-of-contents)</sub>

### MongoDB
<img src="http://s3.amazonaws.com/info-mongodb-com/_com_assets/media/mongodb-logo-rgb.jpeg" height="70px">

<img src="http://deluge-torrent.org/images/apple-logo.gif" height="17"> **Mac OS X**

Install [Homebrew](http://brew.sh/) package manager. Then follow the steps below to install and setup MongoDB.

```shell
# Update Homebrew's package database
$ brew update

# Install MongoDB
$ brew install mongodb

# Create the data directory
$ sudo mkdir -p /data/db

# Set permissions for the data directory
$ sudo chown -R `whoami` /data/db

# Run MongoDB Server
$ mongod
```

<img src="http://dc942d419843af05523b-ff74ae13537a01be6cfec5927837dcfe.r14.cf1.rackcdn.com/wp-content/uploads/windows-8-50x50.jpg" height="17"> **Windows**

1. Download and install the [current stable release](https://www.mongodb.org/downloads#production).
2. Create the data directory: **C:\data\db**.
3. Run MongoDB Server by opening `mongod.exe` in **C:\Program Files\MongoDB\Server\3.2\bin**.

<img src="https://lh5.googleusercontent.com/-2YS1ceHWyys/AAAAAAAAAAI/AAAAAAAAAAc/0LCb_tsTvmU/s46-c-k/photo.jpg" height="17"> **Ubuntu**

```shell
# Import the public key used by the package management system
$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927

# Create a source list file for MongoDB
$ echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

# Update the repository
$ sudo apt-get update

# Install the latest stable version of MongoDB
$ sudo apt-get install -y mongodb-org

# Start MongoDB service
$ sudo service mongod start
```


Obtaining API Keys
------------------

To use any of the included OAuth providers (e.g. Facebook, Twitter, Google), you will need to obtain API keys. I have included "throw-away" API keys for all OAuth providers to get you up and running quickly, but be sure to update them with your own keys.

<img src="http://www.doit.ba/img/facebook.jpg" width="200">
- Go to [Facebook Developers](https://developers.facebook.com/).
- Click on **My Apps** dropdown, then select **Add a New App**.
- Select **Website** platform, then click on **Skip and Create App ID** button.
- Enter a **name** and choose a **category** for your app.
- Click on **Create App ID** button.
- Copy and paste **App ID** and **App Secret** keys into `.env` file:
 - `FACEBOOK_ID='YOUR_APP_ID'`
 - `FACEBOOK_SECRET='YOUR_APP_SECRET'`
- Click on the **Settings** tab, then click on **+ Add Platform** button.
- Select **Website**, then enter `http://localhost:3000/auth/facebook/callback` in the **Site URL**.

**Note**: If you are using React or AngularJS, copy and paste **App Secret** into `.env` file and **App ID** into *app/actions/oauth.js* (React) and *app/app.js* (AngularJS).

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Google_2015_logo.svg/1000px-Google_2015_logo.svg.png" width="200">
- Go to [Google Cloud Console](https://cloud.google.com/console/project)
- Click on **Create project** button.
- Enter a **Project name**, then click on **Create** button.
- Click on **Use Google APIs** (Enable and manage APIs) panel.
- Click on **Credentials** tab in the sidebar.
- Client on **Create credentials** dropdown, then select **OAuth client ID**.
- Select or enter the following:
 - **Application type**: `Web application`
 - **Authorized JavaScript origins**: `http://localhost:3000`
 - **Authorized redirect URIs**: `http://localhost:3000/auth/google/callback`
- Click on **Create** button.
- Copy and paste **client ID** and **client secret** keys into `.env` file:
  - `GOOGLE_ID='YOUR_CLIENT_ID'`
  - `GOOGLE_SECRET='YOUR_CLIENT_SECRET'`

**Note**: If you are using React or AngularJS, copy and paste **client secret** into `.env` file and **client ID** into *app/actions/oauth.js* (React) and *app/app.js* (AngularJS).

<img src="https://g.twimg.com/ios_homescreen_icon.png" width="75">
- Go to [Twitter Application Management](https://apps.twitter.com/).
- Click on **Create New App** button.
- Fill out required fields.
 - **Callback URL**: `http://127.0.0.1:3000/auth/twitter/callback`
- Go to **Settings** tab.
- Click on **Allow this application to be used to Sign in with Twitter** checkbox.
- Click on **Update Settings** button.
- Go to **Keys and Access Tokens** tab.
- Copy and paste **Consumer Key** and **Consumer Secret** keys into `.env` file:
 - `TWITTER_ID='YOUR_CONSUMER_KEY'`
 - `TWITTER_SECRET='YOUR_CONSUMER_SECRET'`

**Note**: If you are using React or AngularJS, copy and paste **Consumer Secret** into `.env` file and **Consumer Key** into *app/actions/oauth.js* (React) and *app/app.js* (AngularJS).

<img src="https://upload.wikimedia.org/wikipedia/commons/2/24/GitHub_logo_2013_padded.svg" width="200">
- Go to [Github Developer Applications Settings](https://github.com/settings/developers)
- Click on **Register a new application** button.
- Fill out required fields.
 - **Application Name**
 - **Homepage URL**
 - **Callback URL**: `http://127.0.0.1:3000/auth/github/callback`
- Click on **Register application**
- Copy and paste **client ID** and **client secret** keys into `.env` file:
  - `GITHUB_ID='YOUR_CLIENT_ID'`
  - `GITHUB_SECRET='YOUR_CLIENT_SECRET'`

**Note**: If you are using React or AngularJS, copy and paste **client secret** into `.env` file and **client ID** into *app/actions/oauth.js* (React) and *app/app.js* (AngularJS).


Learning Resources
------------------

### Web Tools
- [HTML to Jade converter](http://html2jade.aaron-powell.com/)
- [SassMe - A Tool for Visualizing SASS Color Functions](http://sassme.arc90.com/)
- [uiGradients](http://uigradients.com/)

### Express
- [Creating a Simple RESTful Web App with Node.js, Express, and MongoDB](http://cwbuecheler.com/web/tutorials/2014/restful-web-app-node-express-mongodb/)
- [How To Implement Password Reset In Node.js](http://sahatyalkabov.com/how-to-implement-password-reset-in-nodejs/)


### Performance and SEO
- [Managing Mobile Performance Optimization](https://www.smashingmagazine.com/2016/03/managing-mobile-performance-optimization)
- [A technical guide to SEO](https://ma.ttias.be/technical-guide-seo/)

### Mongoose (MongoDB ODM)
- [Easily Develop Node.js and MongoDB Apps with Mongoose](https://scotch.io/tutorials/using-mongoosejs-in-node-js-and-mongodb-applications)
- [Object Modeling in Node.js with Mongoose](https://devcenter.heroku.com/articles/nodejs-mongoose)


Cheatsheets
-----------

### <img src="https://frontendmasters.com/assets/es6-logo.png" height="34" align="top"> ES6 Cheatsheet

#### Declarations

Declares a read-only named constant.

```js
const name = 'yourName';
```

Declares a block scope local variable.
```js
let index = 0;
```

#### Template Strings

Using the **\`${}\`** syntax, strings can embed expressions.

```js
const name = 'Oggy';
const age = 3;

console.log(`My cat is named ${name} and is ${age} years old.`);
```

#### Modules

To import functions, objects or primitives exported from an external module. These are the most common types of importing.

```js
import name from 'module-name';
```
```js
import * as name from 'module-name';
```
```js
import { foo, bar } from 'module-name';
```

To export functions, objects or primitives from a given file or module.

```js
export { myFunction };
```
```js
export const name = 'yourName';
```
```js
export default myFunctionOrClass
```

#### Spread Operator

The spread operator allows an expression to be expanded in places where multiple arguments (for function calls) or multiple elements (for array literals) are expected.

```js
myFunction(...iterableObject);
```
```jsx
<ChildComponent {...this.props} />
```

#### Promises

A Promise is used in asynchronous computations to represent an operation that hasn't completed yet, but is expected in the future.

```js
var p = new Promise(function(resolve, reject) { });
```

The `catch()` method returns a Promise and deals with rejected cases only.

```js
p.catch(function(reason) { /* handle rejection */ });
```

The `then()` method returns a Promise. It takes 2 arguments: callback for the success & failure cases.

```js
p.then(function(value) { /* handle fulfillment */, function(reason) { /* handle rejection */ });
```

The `Promise.all(iterable)` method returns a promise that resolves when all of the promises in the iterable argument have resolved, or rejects with the reason of the first passed promise that rejects.

```js
Promise.all([p1, p2, p3]).then(function(values) { console.log(values) });
```

#### Arrow Functions

Arrow function expression. Shorter syntax & lexically binds the `this` value. Arrow functions are anonymous.

```js
singleParam => { statements }
```
```js
() => { statements }
```
```js
(param1, param2) => expression
```
```js
const arr = [1, 2, 3, 4, 5];
const squares = arr.map(x => x * x);
```

#### Classes

The class declaration creates a new class using prototype-based inheritance.

```js
class Person {
  constructor(name, age, gender) {
    this.name   = name;
    this.age    = age;
    this.gender = gender;
  }

  incrementAge() {
    this.age++;
  }
}
```

:gift: **Credits**: [DuckDuckGo](https://duckduckgo.com/?q=es6+cheatsheet&ia=cheatsheet&iax=1) and [@DrkSephy](https://github.com/DrkSephy/es6-cheatsheet).

:top: <sub>[**back to top**](#table-of-contents)</sub>

### <img src="http://i.stack.imgur.com/Mmww2.png" height="34" align="top"> JavaScript Date Cheatsheet

#### Unix Timestamp (seconds)

```js
Math.floor(Date.now() / 1000);
```

#### Add 30 minutes to a Date object

```js
var now = new Date();
now.setMinutes(now.getMinutes() + 30);
```

#### Date Formatting

```js
// DD-MM-YYYY
var now = new Date();

var DD = now.getDate();
var MM = now.getMonth() + 1;
var YYYY = now.getFullYear();

if (DD < 10) {
  DD = '0' + DD;
} 

if (MM < 10) {
  MM = '0' + MM;
}

console.log(MM + '-' + DD + '-' + YYYY); // 03-30-2016
```
```js
// hh:mm (12 hour time with am/pm)
var now = new Date();
var hours = now.getHours();
var minutes = now.getMinutes();
var amPm = hours >= 12 ? 'pm' : 'am';

hours = hours % 12;
hours = hours ? hours : 12;
minutes = minutes < 10 ? '0' + minutes : minutes;

console.log(hours + ':' + minutes + ' ' + amPm); // 1:43 am
```

#### Next week Date object

```js
var today = new Date();
var nextWeek = new Date(today.getTime() + 7 * 24 * 60 * 60 * 1000);
```

#### Yesterday Date object

```js
var today = new Date();
var yesterday = date.setDate(date.getDate() - 1);
```



Deployment
----------

Once you are ready to deploy your app, you will need to create an account with
a cloud platform to host it. These are not the only choices you have, but they are my top
picks.

### Heroku
<img src="https://camo.githubusercontent.com/fb89a03a7dd0393851b9ed3720742b738944d863/687474703a2f2f7265732e636c6f7564696e6172792e636f6d2f646a7a6c356b6d61372f696d6167652f75706c6f61642f76313433373838333435312f4865726f6b755f6c6f676f5f6d6f6b7369702e706e67" width="200">

- Download and install [Heroku Toolbelt](https://toolbelt.heroku.com/)
- In Terminal, run `heroku login`, then enter your Heroku credentials
- Navigate to the **megaboilerplate-app** directory and run the following commands:
 1. `git init`
 2. `git add .`
 3. `git commit -m 'Initial commit'`
- Then run `heroku create` to create a new Heroku app and link it with your current Git repository

   ```bash
   Creating app... done, ⬢ floating-mesa-51019
   https://floating-mesa-51019.herokuapp.com/ | https://git.heroku.com/floating-mesa-51019.git
   ```
   
- Run `git push heroku master` and you are done!

**Note**: If you have created a new app via Heroku Dashboard, you can link it with an existing Git repository by running:

```bash
heroku git:remote -a your-heroku-app-name
```

For more information, please visit [Getting Started on Heroku with Node.js](https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction).







