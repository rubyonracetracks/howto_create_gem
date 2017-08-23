# Chapter 4: RuboCop

RuboCop is a Ruby code analyzer that points out violations of the Ruby Style Guide. Violations don't cause the code to fail but can slow down expert Rubyists when they read and analyze the code. It's best to add RuboCop very early in a project, because it gets increasingly difficult to introduce later on.

SPECIAL NOTE: The number of RuboCop offenses you get may be different from the number listed here. The point is to eliminate offenses by fixing the issues cited or by configuring the .rubocop.yml file to ignore them.

## New Branch
Enter the command "git checkout -b 04-rubocop".

## Updating the Gemspec
* In the (name of gem).gemspec file, add the following line just before the final "end":
```
  spec.add_development_dependency 'rubocop'
```
* Enter the command "sh gem_test.sh".  All tests should pass.

## Complying with RuboCop
* Enter the command "bundle exec rubocop -D".  At this point, I see that there are 46 offenses.
* Replace the double quotes in bin/console with single quotes.
* Enter the command "bundle exec rubocop -D".  At this point, I see 43 offenses.
* Edit the lib/(name of gem)/version.rb file.  Replace the line defining the version number with the following:
```
  VERSION = '0.0.0'.freeze
```
* Enter the command "bundle exec rubocop -D".  I see 41 offenses.
* In spec/spec_helper.rb, replace the double quotes with single quotes.
* Enter the command "bundle exec rubocop -D".  I see 38 offenses remaining.
* In spec/(name of app)_spec.rb, replace the double quotes with single quotes.  I see 35 offenses remaining.
* In lib/(name of app).rb, replace the double quotes with single quotes, and add the line "#" before the line that begins with "module".  I see 33 offenses remaining.
* In the Rakefile, replace the double quotes with single quotes.
* In the Rakefile, replace the line "task :default => :spec" with the following:
```
task default: :spec
```
* Enter the command "bundle exec rubocop -D".  I see 30 offenses remaining.
* In the Gemfile, replace the double quotes with single quotes in the line beginning with "source".  Add a space between "{" and "|repo_name|".
* Enter the command "bundle exec rubocop -D".  I see 28 offenses remaining.
* In (name of spec).gemspec, follow RuboCop's recommendations for replacing double quotes with single quotes.
* Enter the command "bundle exec rubocop -D".  I see 10 offenses remaining.
* In the gemspec file, follow RuboCop's recommendations for the line containing "spec.files".
* Enter the command "bundle exec rubocop -D".  I see 8 offenses remaining.
* In the gemspec file, add a blank line after "# coding: utf-8".
* Enter the command "bundle exec rubocop -D".  I see 7 offenses remaining.
* In the gemspec file, use quotes instead of "%q{}" for the summary and description parameters.
* Enter the command "bundle exec rubocop -D".  I see 3 offenses remaining.
* Create the file .rubocop.yml with the following content (with the name of the gemspec file filled in):
```
Metrics/LineLength:
  Exclude:
    - (name of gemspec file)
```
* Enter the command "bundle exec rubocop -D".  There should be no offenses remaining.  (If there are, correct them, and run "bundle exec rubocop -D" to make sure they're gone.)

## git_check.sh
* Add the following lines to git_check.sh just before the "git status" section:
```
echo '----------------------'
echo 'bundle exec rubocop -D'
bundle exec rubocop -D
```
* Enter the command "sh git_check.sh".  All tests should pass, and there should be no offenses.

## Wrapping Up
* Enter the following commands:
```
git add .
git commit -m "Added rubocop"
git push origin 04-rubocop
```
* Go to the GitHub repository and click on the "Compare and pull request" button for this branch.
* Accept this pull request to merge it with the master branch, but do NOT delete this branch.
* Enter the following commands:
```
git checkout master
git pull
```

## Conclusions
From now on, be sure to check for RuboCop compliance before entering a "git commit" command.  This is now covered in the git_check.sh script.
