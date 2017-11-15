# assertCacheTags
---

Checks cache tags.

{% method %}
## Definition
Checks for all tags of given page.

{% common %}

```php
  /**
   * Asserts that a renderable array has a set of cache tags.
   *
   * @param array $renderable
   *   The renderable array. Must have a #cache[tags] element.
   * @param array $cache_tags
   *   The expected cache tags.
   */
  protected function assertCacheTags(array $renderable, array $cache_tags) {
    $diff = array_diff($cache_tags, $renderable['#cache']['tags']);
    $this->assertEmpty($diff);
  }
  
```

{% endmethod %}
