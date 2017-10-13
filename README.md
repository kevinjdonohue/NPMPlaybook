# NPM Playbook

A repo for storing notes and examples from the NPM Playbook PluralSight course.

## NPM Basics

### Package vs. Module

* Package - single JS library
* Module - a collection of a packages

### Common Commands

* ```npm search {term}``` - This is used to search for a package.

* ```npm install``` - This is used to pull down all of the packages references in the package.json file for a given project.  An example of when you would use this would be when you have just pulled down a repository from GitHub that is a JavaScript or Node project that contains a package.json file.

* ```npm start``` - This is used to "start" up a given project - invoking whatever start script(s) are stored in the package.json file.  You can review the package.json to verify whether a given project has a start script.

* ```npm test``` - This is used to execute the (unit) tests for a given project.  Again this is a script from the package.json file.

* ```npm -h``` - This brings up the list of commands and general help.

* ```npm {command} -h``` - This brings up help specific to the given command.

* ```npm help {command}``` - This can be used to launch a browser and display the official npm help page for the given command.

* ```npm help-search {topic}``` - This will search for articles, etc. regarding this given topic.

### package.json

Tracks dependencies for packages that you download.  Also, you can add scripts to the file.

#### package.json commands

* ```npm init``` - This command allows you to interactively create a package.json file.

* ```npm set init-author-name``` - Does what it sounds like, stores a name as the default author so you don't have to re-enter it everytime you generate a new package.json file.

* ```npm set init-author-email``` - Does what it sounds like, stores an email as the default email address so you don't have to re-enter it everytime you generate a new package.json file.

* There are other values you set by default such as license, version number, etc.

* ```npm get init-author-name``` - Retrieves the given init- values

* ```npm config delete init-author-name``` - Deletes the given init- value

* All of the these values are stored in a ```.npmrc``` file

### Commands In Detail

### ```npm install {package}```

### Options:

* ```--save``` - Append this to the end of your install statement so that the dependencies section of your package.json file will be updated.

* ```--save-dev``` - Append this to the end of your install statement so that the dev dependencies section of your package.json file will be updated.  E.g. A package for unit testing such as Mocha or Karma.

* There is an *optional* section in packages.json - but since hardly anyone ever uses it, it's not common enough to worry about.

* ```-g``` - This installs the package globally, instead of locally (current directory/project).  You often do this for dev dependencies like testing frameworks, build systems like Gulp or Grunt, etc..

* ```{package name}@{semantic version number}``` - This allows us to install specific versions of a given package.  E.g.  npm install underscore@1.4.5

* ```--save-exact``` - This is used typiically when you are installing a specific version of a package and you don't want npm to update the version of that package if updates become (or are) available.
  * npm install underscore@1.8.2 --save --save-exact.  Note:  The leading ^ will not be present in the dependencies or dev dependencies section for the given package.
  * "underscore": "^1.8.2" versus "underscore": "1.8.2".

### Alternative Sources

In addition to providing a package name to search, install, uninstall or update it via the ```npm``` CLI, you can also execute those same commands for packages available in other ways:

* Via a URL - ```npm install http://github.com/someproject/somepackage```
* Via a GIST - ```npm install gist:{hash}```
* Via a folder or network drive - ```npm install ../hello-mars```


### ```npm list```

* Lists out all of the installed packages in a graphical tree.

* ```--depth {number of levels}``` - This is used to control how deep in the dependency tree to display.  E.g.  --depth 0 is how you display just the top level packages that are installed (locally).

* ```--global true``` - Does what you'd expect - it lists the packages that are installed globally rather than locally.

* These commands can be used in conjunction in order to produce different package lists.  E.g. --depth 0 --global true will list the top level, globally installed packages on your workstation.

* ```--long true``` - This is a formatting command that will increase how much data is returned in the list.  E.g. Using this setting along with --depth and --global true, you could create a detailed listing of all of the globally installed packages -- their full names, URLs, etc.

* ```--json true``` - You guessed it, it outputs the results in JSON.

* ```--parseable true``` - Another format for use programmatically, etc. - this lists the packages as file paths (e.g. /usr/local/lib/)

* ```--dev true``` - Yep, it only lists the dev dependencies.

* ```--prod true``` - You guessed it.

### ```npm uninstall {package}```

* ```--save``` - This removes the package from the packages.json file along with removing the packge itself.

* ```-g``` - You guessed it, just like above you can add this to the uninstall command to uninstall global packages instead of local ones.

### ```npm prune {package}```

Similar to uninstall, except it will handle packages that are no longer in the package.json file.

Running this command will remove any extraneous packages (not listed in the packages.json file).

* ```--production``` - This allows you to remove all of the dev dependencies in the case that you are readying your code to be delivered into Production.

### ```npm update```

Mechanism for updating all of the packages outlined in the package.json file, according to their specific versioning (see below).

* ```--dev``` - You guessed it.
* ```--prod``` - You guessed it.
* ```-g``` - Nuff said.

### ```npm test```

Mechanism for running the (unit) tests for a given project.  The "test" script is defined in the packagee.json file.



### package.json & versions

Related to the ability to install specific versions of packages, there are some methods for allowing or preventing the current version of a package from getting upgraded.

* ```^``` - Latest version of major release - appears in front of a version number indicates that regardless of the specified version, you are allowing npm to upgrade to the latest version.

* ```~``` - Latest version of a minor release - appears in front of a version number this indicates the opposite of the ^ - don't install beyond the specified version.

* ```*``` or ```X``` - This is the mechanism for getting the latest version, regardless of major or minor, for the given package.  Used in place of a ~ or ^ and a version number.

### Package Details

* ```http://npm.im/{packagename}``` - This will take you directly to the package's page on the npm website.
* ```http://www.npmjs.com/search``` - Best way to search instead of via the command line.
* ```npm repo {package}``` - This takes you directly to the repo website for the given package.  E.g. ```npm repo express```

### Updating NPM

* ```npm install npm@latest -g```
* NOTE:  You need to do this from an Administrative-level cmd window on Windows in order to not mess up NPM.

### Publishing a Package

Prepare / Create an npm user

1. Create user on npm website

    * Run ```npm adduser``` to add an authentication token to your .npmrc file

1. Setup your project in git

    * ```git init```

1. Create a new repository (via webpage, e.g. github.com, etc.)

    * ```git remote add origin {url}```

1. Create your package.json file

    * ```npm init```

    * Be really careful with data you put in your package.json file.

1. ```npm publish```

    * Publish the package to the NPM registry and make it available in git.

1. ```git tag {version}``` - do after pushing

1. ```git push --tags``` - pushes up the tag you just created

### Updating a Package

1. Make your updates

1. Update the version number in package.json file (following semantic versioning)

    * Alternatively:  You can have npm make these changes for you

1. ```npm version patch``` or ```npm version minor``` or ```npm version major```

    * NOTE:  npm will automagically make some commits for you - for the change and for the new tag

1. ```npm publish```