# JavaScript

---

## Client side behaviour

### Demo:
![Block filter behaviour](http://g.recordit.co/dqdIy8qlca.gif)


### Click
```php
    // Find the block filter field on the add-block dialog.
    $page->find('css', '#edit-blocks-region-header-title')->click();
    $filter = $assertSession->waitForElement('css', '.block-filter-text');

```

### Fill field

#### Multiple result rows
```php
// Test block filter reduces the number of visible rows.
$filter->setValue('ad');

$session->wait(10000, 'jQuery("#drupal-live-announce").html().indexOf("blocks are available") > -1');
$visible_rows = $this->filterVisibleElements($block_rows);

if (count($block_rows) > 0) {
  $this->assertNotEquals(count($block_rows), count($visible_rows));
}

// Test Drupal.announce() message when multiple matches are expected.
$expected_message = count($visible_rows) . ' blocks are available in the modified list.';
$assertSession->elementTextContains('css', '#drupal-live-announce', $expected_message);
```
#### One result row
```php
// Test Drupal.announce() message when only one match is expected.
$filter->setValue('Powered by');

$session->wait(10000, 'jQuery("#drupal-live-announce").html().indexOf("block is available") > -1');
$visible_rows = $this->filterVisibleElements($block_rows);

$this->assertEquals(1, count($visible_rows));

$expected_message = '1 block is available in the modified list.';
$assertSession->elementTextContains('css', '#drupal-live-announce', $expected_message);
```

#### No rows
```php
// Test Drupal.announce() message when no matches are expected.
$filter->setValue('Pan-Galactic Gargle Blaster');

$session->wait(10000, 'jQuery("#drupal-live-announce").html().indexOf("0 blocks are available") > -1');
$visible_rows = $this->filterVisibleElements($block_rows);

$this->assertEquals(0, count($visible_rows));

$expected_message = '0 blocks are available in the modified list.';
$assertSession->elementTextContains('css', '#drupal-live-announce', $expected_message);
```