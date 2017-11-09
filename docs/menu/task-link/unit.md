# Unit Test
---

## Setup

```php
/**
 * {@inheritdoc}
 */
  protected function setUp() {
    $this->directoryList = ['module_name' => 'path/to/module'];
    parent::setUp();
  }
```

## Display

### Existence of local task plugin

```php
  /**
   * Tests local task existence.
   *
   * @dataProvider getAggregatorAdminRoutes
   */
  public function testAggregatorAdminLocalTasks($route) {
    $this->assertLocalTasks($route, [
      0 => ['aggregator.admin_overview', 'aggregator.admin_settings'],
    ]);
  }
```

> See also: [assertLocalTasks](/methods/assertlocaltasks.md)

### Data provider

```php
  /**
   * Provides a list of routes to test.
   */
  public function getAggregatorAdminRoutes() {
    return [
      ['aggregator.admin_overview'],
      ['aggregator.admin_settings'],
    ];
  }
```

## Summary

```
<?php
```

```php
namespace Drupal\Tests\[module_name]\Unit\Menu;

use Drupal\Tests\Core\Menu\LocalTaskIntegrationTestBase;

/**
 * Tests existence of aggregator local tasks.
 *
 * @group aggregator
 */
class AggregatorLocalTasksTest extends LocalTaskIntegrationTestBase {

  /**
   * {@inheritdoc}
   */
  protected function setUp() {
    $this->directoryList = ['module_name' => 'path/to/module'];
    parent::setUp();
  }

  /**
   * Tests local task existence.
   *
   * @dataProvider getAggregatorAdminRoutes
   */
  public function testAggregatorAdminLocalTasks($route) {
    $this->assertLocalTasks($route, [
      0 => ['aggregator.admin_overview', 'aggregator.admin_settings'],
    ]);
  }

  /**
   * Provides a list of routes to test.
   */
  public function getAggregatorAdminRoutes() {
    return [
      ['aggregator.admin_overview'],
      ['aggregator.admin_settings'],
    ];
  }

}
```

## Reference:
1. [AggregatorLocalTasksTest](https://api.drupal.org/api/drupal/core%21modules%21aggregator%21tests%21src%21Unit%21Menu%21AggregatorLocalTasksTest.php/8.5.x)
2. [LocalTaskIntegrationTestBase](https://api.drupal.org/api/drupal/core%21tests%21Drupal%21Tests%21Core%21Menu%21LocalTaskIntegrationTestBase.php/8.5.x)



