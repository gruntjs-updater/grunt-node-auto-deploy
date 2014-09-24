# grunt-node-auto-deploy

> Automatic deployment of your node apps via grunt to nginx-upstart server.

### About
It's based on node-deploy package. I rewrote it to use grunt. There is also no need to run init before first deployment. And upstart script/ngninx conf file don't need to be a part of git repository since they are created in ssh session. 

### Dependencies
This grunt task requires you to have linux with upstart (ubuntu tested) server running nginx, nodejs, npm and git.

## Getting Started
This plugin requires Grunt `~0.4.5`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-node-auto-deploy --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-node-auto-deploy');
```

## The "node_auto_deploy" task

### Overview
In your project's Gruntfile, add a section named `node_auto_deploy` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  node_auto_deploy: {
    options: {
      url: 'petrkrulis.cz',
      command: 'node server.js',
      port: '8081',
      path: '/var/www/sites',
      nginx: '/etc/nginx/sites-enabled',
      git: 'git://github.com/petrkrulis.cz/grunt-node-auto-deploy.git',
      branch: 'master',
      ssh: 'user@12.34.56.78'
    }
  },
});
```

### Options

#### options.url
Type: `String`

The URL of your app. If you don't own a domain name yet, just pass something.anything to it and add this to your hosts file. You can test the app from your browser then.

#### options.command
Type: `String`

Command used to start the app. Mostly it'll be something like 'node app.js' but you can use forever or anything else. 

#### options.port
Type: `String`

And your app is running on which port?

#### options.path
Type: `String`

Absolute path to the app. This task takes this path, creates a folder named by the options.url in it and clone the git repository specified in options.git.  

#### options.nginx
Type: `String`

Path to ngnix sites-enabled folder. Or basicaly any folder where nginx automatically load all conf files and use it in it's configuration. 

#### options.git
Type: `String`

Git repository to clone. It should contain the app you want to run :)

#### options.branch
Type: `String`

The branch which will be cloned from the git repository.

#### options.ssh
Type: `String`

SSH server adress. Use ssh key to login instead of password.

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).