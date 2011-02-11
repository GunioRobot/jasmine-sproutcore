# jasmine-sproutcore
- [http://github.com/gmoeck/jasmine-sproutcore](http://github.com/gmoeck/jasmine-sproutcore)

jasmine-sproutcore provides two tools for integrating [Jasmine](http://pivotal.github.com/jasmine/) with the [Sproutcore](http://github.com/sproutcore/sproutcore) framework.
  
- a Sproutcore framework that should be a drop-in replace QUnit for testing
- a set of helpers for doing things like click in integration tests
  
#Installation

To setup jasmine-sproutcore to work in your SproutCore project, we need to add the framework to your application.

    $ cd <your sproutcore project's root directory>
    $ mkdir frameworks # if you don't already have a frameworks folder
    $ cd frameworks
    $ git clone git://github.com/gmoeck/jasmine-sproutcore.git
  
Once this has been added to your application, you need to modify your buildfile to use the framework. If you have not previously modified your buildfile, you can just use the sample buildfile from jasmine-sproutcore by doing the following from within your frameworks folder:

    mv jasmine-sproutcore/Buildfile.sample ../Buildfile

If you have previously modified your buildfile, then you need to further modify it to include the following:

    require File.expand_path('../frameworks/jasmine-sproutcore/builders/jasmine_builder', __FILE__)
    ... (Your Previously written setup)
    namespace :build do
      desc "builds a jasmine unit test"
      build_task :test do
        Jasmine::Builder::Test.build ENTRY, DST_PATH
      end
    end

  
You can now write your tests the same way that you normally would using qunit, except in Jasmine. 

##Integration Helpers
When your using Jasmine to write integration tests, you have to account for the Sproutcore way of handling events. For example, in Sproutcore a click event is not the native click, but a mouse up, followed by a mouse down. In order to help to test this, jasmine-sproutcore also provides a layer of abstraction enable you to think strictly on a browser level. The following helpers are currently available:

###clickOn

clickOn takes a css selector, and does the same as if you normally clicked the element.

###fillIn

fillIn takes a css selector, and a value, and fills in that field with the value.

##License:
(The MIT License)

Copyright © 2011 Gregory Moeck

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the ‘Software’), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED ‘AS IS’, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
