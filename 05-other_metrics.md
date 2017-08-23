# Chapter 5: Other Metrics

In the previous chapter, you added the RuboCop tool. In this chapter, you will add additional code analyzers. As was the case with RuboCop, violations don't necessarily mean failing tests, but they can slow down expert Rubyists when they read and analyze the code. Additionally, some of these tools can flag outdated and insecure gems.

## New Branch
Enter the command "git checkout -b 05-other_metrics".

## Updating the Gemspec
* In the (name of gem).gemspec file, add the following lines just before the final "end":
```
  spec.add_development_dependency 'bundler-audit'
  spec.add_development_dependency 'gemsurance'
  spec.add_development_dependency 'ruby-graphviz'
  spec.add_development_dependency 'simplecov'
```
* Enter the command "sh git_check.sh". All tests should pass, and there should be no offenses.

## code_test.sh
* Add the file code_test.sh with the following content:
```
#!/bin/bash

DIR_PARENT="${PWD%/*}"
DIR_TMP="$DIR_PARENT/tmp"
mkdir -p log
rm -rf tmp

echo '--------------'
echo 'bundle install'
bin/setup >/dev/null

echo
echo '----------------------'
echo 'bundle exec rubocop -D'
bundle exec rubocop -D

echo
echo '------------------------'
echo 'bundle exec bundle-audit'
bundle exec bundle-audit

echo '----------------------------------------------------------'
echo 'bundle exec gemsurance --output log/gemsurance_report.html'
bundle exec gemsurance --output log/gemsurance_report.html
echo 'Gemsurance Report: log/gemsurance_report.html'

echo '------------------------------------------------------------------------'
echo 'bundle viz --file=log/diagram-gems --format=svg --requirements --version'
bundle viz --file=log/diagram-gems --format=jpg --requirements --version
echo 'Gem dependency diagram: log/diagram-gems.jpg'
```
* Enter the command "sh code_test.sh".

## Wrapping Up
* Enter the following commands:
```
git add .
git commit -m "Added additional metrics"
git push origin 05-other_metrics
```
* Go to the GitHub repository and click on the "Compare and pull request" button for this branch.
* Accept this pull request to merge it with the master branch.  When the merge has been completed, you may delete this branch.
* Enter the following commands:
```
git checkout master
git pull
```
