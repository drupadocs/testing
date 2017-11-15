# Kernel
---


## Assert tags

```php

 /**
   * Tests the cache tags from image formatters.
   */
  public function testImageFormatterCacheTags() {
    
    // Create a test entity with the image field set.
    $entity = EntityTest::create([
      'name' => $this->randomMachineName(),
    ]);
    $entity->{$this->fieldName}->generateSampleItems(2);
    $entity->save();
    
    // Generate the render array to verify if the cache tags are as expected.
    $build = $this->display->build($entity);
    $this->assertEquals($entity->{$this->fieldName}[0]->entity->getCacheTags(), $build[$this->fieldName][0]['#cache']['tags'], 'First image cache tags is as expected');
    $this->assertEquals($entity->{$this->fieldName}[1]->entity->getCacheTags(), $build[$this->fieldName][1]['#cache']['tags'], 'Second image cache tags is as expected');
  }
  
```

>Note: See also [assertcachetags](/methods/assertcachetags.md) method.

## Reference
1. [ImageFormatterTest](https://github.com/drupal/drupal/blob/8.5.x/core/modules/image/tests/src/Kernel/ImageFormatterTest.php)