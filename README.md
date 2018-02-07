# An introduction to npm

Node is a way of running Chrome's V8 JavaScript engine outside of the browser. You'll be learning more about this later in the course.

npm is Node's package manager. It's a repository of hundreds of thousands of useful pieces of code that you may want to integrate with your Node project.

npm also has a command line tool that lets us easily install, manage and run projects.

### `npm init`

`npm init` is the first command you need to know to create a Node project. It will 'initialise' your project by adding a file called `package.json` in the root directory.

npm will ask you some questions in your terminal after you run the command — your answers will be pre-filled into the `package.json`.

Don't worry, you can change your answers later by editing `package.json` manually.

### `npm install`

`npm install <package-name>` is how you install third party npm 'modules' (pieces of code from the npm repository). E.g. `npm install tape` will install the Tape testing library we'll be using soon.

npm will create a `node_modules` folder at the root of your project. This is where any third party modules you install are stored. Don't worry if you see way more files than you expect — npm also puts all the dependencies of the modules you install in here (and their dependencies, and their dependencies and ...)

You may see `npm install -g <package-name>`. The `-g` flag installs the module globally to your machine, rather than into the `node_modules` folder of that specific project. This can be useful for certain kinds of modules (e.g. command-line utilities that you might want to use anywhere).

### `.gitignore`

This is a good time to mention that you want to keep your `node_modules` folder off Github. There can be hundreds of thousands of files in this directory, which can make for some ugly commits. It can also take up a huge amount of space on something like Github as this folder can easily exceed 100MB for applications with lots of dependencies.

A `.gitignore` file is a way to tell Git to leave certain things alone.

If you are creating a repository on Github then you can use the 'Add .gitignore file' dropdown to automatically generate a variety of `.gitignore` files for different kinds of projects. You'll want to choose 'Node' here.

If you're working locally you can create a file called `.gitignore` at the root of your project and add `node_modules`.

### Saving dependencies

It's useful to declare dependencies within your project. This ensures that other people who clone your repo will be able to replicate your exact environment (since your node modules don't get synced with Github).

There are two ways to save dependencies:
+ `npm install <package-name> --save` (this option is not necessary unless you are using a
  version of npm older then 5.0, see the [npm documentation](https://docs.npmjs.com/cli/install))
+ `npm install <package-name> --save-dev`

At first glance these appear similar, but there is a distinction: `--save` is for dependencies that your application needs to run (i.e. things that need to be installed on the server delivering your application). `--save-dev` is for development dependencies that your project doesn't need in production (e.g. testing frameworks are generally only used in development — you don't need it on your live server).

In recent versions of npm, `npm install` will update your `package.json` with a section called 'dependencies', whilst adding the option `--save-dev` will put the dependency in a section called 'dev-dependencies'.

The idea is to make it clear to other developers who might work on your project what dependencies are required for it to work and what are only needed for the dev environment.

## Tasks

1. Create a new directory
2. Initialise the project with `npm init` (you can skip all the questions with the `-y` flag)
3. Install the [Tape](https://github.com/substack/tape) testing framework with `npm install tape --save-dev`
4. Have a look at the `package.json` file (and peek into `node_modules` if you dare!)
