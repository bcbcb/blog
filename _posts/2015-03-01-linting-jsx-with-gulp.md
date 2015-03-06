---
layout: post
title: Linting JSX with Gulp
---

Using [JSHint with Gulp](https://www.npmjs.com/package/gulp-jshint) is great for automatically linting Javascript as part of your build system. If you're writing JSX for [React](https://facebook.github.io/react/), however, JSHint will break when it runs into JSX code. 

You can try to make JSHint ignore JSX, but it requires wrapping every portion of JSX in your code base, and it's more of a workaround than a solution.

You can also just compile JSX into regular Javascript before running it through JSHint. If you're using something like [Browserify](http://browserify.org/) to compile your JSX, you may end up with duplicate tasks and modules for compiling JSX.

The cleanest solution I've found is to use an alternative Javascript linter called [ESLint](http://eslint.org/).

## ESLint

ESLint is newer and allows for more flexible rule configurations. It also recently added support for linting JSX syntax.

You can install ESLint globally with NPM and manually run `eslint` on your JS files. Or you can just use the ESLint module for gulp.

Keep in mind that **ESLint does not lint JSX by default.**

Here's how to set up ESLint with Gulp to lint JSX:

### npm

First, install [gulp-eslint](https://github.com/adametry/gulp-eslint):

```npm install gulp-eslint```


### gulpfile.js
Then add it to your gulp file, specifying the source of your JS/JSX files you want to lint:

{% highlight js %}

var gulp = require('gulp'),
var eslint = require('gulp-eslint');

gulp.task('lint', function () {
    return gulp.src([
      'js/**/*.js',
      'js/**/*.jsx'
    ])
      .pipe(eslint())
      .pipe(eslint.format())
      .pipe(eslint.failOnError());
});

{% endhighlight %}

### .eslintrc

Lastly create an `.eslintrc` file with the following configuration:

{% highlight js %}

{
  "ecmaFeatures": {
   "jsx": true
}
{% endhighlight %}


You can add other options and rules to this file ([ESLint provides a lot to choose from](http://eslint.org/docs/configuring/)), but the above fields are necessary to enable JSX linting.

Now run your lint task in Gulp, and it will lint not only your JS code but also your JSX code.
