# Types of Testing
There are 4 major categories of testing available out-of-box Drupal core. These tests focus on different aspects of code and functionality. Some part of the code could have tests on multiple types.

All these types are heavily based generic PHP libraries: [PHPUnit](https://phpunit.de/), [MinkPHP](http://mink.behat.org/en/latest/) and [Guzzle](http://docs.guzzlephp.org/en/stable/). Basic knowledge on those would help a lot.

## Types

## 1. Unit
Basic tests without bootstrap/create Drupal site. Function/method level testing 


## 2. Kernel
Kernel test allows to do integration testing which helps to setup dependency injection container. Also allows to bootstrap/load required drupal elements like entity schema and module schemas.

## 3. Functional
Checks behaviour of an application as an user. This would allow to test end-to-end functionality.

![](https://raw.githubusercontent.com/drupadocs/drupal-core/master/testing/PHPUnit-Functional-Testing-Component-Diagram.png)

>Note:  
When assert, labels, Button text, messages are not translated (i.e. passed in `t()`) as these tests are running in single language instance. Check [here](https://www.drupal.org/docs/8/phpunit/phpunit-browser-test-tutorial#t) for more details.


## 4. Functional Javascript

  
![](https://raw.githubusercontent.com/drupadocs/drupal-core/master/testing/PHPUnit-Javascript-testing-Component-Diagram.png)

## Structure

{% method %}

### Class

![](https://user-images.githubusercontent.com/1220029/32525579-fe73f744-c41c-11e7-816f-cfc86f44fe22.png)

### Directory

![](https://user-images.githubusercontent.com/1220029/32525578-fe5ade1c-c41c-11e7-8b09-e949e0057240.png)  

{% endmethod %}


## Reference
1. [UnitTestCase](https://github.com/drupal/drupal/tree/8.5.x/core/tests/Drupal/Tests/UnitTestCase.php)
2. [KernelTestBase](https://github.com/drupal/drupal/tree/8.5.x/core/tests/Drupal/KernelTests/KernelTestBase.php)
3. [BrowserTestBase](https://github.com/drupal/drupal/tree/8.5.x/core/tests/Drupal/Tests/BrowserTestBase.php)
4. [JavaScriptTestBase](https://github.com/drupal/drupal/tree/8.5.x/core/tests/Drupal/FunctionalJavascriptTests/JavascriptTestBase.php)









