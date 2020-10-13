### Project Setup
- Clone this repo into a current directory to get the modularized sample of a JUnit Framework
- To get a version that is not separated into different modules go to:
[https://github.com/yelenagotraining/JavaAutomationFrameworkNoModules](https://github.com/yelenagotraining/JavaAutomationFrameworkNoModules)

### Evolving into a multi-module test framework

- This topic is unique because iI've seen a lot of courses on how to build a UI, WebAPI, or any other kinds of tests using various tools and technologies. I've also seen a lot of automation test code bases that are fairly messy and difficult to extend and maintain. 
![](https://raw.githubusercontent.com/yelenagou/AutomationStrategyImages/main/img/AutomationFrameworkFromScratch/Chapter5Slide2.png)

- Given all the fancy modern tools and technologies. How is that possible? 

    - This is because a better hammer does not make you a professional builder. And using a popular library doesn't mean one can create large, high quality frameworks. 
![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/Chapter5Slide3.png)
#### This overview will show you how to keep your test framework clean professional and maintainable. 
#### Overview
- Review popular techniques being applied when building frameworks
- Will map above techniques to what I developers call a "test refactoring pyramid"
- We will take a look at how frameworks abuse inheritance 
- Discover how this affects our future Work and how to re-factor that to composition.
- This will allow us to proceed to the next step: 
    - Split our single module framework to a multi module framework. 
    - Build a foundation upon which you can scale to hundreds or thousands of tests
 
![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/Chapter5Slide5.png) 
* If you have written unit, integration, or system test before you know that a lot of test can be generated
  and become difficult to maintain. 
  
![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/Chapter5Slide6.png)

* As you write more test, hopefully, you applied the best techniques discusses in most courses such as:
  * Refactor setup and clenup code in separate methods that that with @BeforeXXX and @AfterXXX depending on the libraries you use
  * Parametarized your tests to achieve good coverage with less lines of code
    * `@ParamerizedTest` or `@DataProvider`
    * Applied DRY (Do Not Repeat Yourself) and DAMP principles to keep them readable. 

#### Your biggest Enemies

![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/Chapter5Slide7.png)

* Abuse of Inheritance
  * Code becomes really inflexible
* Monolith module
* To fight the enemies above we will implement composition or 
modularization the monolith by creating multiple maven modules. 
    * Each with property defined responsibility. 

* If you clone this repo, you'll see we have a lot of defferent tests, testing a lot of different ares
of the system:
[https://github.com/yelenagotraining/JavaAutomationFrameworkNoModules](https://github.com/yelenagotraining/JavaAutomationFrameworkNoModules)

- In our case, for demo purposes, we have a few UI test

    - One UI test tests something useful
    ![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/UILoginTest.png)
       
    - Another UI test is a dummy test
     ![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/UIDummyTest.png)

    - As a good testing practice, string generators are useful to create new types of input to keep tests valuable

- The String randomizer is used in different classes.
> It's importnat to remember that we must avoid duplication by moving common classes into a higher common class. 
![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/FrameWorkHierarchyBefore.png)

> First Bad Solution - Extending base class:

* For example, we want to use string generator in our API and UI tests.
    * Also, we went to use our properties in both set of tests
* First bad solution is to use inheritance to solve this problem. 
    * Right now, our API tests do not extend any base classes. 

* First bad solution is to use inheritence 
    * Our API tests do not extend any parent classes, at the moment
    One option is for one class to extend the other. 
![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/FrameWorkUseInheritance.png)
    * The side effect of this is we are mixing this that should be not be mixed
    * With inheritence we create Is-A relationship 
    * Inherit unwatned UI Code including set up and cleanup. 
![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/FrameworkIsARelationship.png)

#### Second Bad Solution - Inheretance Hierarchy

* Make a parent class on top of other classes

* This is a bad idea because we are creating one monolith class. 
    * The structure is going to higher and higher and all the functionality is going to get pulled up.
![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/FrameworkHirerarchy.png)
    
    * Pulling all the functionality in the top most class will create something called a God Class

#### No to God Class
* God Class: a class which knows too much or does too much. 
* God Class connected to way too many other classes and has grown
    beyond all logic. 
    
* God class is described as follows:
 - If you want your banana, you'll get your banana, but you will also get the animal that is holding it. 
 Along with a jungle it lives in. 
![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/Chapter5Slide12.png)

- What if you don't want any of the extra stuff?

### Replace Inheritance with Composition 
- To achieve composition you must establish a HAS-A relationship vs IS-A relationship
- With traditional OO software you establish logical relationship
* For example:
    * Savings account IS-A account vs Person HAS-A Account

![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/Chapter5Slide15.png)
)

* The logic with tests is a bit different. Base class should only extend to run setup and clenup.
  For most other thing a test  HAS-A piece of functionality.
* Test should have a functionality by statically importing it or by creating a helper object.
![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/Chapter5Slide16.png)
* We create two separate classes, one for String Utils and one for Properties Utils

![](https://github.com/yelenagou/AutomationStrategyImages/blob/main/img/AutomationFrameworkFromScratch/Chapter5Slide17.png)
 
 





    