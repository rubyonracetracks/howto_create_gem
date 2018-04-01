# Chapter 7: Updating the Documentation

On the CodeClimate page for your project, you will see 5 issues.  In this chapter, you will address them all.

## Code of Conduct
* In the CODE_OF_CONDUCT.md file, fill in your email address.

## License
* In the LICENSE.txt file, fill in your name.

## Gemspec File
* Assuming that you intend to publish your gem at rubygems, org, remove the entire section that begins with "if spec.respond_to?(:metadata)".
* Enter the command "sh git_check.sh".  All tests should pass, there should be 100% test coverage, and there should be no offenses.

## README.md File
* Fill in your GitHub username in the "Contributing" and "Code of Conduct" sections.
* Fill in the description of your gem.
* Fill in the instructions on how to use your gem.
* Replace the Development section with the following:
```
* To test this gem, enter the command "sh gem_test.sh".
* To install this gem, enter the command "sh gem_install.sh".
* To test the source code for various metrics, enter the command "sh code_test.sh".
* To do all of the above, enter the command "sh all.sh".
* To run an interactive prompt, enter the command "sh console.sh".
```

## Wrapping Up
* Enter the following commands:
```
git add .
git commit -m "Filled in the documentation"
git push origin master
```
* The CodeClimate page should now show no issues in your project.
