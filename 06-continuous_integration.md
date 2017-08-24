# Chapter 6: Continuous Integration Badges

## Procedure
* Enter the following command:
```
git rm .travis.yml # You will use CircleCI instead of Travis.
```
* Add the following to the gemspec file just before the last "end" line:
```
  spec.add_development_dependency 'codeclimate-test-reporter'
```
* Enter the command "sh git_check.sh".  The code-climate-test-reporter gem will be installed.  All tests should pass, and there should be no offenses.
* Enter the following commands:
```
git add .
git commit -m "Added codeclimate-test-reporter"
git push origin master
```
* Go to https://gist.github.com/jhsu802701/bfa9a016d5edcbeca8bd6a7ab78bfbae for further instructions.  Remember to add the badges and push the changes to your README.md file.
