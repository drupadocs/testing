# Functional

---


## 1. Setup

{% gist id="drupadocs-user/5932b56120d8c0e8b816e5c8571888e1" %} {% endgist %}

## 2. UI Tests

### 2.1 Text 

```php
// Checks for text "Test fetcher" is on current page.
$this->assertSession()->pageTextContains('Test fetcher');

// Checks for text "Test fetcher" is NOT on current page.
$this->assertSession()->pageTextNotContains('Test fetcher');

// Checks for regular expression pattern match.
$this->assertSession()->pageTextMatches('/[0-9]{10}/');

// 
$this->assertSession()->pageTextNotMatches('/[0-9]{5}/');
```
### 2.2 HTML
```php
// Check HTML content.
$this->assertSession()->responseContains();
```

#### 2.2 Field 
```php
// Check for a field by id or name or label
$this->assertSession()->fieldExists('aggregator_allowed_html_tags')
```


### 2.3 Button
```php
// Check for a button by id or name or label
$this->assertSession()->buttonExists('Submit')
```
### 2.4 Summary

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

    // Check for a field by id or name or label
    $this->assertSession()->fieldExists('aggregator_allowed_html_tags')

    // Check for a button by id or name or label
    $this->assertSession()->buttonExists('Submit')
  }
```

## 3. Behavior Tests

### 3.1 Validation

```php
   // Try to submit with invalid value.
    $edit = [
      'total_count' => 'invalid string',
    ];
    $this->drupalPostForm('admin/config/services/aggregator/settings', $edit, t('Save configuration'));

    // Check for error message.
    $this->assertSession()->pageTextContains('Total count should be an integer.');
```

### 3.2 Submit

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
    $this->drupalPostForm('admin/config/services/aggregator/settings', $edit, 'Save configuration');
    $this->assertText('The configuration options have been saved.');
```
> Note:
1. It is a good idea to make sure new values are saved after submit by asserting like in display section above.

## 4. Reference:
1. [AggregatorAdminTest](https://github.com/drupal/drupal/blob/8.5.x/core/modules/aggregator/tests/src/Functional/AggregatorAdminTest.php)
2. [ResponsiveImageAdminUITest](https://github.com/drupal/drupal/blob/8.5.x/core/modules/responsive_image/src/Tests/ResponsiveImageAdminUITest.php)


