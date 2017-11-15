# Functional
---


## 1. Setup

{% gist id="drupadocs-user/5932b56120d8c0e8b816e5c8571888e1" %} {% endgist %}


On top of regular setup, place your block in a region.

```php
    // Add the system branding block to the page.
    $this->drupalPlaceBlock('system_branding_block', ['region' => 'header', 'id' => 'site-branding']);

```

## 2. UI test

### 2.1. Block presence

```php
    $site_slogan_xpath = '//div[@id="block-site-branding"]//div[@class="site-slogan"]';
    $site_slogan_element = $this->xpath($site_slogan_xpath);
    $this->assertTrue(!empty($site_slogan_element), 'The branding block slogan was found.');

```
### 2.2. View block
```php
    // Place the block in a region with custom title.
    $block = $this->drupalPlaceBlock('views_block:test_view_block-block_1', ['label' => 'test_view_block-block_1:1', 'views_label' => 'Custom title']);

    // Visit the page.
    $this->drupalGet('');

    // Get block selector.    
    $result = $this->xpath('//div[contains(@class, "region-sidebar-first")]/div[contains(@class, "block-views")]/h2');

        // Check block title exists.
    $this->assertEqual($result[0]->getText(), 'Custom title');


    // Don't override the title anymore.
    $plugin = $block->getPlugin();
    $plugin->setConfigurationValue('views_label', '');
    $block->save();

    // Make sure default title.
    $this->drupalGet('');
    $result = $this->xpath('//div[contains(@class, "region-sidebar-first")]/div[contains(@class, "block-views")]/h2');
    $this->assertEqual($result[0]->getText(), 'test_view_block');

```


## 3. Behaviour test

### 3.1 XSS filter

```php
    // Be sure the slogan is XSS-filtered.
    $this->config('system.site')
      ->set('slogan', '<script>alert("Community carpentry");</script>')
      ->save();

    $this->assertEqual($site_slogan_element[0]->getText(), 'alert("Community carpentry");', 'The site slogan was XSS-filtered.');
```
### 3.2 Disable

```php
    // Turn just the site slogan off.
    $this->config('block.block.site-branding')
      ->set('settings.use_site_slogan', 0)
      ->save();
    $this->drupalGet('');
    $this->assertTrue(empty($site_slogan_element), 'The branding block slogan was disabled.');

```

## 4. Reference
1. [BlockSystemBrandingTest](https://github.com/drupal/drupal/blob/8.5.x/core/modules/block/tests/src/Functional/BlockSystemBrandingTest.php)
2. [NodeSyndicateBlockTest](https://github.com/drupal/drupal/blob/8.5.x/core/modules/node/tests/src/Functional/NodeSyndicateBlockTest.php)
3. [DisplayBlockTest](https://github.com/drupal/drupal/blob/8.5.x/core/modules/block/tests/src/Functional/Views/DisplayBlockTest.php)

