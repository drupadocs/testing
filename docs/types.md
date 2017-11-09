# Types of Testing
There are 4 major categories of testing available out-of-box Drupal core. These tests focus on different aspects of code and functionality. Some part of the code could have tests on multiple types.

## Types

## 1. Unit
Basic tests without bootstrap/create Drupal site. Function/method level testing 


## 2. Kernel



## 3. Functional
Checks behaviour of an application as an user. This would allow to test end-to-end functionality.

![](https://raw.githubusercontent.com/drupadocs/drupal-core/master/testing/PHPUnit-Functional-Testing-Component-Diagram.png)

>Note:  
When assert, labels, Button text, messages are not translated (i.e. passed in `t()`) as these tests are running in single language instance. Check [here](https://www.drupal.org/docs/8/phpunit/phpunit-browser-test-tutorial#t) for more details.


## 4. Functional Javascript

  
![](https://raw.githubusercontent.com/drupadocs/drupal-core/master/testing/PHPUnit-Javascript-testing-Component-Diagram.png)

## Structure

### Class

![](https://user-images.githubusercontent.com/1220029/32525579-fe73f744-c41c-11e7-816f-cfc86f44fe22.png)

### Directory

![](https://user-images.githubusercontent.com/1220029/32525578-fe5ade1c-c41c-11e7-8b09-e949e0057240.png)  









