# Functional

---


## 1. Setup

{% gist id="drupadocs-user/5932b56120d8c0e8b816e5c8571888e1" %} {% endgist %}

## 2. UI Tests

### 2.1 Link 

```php
// Checks link with label 'Add workflow'
$this->assertSession()->linkExists('Add workflow');

// Checks link with exact label 'Add workflow'
$this->assertSession()->linkExistsExact('Add workflow');

// Checks no link with label 'Add workflow'
$this->assertSession()->linkNotExists('Add workflow');

// Checks no link with exact label 'Add workflow'
$this->assertSession()->linkNotExistsExact('Add workflow');

```

## 3. Reference

1. [WorkflowUiNoTypeTest](https://github.com/drupal/drupal/blob/8.5.x/core/modules/workflows/tests/src/Functional/WorkflowUiNoTypeTest.php)
2. [VocabularyPermissionsTest](https://github.com/drupal/drupal/blob/8.5.x/core/modules/taxonomy/tests/src/Functional/VocabularyPermissionsTest.php)
