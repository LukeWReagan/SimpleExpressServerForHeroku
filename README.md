# README for a Simple Express Server for Heroku

## Introduction

This project provides an easy way to deploy a Web server on Heroku. It will serve "static" files, including HTML, CSS, JavaScript, and images.

In addition to serving static files, this server echoes any form data posted to it back to the client. This is for instructional/experimental purposes.

Everything here is free, mostly open-source. Heroku is free for modest sites where performance is not important.

## Instructions

These instructions apply most directly to Linux, particularly Debian, Ubuntu, Mint, or related distributions. But you will find instructions for other operating systems at the various projects' Web sites.

Many of these steps are done at the command line (a.k.a. terminal or shell), and the command prompt is represented by "$".

1.  Install [Node.js](http://nodejs.org/). The best way to do this depends on your OS, among other things.

    Most Linux distributions include _nodejs_ as a package in their repositories and you can install it with a command like  
    `$ sudo apt-get install nodejs`  
    For Mac OS X and Windows, you can download installers at [Node.js Downloads](https://nodejs.org/download/).

    If you find yourself using Node.js for other projects, you should consider using [n](https://github.com/tj/n) or [nvm](https://github.com/creationix/nvm). These allow you to switch between multiple versions and also to avoid permission issues that often arise when using _npm_.

    Test the installation at the command-line prompt with:
    *   `$ node -v`
    *   `$ npm -v`

2.  Install [Git](http://git-scm.com/). On Debina/Ubuntu/Mint, just run  
    `$ sudo apt-get install git`

    Test:  
    `$ git --version`

    Configure Git:
    *   `$ git config --global user.name "_Your Name_"`
    *   `$ git config --global user.email "_your_email@some_domain.com_"`
    *   You should also set your system's EDITOR environment variable to something you like. Many people choose _nano_ or _vim_.

3.  Go to [GitHub](https://github.com) and create an account. You can use this account for all of your projects.

4.  Go to [the repository for this project](https://github.com/davidand36/SimpleExpressServerForHeroku) and click the _Fork_ button at the top right. This will create a copy (fork) of the repository in your own account.

    Rename your project: Go to your copy (`https://github.com/_your_account_/SimpleExpressServerForHeroku`). Click the project _Settings_ link. Type a new name (e.g., "YourProject") and click the _Rename_ button.

5.  At the command line, go to your projects directory, e.g.:  
    `$ cd ~/Projects`

    Clone your forked project to this directory:  
    `$ git clone git:github.com:_your_account_/_YourProject_.git`
    
    This will create a new directory, `~/Projects/YourProject`, and copy the project code there.

    Go to your new project directory:  
    `$ cd YourProject`

6.  Install the node modules required for this project:  
    `$ npm install`

7.  Test the project:
    1.  Start the Node server:  
        `$ node web.js`
    2.  You should see "Listening on port 6201".
    3.  In your browser, go to _http://localhost:6201_. You should see a basic Web home page.
    4.  You won't be able to do anything in this terminal while the server is running. Either open a new terminal or, at the command line, press Ctrl-C to stop the server.
    5. You can change the port used for this app by editing _web.js_. I like to use a different port number for each Web app I write so I can run several at the same time. (Only one program at a time can listen on any particular port.) 

8.  Go to [Heroku](https://signup.heroku.com/dc) and create an account. Choose _Node.js_ as your development language. You can use this account for all of your projects in various languages.

    You should walk through the _Getting Started_ tutorial at the Heroku site at some point, but these instructions should be enough for now.

9.  Install the [Heroku Toolbelt](https://toolbelt.heroku.com). Instructions vary by platform; for Debian/Ubuntu/Mint:  
    `$ wget -qO- https://toolbelt.heroku.com/install-ubuntu.sh | sh`

    Type  
    `$ heroku login`
    
    Enter the e-mail address and password you used to create your Heroku account.

10.  Test your setup:

    1.  Open a new terminal and go to your project directory.
    2.  Start the local Heroku server:  
        `$ foreman start web`
        
        It should tell you which port it is using, e.g. "Listening on port 6202".
    3.  In your browser, go to _http://localhost:6202_ (or whatever port you were given). You should see that basic Web home page.
    4.  At the command line, you can press Ctrl-C to stop the server. But, even better, you can leave it running while you work on the next steps. (Run the server in one terminal while you work in another.) Refreshing the browser should show changes as you make them.
    5.  You can control the port Foreman uses by creating a _.env_ file with the contents  
    `PORT=<your port>`  
    If you do this, be sure the line  
    `.env`  
    is in your _.gitignore_ file, so it doesn't get checked into your Git repository or uploaded to Heroku.

11.  Create a Heroku repository for this project:  
     `$ heroku create`

    Heroku assigns a unique name to your project, e.g., _infinite-journey-4288_ and creates a remote Git repository on its servers for your project. If you type  
    `$ git remote -v`  
    you should see two pairs of remote repositories: one labeled _heroku_ at `heroku.com` and one labeled _origin_ at `github.com`. The former is what Heroku uses to run your Web site. The latter is for safekeeping of your code and sharing with others.

12.  Modify these files:
    *   _package.json_: Change these fields:
        *   _name_: Your project name
        *   _version_: Your project version (update as appropriate)
        *   _description_: Describe your project
        *   _repository url_: Your GitHub repository
        *   _bugs url_: For your GitHub repository
        *   _homepage_: Your GitHub repository
        *   _keywords_: Terms characterizing your site
    *   _README.md_: Explain your project for GitHub users

13.  The _public/_ is all yours. Build your site there. Certainly change
    *   _favicon.ico_. (I personally use [Inkscape](http://www.inkscape.org/en/) for most graphics work.)
    *   _index.html_: the "home" page for the project.
    *   Replace or remove any other files in _public/_.
    *   Feel free to create subdirectories, CSS, JavaScript, graphics, and more.

14.  Once you have the first version of your site working and ready, check it into Git:
    *   Get a summary of what you have changed:  
        `$ git status`
    *   For files you have modified, check that the changes are what you want:  
        `$ git diff _filename_`
    *   Stage each file you are happy with:  
        `$ git add _filename_`
    *   Check again that everything you want to commit has been staged:  
        `$ git status`
    *   Commit the changes:  
        `$ git commit`

    Push your latest work to GitHub:  
    `$ git push origin master`

    (Git has many more features and actions than are mentioned here. Read up on it when you get a chance. Also notice that `git status` explains your choices, such as how to undo things, precisely if tersely.)

15.  Push your latest work to Heroku:  
    `$ git push heroku master`

16.  Test your Heroku Web site:  
    `$ heroku open`

    This opens your site in a browser.

    You can get information about your Heroku site's activity with commands like:  
    `$ heroku logs --tail` (quit with Ctrl-C)  
    and  
    `$ heroku ps`

17.  Continue to build your site, cycling through steps 13-15 as long as you want.

