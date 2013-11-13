# The Goal

> Rapid Prototyping: *The process of quickly mocking up the future state of a system* (Source: [Design Better And Faster With Rapid Prototyping](http://www.smashingmagazine.com/2010/06/16/design-better-faster-with-rapid-prototyping)).

The goal of this session is to work through a suggested workflow for creating rapid prototypes of a web site or app.  The techniques used will emphasize speed, team coding, and ease of iteration.

# Required Tools

* [GIT](http://git-scm.com/) - Source control, versioning, and code sharing
* [Node.js](http://nodejs.org/) - Server side js (runs Yo, Grunt, and Bower).
* [NPM (Node Package Manager)](https://npmjs.org/) - The name says it all: This manages all of your Node packages
* [Ruby](https://www.ruby-lang.org/en/) - Server side scripting language. We’re using it for SASS, Compass, Jekyll, and Foundation.
* [Yeoman (‘Yo’)](http://yeoman.io/) - ‘Scaffolding’ i.e. automatic project setup.
* [Grunt](http://gruntjs.com/) - Build tool and task runner.  Automates development, testing, and deployment.
* [Bower](http://bower.io/) - Front end package manager (built by Twitter).
* [Zurb Foundation](http://foundation.zurb.com) - Front end framework (Responsive, Mobile First)
* [Jekyll](http://jekyllrb.com/) - Fast static html templates from [markdown](http://daringfireball.net/projects/markdown/) and [Liquid](http://docs.shopify.com/themes/liquid-basics) tags.
* [Angular.js](http://angularjs.org/) - Fast interactive javascripting (by Google)

# Optional Tools
* [Console 2](http://sourceforge.net/projects/console/) - Tabbed and improved console for Windows.  [GIT Bash integration how-to](http://johngilliland.wordpress.com/2012/12/22/git-bash-console2-finally/)
* [Sublime Text](http://www.sublimetext.com/) - A fantastic code editor
* [Emmet](http://emmet.io/) - Crazy fast html shortcuts for Sublime (and other editors)

# Setup ( Windows 8 )

## 1. Install GIT and GIT Bash
You'll need a way to use command line [GIT](http://git-scm.com/) and [SSH](http://www.openssh.org/).  If you're using Linux/Mac for development you probably already have both and can run them from your operating system's native terminal.

Windows users can get everything they need by downloading and installing the appropriate installer [here](http://git-scm.com/downloads).  When you run the installer, use the default options except be sure to set your line endings to Unix style (see _fig 1_).  This will install Git, ssh, and other related utilities that you'll need for development.  It also installs a custom terminal called 'Git Bash'.  **NOTE: All commands should be run from Git Bash from now on.  Do NOT use Windows' cmd.exe.**

If you already have an alternative way of running Git/SSH on windows (like cygwin) feel free to stick with that.

![](https://lh6.googleusercontent.com/93jLHd_-BYElDik10RDRPL4yjRQGX_AB5xyH6Qyd3-84LT5-wmi_lnFNRmXdZxCKVJwT_uEhKMcvhDB3_e-vS1uy2Cocb2Bl6Byf5HU8i4OxtFw58CoG1-Aqiw)

_fig 1: Setting commit Unix-style line endings_

**Download: **http://git-scm.com/downloads

## 2. Install Node.js and NPM
 Download the windows installer from [the Node Downloads Page](http://nodejs.org/download/).  Run the installer with its default options.  This should also install NPM and add Node to your system PATH (so you can type Node commands no matter what directory you’re in).

Test it by launching GIT Bash and entering `node -v`. If Node is working, you’ll get the version number back.  Now try `npm -v`.  You should get a version number back again.  Congrats!  You can now Node.

If you get an error, make sure Node was added to PATH ([see this thread for help](http://stackoverflow.com/questions/8768549/node-js-doesnt-recognize-system-path)).

## 3. Install Ruby
The fastest way to do get Ruby going on Windows is to use [Rails Installer](http://railsinstaller.org/en).  Download at least version 1.8 and run the installer.  This will install Ruby, as well as some other packages that we need (namely the [devkit](http://rubyinstaller.org/add-ons/devkit/), which we need to get some other things running, and [Bundler](http://bundler.io/), which makes sure we have all the right versions of all Ruby gems etc.).

If that doesn’t work for you, try [Ruby Installer](http://rubyinstaller.org/).  Just be sure to also install the [devkit](http://rubyinstaller.org/add-ons/devkit/), and [Bundler](http://bundler.io/), because they’re not included.  You may also need to add Ruby to PATH yourself.

## 4. Install Yo/Bower/Grunt
Fire up GIT Bash and enter `npm install -g yo`.  Wait for the install to download and complete.  If you have errors, try running GIT Bash as an administrator.  Beyond that, Googling any errors you’re getting is amazing for helping overcome system specific snags.

## 5. Install Generator-jekyllrb
Generators are instructions that help Yeoman set up new projects automatically.  Install the one for Jekyll by entering `npm install -g generator-jekyllrb`.

# Let’s Build! (CSS and HTML)

> **Note**: All GIT techniques are roughly based on the article [‘How I Use GIT’ by Glenn Stovall](http://glennstovall.com/blog/2013/03/15/how-i-use-git/).  If you are unfamiliar with GIT, I recommend working through the 15min interactive tutorial at [Try Git](http://try.github.io/levels/1/challenges/1).
## 1. Create a work space and local GIT repo
* Create a directory
* Move into new dir and GIT init `git init`
* Create dev branch   `git checkout -b dev`

## 2. Get Yeoman to set up a blank Jekyll project for us
* `yo jekyllrb`
  * causes an error - Googled ‘Error: building is not supported on win32 npm install’ and found a [fix here].(https://github.com/gruntjs/grunt-contrib-imagemin/issues/109)
  * run `npm install` to finish the installation
* Now run `grunt server` to see the site Yeoman built
* Commit your changes by adding the new files to GIT tracking ( `git add .`) and committing them (`git commit -am ‘your message about the commit`)
## 3. Commit files to remote GIT server for sharing and safekeeping
* Connect to remote GIT repo `git remote add origin [Bitbucket or Github repository URL]`
* Create a master branch on the remote server `git push origin master`
* Create a dev branch on the remote server `git push origin dev`

## 4. Add Foundation using Bower
* `bower install foundation --save`
* Add `@import "../_bower_components/foundation/scss/foundation.scss";` to main.scss

## 5. Templating with Jekyll
* YAML
* Folder structure (for pretty urls)
* layouts
* includes
* logic

## 6. Add Foundation Javascripts
* Add any Foundation .js files you need to the usemin blocks
  * [Foundation Documentation on adding .js](http://foundation.zurb.com/docs/javascript.html)
* Add any supporting .js to `copy:dist` grunt task
  * [Documentation Here](https://github.com/robwierzbowski/generator-jekyllrb#bower-components-and-usemin)
* `grunt server` to see results

## 7. Build (for sharing or deployment)
* Simply enter `grunt build`
* Take a look at your files to make sure everything was minified and copied correctly.

# Make it Dance! (Angular.js interactivity)

## 1. Use Bower to Install Angular.js
* `bower install angular --save`
  * [Docs here](https://github.com/angular/bower-angular)
* Add script to `<head>`
* Add script url to `copy:dist` task in Gruntfile.js (like we did for the foundation files)
## 2. Start using Angular
* This is another lesson for another day
* If you’re curious, check out [Egghead.io](http://egghead.io/).  All of the beginner lessons are free, as are a lot of the advanced ones.  Watching 1 - 31 is how I got started. [Angular’s official tutorial](http://docs.angularjs.org/tutorial) is also quite good.






