# Chapter 8: Adding Functionality

* If your gem is complex enough, you may need to work on it in multiple stages rather than risk confusion by trying to complete everything at once.
* Create a new branch for your current objective.
* Add RSpec tests for your current objective in the spec directory.
* Add the functionality in the lib directory.
* It may be necessary to make your app a class instead of a module.
* If you wish to create an executable, you need to do the following:
  * Add an executable file in the bin directory to run your gem.
  * Change the value of the spec.bindir parameter in the gemspec from "exe" to "bin".
  * Edit the spec.executables parameter in the gemspec to specify the "bin" directory instead of the "exe" directory.
* When all your tests pass, you are ready to push to the Git branch.  Make sure that all tests pass in continuous integration.  If they do, you are ready to merge this branch into the master branch.
* If necessary, repeat the above steps for the next step.
* Continue until your gem has all of the desired functionality.
