### Web Api Tests Using Configuration Loader
* Add api_config.properties to the root of the project

### Evolving into a multi-module test framework

- This topic is unique because iI've seen a lot of courses on how to build a UI, WebAPI, or any other kinds of tests using various tools and technologies. I've also seen a lot of automation test code bases that are fairly messy and difficult to extend and maintain. 
![](https://github.com/AAInternal/TestAutomationStrategy/blob/master/img/AutomationFrameworkFromScratch/Chapter5Slide2.png)

- Given all the fancy modern tools and technologies. How is that possible? 

    - This is because a better hammer does not make you a professional builder. And using a popular library doesn't mean one can create large, high quality frameworks. 

#### This overview will show you how to keep your test framework clean professional and maintainable. 
#### Overview
- Review popular techniques being applied when building frameworks
- Will map above techniques to what I developers call a "test refactoring pyramid"
- We will take a look at how frameworks abuse inheritance 
- Discover how this affects our future Work and how to re-factor that to composition.
- This will allow us to proceed to the next step: 
    - Split our single module framework to a multi module framework. 
    - Build a foundation upon which you can scale to hundreds or thousands of tests
  
* If you have written unit, integration, or system test before you know that a lot of test can be generated
  and become difficult to maintain. 

[Image]

* As you write more test, hopefully, you applied the best techniques discusses in most courses such as:
  * Refactor setup and clenup code in separate methods that that with @BeforeXXX and @AfterXXX depending on the libraries you use
  * Parametarized your tests to achieve good coverage with less lines of code
    * `@ParamerizedTest` or `@DataProvider`
    * Applied DRY (Do Not Repeat Yourself) and DAMP principles to keep them readable. 

#### Your biggest Enemies

[Image]

* Abuse of Inheritance
  * Code becomes really inflexible
* Monolith module

* To fight the enemies above we will implement composition or modularization by creating multiple maven modules

