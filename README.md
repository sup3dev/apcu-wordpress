# Improved APCu Object Cache Backend

This plugin enhances the original APCu Object Cache Backend by adding **intelligent cache invalidation** and improved **resource management**. It aims to provide faster cache handling while reducing unnecessary operations.

## Key Features

### Intelligent Cache Invalidation
- **Automatic Cache Clearing**: The cache is cleared automatically when WordPress content changes, ensuring up-to-date cached data.
- **Spot Invalidation**: Instead of clearing the entire cache, only modified items are invalidated.
- **Data-Specific Handlers**: Cache invalidation is managed separately for different data types (posts, terms, metadata, comments, etc.), optimizing resource usage.

### Improved Resource Management
- **Selective Cleanup**: Only modified objects are removed from the cache, leaving untouched objects for better performance.
- **Reduced Database Access**: Fewer queries are required after content updates due to more efficient cache handling.

## Known Issues

- **TTL Problem**: Records with `TTL=0` remain in memory indefinitely, which can lead to stale cache entries.
- **Cache Versioning**: While cache versions are created when data changes, old versions are not automatically removed, leading to potential memory bloat.

## Installation

1. Ensure you have PHP 7.2+ and a compatible APCu version installed.
2. Download and place `object-cache.php` in your WordPress `wp-content/` directory.
3. That's it!

## Composer Installation (Old Version)
If you'd like to use the **old version** with Composer, you can still install it via the [l3rady repository](https://github.com/l3rady/object-cache-apcu) using the following command:

```bash
composer require l3rady/object-cache-apcu
```
Please note that this version is not up-to-date with the latest improvements.

Contributing
Feel free to open an issue or submit a pull request if you have suggestions or find bugs. Contributions are always welcome!

## Changelog
### 1.2
- Enhanced cache invalidation logic and resource management:
  - Added intelligent cache invalidation: automatic clearing of cache on content changes, spot invalidation instead of full cleanup.
  - Introduced separate handlers for different data types (posts, terms, metadata, comments, etc.) to improve performance.
- Improved resource usage by selectively cleaning up only modified objects, reducing unnecessary database accesses.

### 1.2
(in the repository https://github.com/l3rady/object-cache-apcu):
- Add composer file and add dropin plugin to packagist.org for easy installation via composer.
- Add latest cache methods added to core recentlys

### 1.1
- Added local array cache to minimize APCu calls during repeated requests (thanks to rob006).
- Introduced WP_APCU_LOCAL_CACHE to disable local cache in specific cases.

### 1.0
- Initial release, based on the APC Object Cache Backend.

This plugin is an improved version of the original APCu Object Cache Backend with better cache invalidation and resource management.
Based on https://wordpress.org/plugins/apc/
