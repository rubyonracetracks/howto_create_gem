# Chapter 2: Basic Scripts

In this chapter, you will add basic scripts in the root directory for executing routine tasks in only one step.  I find these scripts to be necessary, because projects have more tasks and details than I can remember verbatim.

## New Branch
Enter the following command:
```
git checkout -b 02-basic_scripts
```

## Updating the Gemspec File
* The gemspec file is the (name of gem).gemspec file in your gem's root directory.
* In this file, fill in the authors, email, summary, description, and homepage parameters.  The "bundle install" command will not work until certain parameters are provided.
* Enter the command "bundle install".  All of your gem's dependencies should be installed.

## gem_test.sh
* In the root directory of your gem, add the file gem_test.sh with the following content:
```
#!/bin/bash

echo '-----------------'
echo 'BEGIN TESTING gem'

bin/setup
rake

echo 'FINISHED TESTING gem'
echo '--------------------'
```
* Enter the command "sh gem_test.sh".  One test will fail.
* Edit the spec/(name of gem)_spec.rb file.  Change "expect(false).to eq(true)" to "expect(true).to eq(true)".
* Enter the command "sh gem_test.sh".  Both tests should now pass.

## gem_console.sh
* In the root directory of your gem, add the file gem_console.sh with the following content:
```
#!/bin/bash

bin/setup
bin/console
```
* Enter the command "sh gem_console.sh".  You should end up in the irb console.
* Enter "exit" to return to the normal Bash interface.

## gem_install.sh
* In the root directory of your gem, add the file gem_install.sh with the following content:
```
#!/bin/bash

echo '--------------------'
echo 'BEGIN INSTALLING gem'

gem build *.gemspec
gem install *.gem

echo 'FINISHED INSTALLING gem'
echo '-----------------------'
```
* Enter the command "sh gem_install.sh".  Your gem should be installed.
* NOTE: Yes, I am aware of the "rake install" command, but this script provides an experience much closer to that of an end-user.  For one of my gems (generic_app), I once had an error message about a conflict between the bin/setup executable and one of the gem dependencies when I installed it with the "gem install" command but not with the "rake install" command.  (I ended up rewriting the source code from scratch for both gems, though I was able to use the gem-specific parts of the old source code to save time.)

## git_check.sh
* In the root directory of your gem, add the file git_check.sh with the following contents:
```
#!/bin/bash

# Run this script before entering "git add" and "git commit".

sh gem_test.sh

echo '----------'
echo 'git status'
git status
```
* Enter the command "sh git_check.sh".  Both tests should pass.  You'll see that the scripts you just created are new, and the the spec/(name of gem)_spec.rb and (name of gem).gemspec have been modified.

## Wrapping Up
* Enter the following commands:
```
git add .
git commit -m "Added basic scripts"
git push origin 02-basic_scripts
```
* Go to the GitHub repository and click on the "Compare and pull request" button for this 02-basic_scripts branch.
* Accept this pull request to merge it with the master branch, and then delete this branch once it has been merged.
* Enter the following commands:
```
git checkout master
git pull
```
