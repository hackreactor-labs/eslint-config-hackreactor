# Enforcing Hack Reactor's Style Guide

This is an installable ESLint configuration file that enforces Hack Reactor's style guide.

[ESLint](http://eslint.org/) is a tool for identifying and reporting on patterns found in JavaScript code, with the goal of making code more consistent and avoiding bugs. It's an invaluable tool when working with other engineers.

## System Requirements

A working version of [Node.js](https://nodejs.org/en/)

## Installation

Install ESLint globally by running the following command in your terminal:
```
npm install -g eslint
```

Install the Hack Reactor style guide configuration:
```
npm install -g hackreactor-labs/eslint-config-hackreactor
```

## Enforce the style guide in a project

Create an `.eslintrc.js` file in the root directory of your repository:

```js
module.exports = {
  extends: 'hackreactor',
  rules: {
    // Rules here will override the 'hackreactor' configuration
    // http://eslint.org/docs/rules/
  }
};
```

Now, you can run ESLint from [the command line](http://eslint.org/docs/user-guide/command-line-interface):

```
eslint [options] [file|dir|glob]*
```
For example:
```
eslint someFile.js someOtherFile.js
eslint client/**
```

If you don't see any output, your files have passed all the linting rules. In addition to the command line interface, ESLint can be integrated into various [build systems](http://eslint.org/docs/user-guide/integrations#build-systems) like [Gulp](https://github.com/adametry/gulp-eslint), [Grunt](https://www.npmjs.com/package/grunt-eslint), or a [pre-commit hook](https://github.com/hackreactor-labs/pomander).

## Enforce the style guide in Sublime Text

By downloading and configuring a couple of plugins for Sublime Text, you can receive live feedback about your code's syntax and style, much like spelling errors in a word document. This is a very useful practice to build muscle memory around good style habits.

### Install SublimeLinter
The easiest way to download plugins for Sublime Text is through [Package Control](https://packagecontrol.io/installation). With Package Control, you can install [SublimeLinter](http://www.sublimelinter.com/) and its [ESLint plugin](https://github.com/roadhump/SublimeLinter-eslint) from the Command Palette (`cmd + shift + p`):

* `Package Control: Install Package -> SublimeLinter`
* `Package Control: Install Package -> SublimeLinter-contrib-eslint`

### Configure SublimeLinter

Without any configuration, SublimeLinter will only enforce rules from a `.eslintrc` file. If no `.eslintrc` file exists among the open files, SublimeLinter will fall back to the default behavior the `eslint` command, and only enforce syntax errors.

You can configure SublimeLinter to enforce the Hack Reactor style guide on files/projects without an `.eslintrc` file.

Navigate to `Preferences -> Package Settings -> SublimeLinter -> Settings - User` and update the `linters` section to the following:

```json
"eslint": {
  "@disable": false,
  "args": [
    "--config",
    "hackreactor"
  ],
  "excludes": []
}
```
