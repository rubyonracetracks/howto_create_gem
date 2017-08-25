# Chapter 8: Adding Functionality

* If your gem is complex enough, you may need to work on it in multiple stages rather than risk confusion by trying to complete everything at once.
* Create a new branch for your current objective.
* Add RSpec tests for your current objective in the spec directory.
* Add the functionality in the lib directory.  Note that it may be necessary to make your app a class instead of a module.  You may also need to create an executable in the bin directory to run your gem.
* When all your tests pass, you are ready to push to the Git branch.  Make sure that all tests pass in continuous integration.  If they do, you are ready to merge this branch into the master branch.
* If necessary, repeat the above steps for the next step.
* Continue until your gem has all of the desired functionality.
