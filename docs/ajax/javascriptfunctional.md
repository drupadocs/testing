# JavaScript

---

## Client side behaviour


### Check modal
```php
    $this->clickLink('Normal Modal!');
    // Neither of the wide modals should have been used.
    $style = $session_assert->waitForElementVisible('css', '.ui-dialog')->getAttribute('style');

```
