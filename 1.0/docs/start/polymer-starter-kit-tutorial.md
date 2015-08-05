---
layout: default
type: start
title: Up and running with Polymer Starter Kit
subtitle: Tutorial
---

[//]: # (After reading title, user should understand that PSK

This guide teaches you how to use Polymer Starter Kit as a starting point for your own
web applications and static sites.

## Setup

1. Install [Node.js](https://nodejs.org/) (`node`) version 0.12 or above. 
   Node.js includes
   Node Package Manager (`npm`) by default. PSK uses `npm` to install and manage
   tooling.

2. Verify that you're running `node` version 0.12 or above and `npm` version 2.11
   or above.

       node -v
       v0.12.5

       npm -v
       2.12.2

3. Install Gulp and Bower.

       [sudo] npm install -g gulp bower

   Note: the `-g` flag installs Gulp and Bower globally, so you may need to 
   execute the script with sudo privileges. The reason they are installed
   globally is because some scripts expect 
   `gulp` and `bower` to be available from the command line. 

   [//]: # (discussion of the Git workflow)

4. Create a directory for your project. This guide uses the name `proj` for the 
   name of the directory. You can use whatever name you want, but when you see
   `proj`, you need to replace it with your name.

       mkdir proj

       cd proj

5. Initialize a Git repository.

       git init

6. Download the [latest PSK release][psk latest release url] and copy-paste 
   all of the files into your directory.

   [//]: # (if you copy-paste, you're going to miss all the dot files...)

   [//]: # provide link to Git-based workflow

7. Add and commit all of the files.

       git add .

       git commit -m "Add PSK vX.X.X files."

8. The PSK source code is now in your repository. Next, install all
   of the dependencies.

       npm install

       bower install

9. Build the project.

       grunt build

10. Run the project on your local host.

        grunt serve

11. Open a browser and view the site at `localhost:8080`.

## Creating a new page

In this section, you add a new page to the application.

[//]: # (description of new page)


[//]: # (use seed-element)

1. Create a new file at `app/elements/my-books-feed/my-books-feed.html`
   (you'll need to create the `my-books-feed` directory) and add the 
   code below to it.

```html


<dom-module id="my-books-feed">
  <script>
    (function() {
      Polymer({
        is: 'my-books-feed',
        properties: {}
      });
    })();
</dom-module>
```



1. Save and close `my-books-feed.html`.


1. Open `app/elements/elements.html` and import the new element.

```html
<link rel="import" href="my-book-feed/my-book-feed.html">
```


1. Open `app/index.html`.

1. Find the navigation menu. Add a link to your new page.

```html
<a data-route="my-books-feed" href="/my-books-feed">
  <iron-icon icon="book"></iron-icon>
  <span>Books</span>
</a>
```

1. Find the part of `index.html` containing all of the main content for 
   the site. Add your new content below the last `<section>`.

   [//]: # (do something PSK, but not issues)

```html
<section data-route="my-books-feed">
  <my-books-feed></my-books-feed>
</section>
```

1. Save and close `index.html`.

1. Open `app/elements/routing.html`.

1. Add the code below to configure the route to the new page.

```javascript
page('/my-books-feed', function () {
  app.route = 'my-books-feed';
});
```

1. Save and close `routing.html`.

1. Build and preview the site.

### Using elements

1. The `iron-ajax` element is already bundled as a dependency. If it
   was not, you could install it as a Bower dependency with the 
   command below.

       bower install -S PolymerElements/iron-ajax

1. Open `app/elements/elements.html` and add a line to import 
   `iron-ajax`.

## Setting up a Git-based workflow for PSK releases

Follow the instructions below to set up a Git-based workflow for updating
your project whenever a new release of PSK comes out. 

1. Create a remote that tracks the Polymer Starter Kit repository. This is
   where you pull the PSK source code. 

   The workflow below is a little more work than downloading the repository
   and copy-pasting the files, but it will enable you to quickly pull 
   PSK updates into your repository.

   SSH:

       git remote add psk git@github.com:PolymerElements/polymer-starter-kit.git

   HTTPS: 

       git remote add psk https://github.com/PolymerElements/polymer-starter-kit.git

2. Fetch the PSK source code.

      git fetch psk

3. After fetching, you should have seen a list of branches and tags. Find and 
   checkout the latest tag.

       git checkout tags/v1.0.3

4. Create a branch so that we can commit these changes to master.

      git checkout -b psk-v1.0.3

5. Go back to master, and merge the PSK release into master.

      git checkout master

   [//]: # (this adds all commits from PSK to your repository...)

      git merge psk-v1.0.3

5. OK. You're Git repository is now set up to pull in new PSK releases.



[psk latest release url]: https://github.com/PolymerElements/polymer-starter-kit/releases
