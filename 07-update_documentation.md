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

## Wrapping Up
* Enter the following commands:
```
git add .
git commit -m "Filled in the documentation"
git push origin master
```
* The CodeClimate page should now show no issues in your project.
