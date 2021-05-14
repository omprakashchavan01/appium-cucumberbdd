# appium-cucumberbdd
Appium mobile test automation framework with Page Object Model design using Java + Cucumber + Maven + JUnit.
Framework follows many of the industry best practices and supports Android and iOS in a single code base.



Technologies/Tools used in building the framework
=================================================
- IntelliJ - IDE
- Appium - Mobile Automation library
- Maven - Build automation tool
- Java - Programming language
- Cucumber - BDD
- Gherkin - DSL
- JUnit - Unit testing framework
- Log4J - Logging framework
- Extent Reports - Reporting framework
- JSON - Test Data
- XML - Static text
- GitHub - Version control
- Jenkins - CI/CD

Framework implements below best practices
=========================================
- Code reusability
- Code readability
- Scalable automation (demonstrated using multiple test classes)
- Uses explicit waits
- Abstraction layer for UI commands like click, sendkeys, etc.
- Parameterization using TestNG XML and config.properties
- Abstraction layer for test data
- Abstraction layer for static text
- Supports iOS and Android
- Demonstrates how to define UI elements that are common across pages (e.g. menu bar, side bar, etc.)
- How to recover from test failure/ how to write fail safe test cases
- Scrolling for both Android and iOS (using touchaction, uiScrollable, mobile:scroll)
- Demonstrates how to effectively capture Screenshots/Videos
- Supports parallel execution using JUnit
- Supports parallel execution on multiple real Android and iOS devices
- Start Appium server propgrammatically
- Supports Cucumber-HTML-Reporter plugin
- Integrated with Log4J2 Logging framework



============================================
Cucumber BDD framework with Appium:

What are we automating?
=========================
Sauce Lab's demo mobile app
GitHub: https://github.com/saucelabs/sample-app-mobile
Releases (Latest APKs and IPAs): https://github.com/saucelabs/sample-app-mobile/releases

iOS: Steps to build app for simulator: 
Refer this lecture from TDD framework design: Page Object Model (POM) Design with Appium - Part 4
Watch from 9:02 minutes to 17:40 minutes

Login Feature file
Scenarios:
Login with an invalid user name
Login with an invalid password
Login with a valid user name and password

Products Feature file
Scenarios:
Validate product info on Products page
Validate product info on Product Details page

Steps:
=======

1. IntelliJ setup for Cucumber
===============================
https://www.jetbrains.com/idea/download/#section=windows
Download community edition
Install by selecting default options
Launch
Select default options
Configure -> Plugins -> Search Cucumber -> Install plugin "Cucumber for Java". 
It will ask to install Gherkin plugin as well.
Restart IDE

2. Maven setup
===============
https://maven.apache.org/download.cgi
Download Zip
Unzip and copy to say c:\maven

Windows:
Edit System environment variable PATH and add c:\maven\bin
Open command prompt and type mvn -v

Mac:
Open terminal and navigate to home dir by typing cd ~/
open -e .bash_profile
Add <path_to_maven_bin_folder> to PATH
type mvn -v
Note: If on latest Mac OS Catalina, it uses zsh and not bash. 
What this means is, your change will not persist if you exit and launch terminal.
To resolve this, refer first comment on my video: https://youtu.be/2-3r7WPubes

For any issue, you can always refer Maven website or search on internet. This is fairly simple setup.

3. Create new Maven project
============================

4. Add Cucumber JVM and Cucumber-JUnit dependencies
===================================================
https://cucumber.io/docs/installation/java/
https://cucumber.io/docs/cucumber/api/#junit

5. Add other dependencies: Appium, JSON, Log4J2
===============================================

6. Create Runner file: src/test/java/com/qa/runners/MyRunnerTest
========================
[glue, features]

7. Create feature files:
=========================== 
src/test/resources/Login.feature and Products.feature
Gherkin basics - https://cucumber.io/docs/gherkin/reference/

8. Create step defination files: 
================================
src/test/java/com/qa/stepdef: Login and Products
https://cucumber.io/docs/gherkin/step-organization/

9. Copy apps to src/test/resources/app
=====================================

10. Copy config.properties and log4j2.xml
=========================================
log4j2 configurations: https://github.com/omprakashchavan01/log4j2_properties
Video Tutorials: https://www.youtube.com/playlist?list=PLIuQPt4XLm7BEVaydA8zSt4zpguT1joN_

11. Copy TestUtils class to src/main/java/com/qa/utils
======================================================

12. Create hooks under src/test/java/stepdef
=============================================

13. Create GlobalParams under src/main/java/com/qa/utils
========================================================
platformName, udid, deviceName, systemPort,chromeDriverPort, wdaLocalPort, webkitDebugProxyPort

14. Initialize global params and add Thread Context for Log4j2 in Before hook
========================

15: Create ServerManager
===========================
Programmatically start Appium Server (Mac and Windows): 
https://www.youtube.com/playlist?list=PLIuQPt4XLm7BEVaydA8zSt4zpguT1joN_

16. Start server in Before hook and stop service in After hook
=============================================================

17. Create PropertyManager
===========================

18. Create CapabilitiesManager
=============================

19. Create DriverManager
===========================

20. Initialize driver in Before hook and Quit in After hook (and set to null)
====================================

21. Add Base Page and Page Objects
===================================
Page Object Model design and Scrolling: https://www.youtube.com/playlist?list=PLIuQPt4XLm7BEVaydA8zSt4zpguT1joN_

22. Update step defination files with actual code
================================================

23. Execute Runner and "mvn test" with parameters
================================================

24. Embed Screenshot in Before hook
=====================================

25. Create VideoManager
========================
Video tutorial: https://www.youtube.com/playlist?list=PLIuQPt4XLm7BEVaydA8zSt4zpguT1joN_

26. Start video in Before hook and stop in After hook
=========================

27. Moving server and driver initialization from Cucumber hooks to JUnit's BeforeClass and AfterClass
===============================

28. Execute Runner and execute "mvn test" with parameters
=========================================================

28. Integration with Cucumber HTML Reports
============================================
	cucumber-jvm reports (Jenkins plugin): https://github.com/jenkinsci/cucumber-reports-plugin
	cucumber-jvm reports (cucumber): https://gitlab.com/monochromata-de/cucumber-reporting-plugin
Add Dependency
Add plugin in Runner

29. Import project on Mac and execute for iOS using terminal
==============================================
Revise mvn setup
navigate to home directory cd ~/
open -e .zprofile

30. Execute for both iOS and Android in parallel
================================================


Seperate tutorials:
=====================

Cucumber with TestNG
=====================
- Parallel Execution

Extent reporting
======================
- Using API
- Using Adapter
- Parallel Execution 

Dependency injection: 
=======================
https://cucumber.io/docs/cucumber/state/#dependency-injection
http://www.thinkcode.se/blog/2017/04/01/sharing-state-between-steps-in-cucumberjvm-using-picocontainer


Extent reports:
use adaptor (current: 1.0.11)
use spark reporter
extent.properties example that's working: https://github.com/salunkhe-ravi/Selenix/blob/master/Selenix/src/test/resources/extent.properties
extent.properties example: https://github.com/extent-framework/extentreports-cucumber4-adapter/issues/20#issuecomment-601591963
Note: currently, @Before and @After are working, but @BeforeStep and @AfterStep aren't. This will be fixed in the upcoming version 1.0.12 release, fix available with 1.0.12-SNAPSHOT.



