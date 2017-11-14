# Functional

---


## 1. Setup

{% gist id="drupadocs-user/5932b56120d8c0e8b816e5c8571888e1" %} {% endgist %}

## 2. UI Tests

### 2.1 Link 

```php
// Checks for link by href path.
$this->assertSession()->linkByHrefExists('/admin/config');

// Checks no link with href path.
$this->assertSession()->linkByHrefNotExists('/admin/config');
```

## 3. Reference

1. [ContentModerationWorkflowTypeTest](https://github.com/drupal/drupal/blob/8.5.x/core/modules/content_moderation/tests/src/Functional/ContentModerationWorkflowTypeTest.php)
2. [MediaAccessTest](https://github.com/drupal/drupal/blob/8.5.x/core/modules/media/tests/src/Functional/MediaAccessTest.php)


