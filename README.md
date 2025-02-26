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

### 1.5
- Bug fixes
  - Fixed a critical error in the flush_meta_cache() method when the function was called with an array of parameters instead of individual arguments
  - Added correct object handling in flush_post_cache(), flush_term_cache(), flush_comment_cache() and flush_user_cache() methods
  - Fixed _key() method - added check for empty or null key values
  - Improved error handling in cleanup_old_entries() method using error suppression for APCu functions


- Improvements
  - Optimized setup_scheduled_cleanup() method to prevent duplicate hooks
  - Added type checks to cache handling methods to prevent errors
  - Enhanced existence checks for WordPress functions before calling them
  - Improved metadata handling for different content types

- Security
  - Added additional checks for type and existence of parameters before processing

### 1.4.1

- TTL Handling Improvements
  - Unified default TTL logic in `_set()` method to use `WP_APCU_DEFAULT_TTL`
  - Added validation and default TTL assignment in `_add()` method

### 1.4

- Default TTL Configuration
  - Set default TTL for all methods (6 hours, 21600 seconds)
  - Added configurable constant `WP_APCU_DEFAULT_TTL`

- Version Counter Reset
  - Reset version counter to 1 when exceeding 100
  - Implemented cleanup of outdated entries for specific groups/sites

- Periodic Cache Cleanup
  - Added `cleanup_old_entries()` method
  - Configured WordPress cron for hourly execution
  - Automatic cleanup when memory usage exceeds 80%

- Smart Invalidation
  - Added hooks for all WordPress data types

### 1.3
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
