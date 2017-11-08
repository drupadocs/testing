# Functional

---

## Setup

```php
/**
 * Tests aggregator admin pages.
 *
 * @group [module_machine_name]
 */
class ModuleNameAdminUiTest extends BrowserTestBase {

  /**
   * Modules to install.
   *
   * @var array
   */
  public static $modules = ['block', 'node', 'aggregator'];

  /**
   * {@inheritdoc}
   */
  protected function setUp() {
    parent::setUp();
    $this->drupalCreateContentType(['type' => 'article', 'name' => 'Article']);

    $permissions = [
      'access administration pages',
      'administer news feeds',
      'access news feeds',
      'create article content',
     ];
    $this->adminUser = $this->drupalCreateUser($permissions);
    $this->drupalLogin($this->adminUser);

  }

}
```

### Display

#### Display of text,  field & button

```php
  /**
   * Tests the settings form to ensure the correct default values are used.
   */
  public function testSettingsPage() {
    // Visit a page
    $this->drupalGet('admin/config');

    // Click a link on a page.
    $this->clickLink('Aggregator');
    $this->clickLink('Settings');

    // Check for text.
    $this->assertSession()->pageTextContains('Test fetcher');
    $this->assertSession()->pageTextContains('Test parser');
    $this->assertSession()->pageTextContains('Test processor');

    // Check for a field by id|name|label
    $this->assertSession()->fieldExists('aggregator_allowed_html_tags')

    // Check for a button by id|name|label|value
    $this->assertSession()->buttonExists('Submit')

  }
```

## Behavior

### Validation

```php
   // Try to submit with invalid value.
    $edit = [
      'total_count' => 'invalid string',
    ];
    $this->drupalPostForm('admin/config/services/aggregator/settings', $edit, t('Save configuration'));

    // Check for error message.
    $this->assertSession()->pageTextContains('Total count should be an integer.');
```

### Submit

```php
    // Set new values and enable test plugins.
    $edit = [
      'aggregator_allowed_html_tags' => '<a>',
      'aggregator_summary_items' => 10,
      'aggregator_clear' => 3600,
      'aggregator_teaser_length' => 200,
      'aggregator_fetcher' => 'aggregator_test_fetcher',
      'aggregator_parser' => 'aggregator_test_parser',
      'aggregator_processors[aggregator_test_processor]' => 'aggregator_test_processor',
    ];
    $this->drupalPostForm('admin/config/services/aggregator/settings', $edit, t('Save configuration'));
    $this->assertText(t('The configuration options have been saved.'));
```

## Summary

```php
<?php

namespace Drupal\Tests\[module_name]\Functional

use Drupal\Tests\BrowserTestBase;

/**
 * Tests [Module Name] admin pages.
 *
 * @group [module_name]
 */
class [ModuleName]AdminUiTest extends BrowserTestBase {

  /**
   * Modules to install.
   *
   * @var array
   */
  public static $modules = ['block', 'node', 'aggregator', '[module_name]'];

  /**
   * {@inheritdoc}
   */
  protected function setUp() {
    parent::setUp();
    $this->drupalCreateContentType(['type' => 'article', 'name' => 'Article']);

    $permissions = [
      'access administration pages',
      'administer news feeds',
      'access news feeds',
      'create article content',
    ];
    $this->adminUser = $this->drupalCreateUser($permissions);
    $this->drupalLogin($this->adminUser);
  }

  /**
   * Tests the settings form to ensure the correct default values are used.
   */
  public function testSettingsPage() {
    // Visit a page
    $this->drupalGet('admin/config');
    // Click a link on a page.
    $this->clickLink('Aggregator');
    $this->clickLink('Settings');
    // Check for text.
    $this->assertSession()->pageTextContains('Test fetcher');
    $this->assertSession()->pageTextContains('Test parser');
    $this->assertSession()->pageTextContains('Test processor');
    // Check for a field by id|name|label
    $this->assertSession()->fieldExists('aggregator_allowed_html_tags');
    // Check for a button by id|name|label|value
    $this->assertSession()->buttonExists('Submit');
    // Try to submit with invalid value.
    $edit = [
      'total_count' => 'invalid string',
    ];
    $this->drupalPostForm('admin/config/services/aggregator/settings', $edit, t('Save configuration'));
    // Check for error message.
    $this->assertSession()->pageTextContains('Total count should be an integer.');

    // Set new values and enable test plugins.
    $edit = [
      'aggregator_allowed_html_tags' => '<a>',
      'aggregator_summary_items' => 10,
      'aggregator_clear' => 3600,
      'aggregator_teaser_length' => 200,
      'aggregator_fetcher' => 'aggregator_test_fetcher',
      'aggregator_parser' => 'aggregator_test_parser',
      'aggregator_processors[aggregator_test_processor]' => 'aggregator_test_processor',
    ];
    $this->drupalPostForm('admin/config/services/aggregator/settings', $edit, t('Save configuration'));
    $this->assertText(t('The configuration options have been saved.'));
  }

}
```



