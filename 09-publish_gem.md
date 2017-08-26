# Chapter 9: Publishing Your Gem

## Prerequisites
* All of your desired functionality should be in your gem.
* All tests pass, test coverage is 100%, and there are no offenses.
* Everything panned out under the continuous integration tools, and you have merged your changes into the master branch.

## Reset
* Reset your Docker container.
* Delete the local copy of your gem's source code.
* Download your gem's source code into the shared directory of your Docker container.
* In the root directory of the source code, enter the command "sh all.sh".  All tests should pass, there should be no offenses, and your gem should be installed smoothly.

## Trying Out Your Gem
* Reset your Docker container.
* In the root directory of your gem's source code, enter the command "gem install *.gem".
* Enter the command "cd; cd shared".
* Try out your new gem.  (You may need to enter the command "irb" first.  In this case, don't forget to enter the command "require '(name of gem)'.)
* If your gem works as expected, you are ready to publish it.

## Pushing Your Gem
* If you have not already done so, sign up for an account at https://rubygems.org/.
* When you ran the all.sh script, a *.gem file should have been created.
* Enter the command "gem push (name of *.gem file)".  Enter your email address and password when prompted to do so.
* Congratulations!  Your new gem has been published.
