## Plugin

---
Best way to functional test any plugin is to create a test module that implements the plugin. This would provide flexibility as well as full coverage of plugin handlers, forms and access.

## Base class
[PluginTestBase](https://github.com/drupal/drupal/blob/8.5.x/core/tests/Drupal/KernelTests/Core/Plugin/PluginTestBase.php) provides additional APIs on top of [KernelTestBase](https://github.com/drupal/drupal/blob/8.5.x/core/tests/Drupal/KernelTests/KernelTestBase.php). For example, [TestPluginManager](https://github.com/drupal/drupal/blob/8.5.x/core/modules/system/tests/modules/plugin_test/src/Plugin/TestPluginManager.php).


## Reference
1. [block_test](https://github.com/drupal/drupal/blob/8.5.x/core/modules/block/tests/modules/block_test) module
2. [media_test_source](https://github.com/drupal/drupal/blob/8.5.x/core/modules/media/tests/modules/media_test_source) module
3. [aggregator_test](https://github.com/drupal/drupal/blob/8.5.x/core/modules/aggregator/tests/modules/aggregator_test) module

