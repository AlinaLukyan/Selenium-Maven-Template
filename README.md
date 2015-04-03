Selenium-Maven-Template
=======================

A maven template for Selenium that has the latest dependencies so that you can just check out and start writing tests in five easy steps.


1. Open a terminal window/command prompt
2. Clone this project.
3. CD into project directory
4. mvn clean verify

All dependencies should now be downloaded and the example google cheese test will have run successfully (Assuming you have Firefox installed in the default location)

### What should I know?

- To run any unit tests that test your Selenium framework you just need to ensure that all unit test file names end, or start with "test" and they will be run by step 4.
- The maven surefire plugin has been used to create a profile with the id "selenium-tests" that configures surefire to pick up any java files that ends with the text "WebDriver".  This means that as long as all of your selenium test file names end with WebDriver.java they will get picked up and run when you perform step 4.

### Anything else?

Yes you can specify which browser to use by using one of the following switches:

- -Dbrowser=firefox
- -Dbrowser=chrome
- -Dbrowser=ie
- -Dbrowser=opera
- -Dbrowser=htmlunit
- -Dbrowser=phantomjs

You don't need to worry about downloading the IEDriverServer, or chromedriver binaries, this project will do that for you automatically.

Not got PhantomJS?  Don't worry that will be automatically downloaded for you as well!

You can specify a grid to connect to where you can choose your browser, browser version and platform:

- -Dremote=true 
- -DseleniumGridURL=http://{username}:{accessKey}@ondemand.saucelabs.com:80/wd/hub 
- -Dplatform=xp 
- -Dbrowser=firefox 
- -DbrowserVersion=33

You can even specify multiple threads (you can do it on a grid as well!):

- -Dthreads=2

If the tests fail screenshots will be saved in ${project.basedir}/target/screenshots


Comments from http://stackoverflow.com/questions/16005672/running-multiple-selenium-tests-at-the-same-time:

You can run multiple instances of chromedriver locally quite easily, just instantiate multiple driver objects, chromedriver will keep the profiles separate and find a port to run on all by itself.

Here a link to an example that can run multiple tests using TestNG and Maven:

https://github.com/Ardesco/Selenium-Maven-Template

Just clone the above project and run the following in the command line:

mvn verify -Pselenium-tests -Dbrowser=chrome -Dthreads=2
It takes advantage of TestNG's ability to manage the thread pool and will open up multiple instances if specified. You can do the same thing with jUnit but you'll need to write a custom test runner to fire the tests off into individual threads.

If you decide to use gradle it can deal with managing the thread pools for you with both TestNG and jUnit and a lot of people prefer it to maven.
