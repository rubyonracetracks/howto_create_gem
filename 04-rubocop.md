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
* Enter the command "sh gem_test.sh".

### Wrapping Up
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

### Conclusions
From now on, be sure to check for RuboCop compliance before entering a "git commit" command.  This is now covered in the git_check.sh script.
