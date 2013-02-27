# About this project

This project is built on the Hull platform, with [Aura](github.com/aurajs/aura), [Backbone.js](https://github.com/documentcloud/backbone) and lots of other cool libraries.

**You don't need an account on Hull to use it locally, the App key is already present in this app.**

-----------------------

# Instant Win

This is demo entirely built with Hull.
Connect, and immediately know if you've won or lost.

## Skip the Queue !

What you'll win here is an immediate access to hull.
Also, somewhere deep in the source are hidden more codes to gain immediate access to Hull, without waiting for an invite.

[Play Instant Win (http://hull.github.com/instant-win)](http://hull.github.com/instant-win)

The following features are demoed in this app.
It has no server code and barely any Javascript.

* Login with Twitter
* Use a hull [Instant Win widget](http://hull.io/docs/widgets/packaged_widgets/#hull-widget-instant_win) to know if you've won or lost.
* Share your result on Twitter

The steps below are tailored for Mac environments.
Linux should mostly work the same.

## How it was done

1. Create a new Hull app using our [Grunt-init task](https://github.com/hull/grunt-init-hull).

        grunt-init instant-win

2. Create a HTML page called ``admin.html``, and insert a ``instant_win_admin@hull`` widget to write your questions.

        <!-- Instant Win Admin Widget -->
        <div data-hull-widget="instant_win_admin@hull"></div>

3. From there, create a new Instant Win, give it a name, a description, and a hard to guess secret.


4. Enter the Prizes for this Instant Win. The format is plain JSON.
For your convenience a template for it is bundled in this repository, in `prizes.json`


5. Copy the newly created Instant Win's ID, and insert a ``instant_win@hull`` widget inside the main HTML page.

        <!-- Instant Win Widget -->
        <div data-hull-widget="instant_win@hull" data-hull-id="YOUR_INSTANT_WIN_ID"></div>

6. Create `widget/instant_win/won.hbs` to override the default template.

7. Do a bit of CSS for an effective design.

8. **There's no step 8.**


## Installing

First, clone this repository :

    git clone git://github.com/hull/instant-win.git

Install [node.js](http://nodejs.org) (Only used for building the app, not needed for deployment)

Install [grunt-cli](https://github.com/gruntjs/grunt-cli) as a global module.
It's amazing so you should do it anyways.

    [sudo] npm install grunt-cli -g
    [sudo] npm install bower -g

then install grunt and it's modules in the project's folder.

    cd instant-win/
    npm install
    bower install

## Running the app

**To run the app locally, run:**

    grunt server

## Deploying

First create your heroku app if it's not done yet :

    heroku create your_amazing_app

Build your app for deployement, and commit the compiled version:

    grunt build
    cd dist
    git init
    git add dist
    git commit -m "Deployment build"

Deploy your app to heroku:

    git subtree push --prefix dist heroku master
    open http://your_amazing_app.herokuapp.com
