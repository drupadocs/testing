
# assertLocalTask()
---

Checks for different components of local tasks.

{% method %}
## Definition


{% common %}
Whatever language you are using, the result will be the same.


```php5
  /**
   * Asserts that local tasks exists.
   */
  public function assertLocalTasks() {
    $this->assertSession()->linkExists('Settings');
    $this->assertSession()->linkExists('Manage fields');
    $this->assertSession()->linkExists('Manage display');
    $this->assertSession()->linkExists('Manage form display');
  }
```
{% endmethod %}
