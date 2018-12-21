## Overview

A highly efficient, predictive and unit tested WordPress object cache backend that implements all available methods using the Redis PECL library.

# Why is this fork better?

- Preloads known cache keys via a single `mget()` call with lazy unserialization
- Further microoptimized routines makes this the **fastest** Redis object cache implementation out there
- Unit-tested with 100% effective target coverage

For more information check out https://pressjitsu.com/blog/redis-object-cache-wordpress/

## Authors

* Pressjitsu, Inc.
* Eric Mann
* Erick Hitter

## Installation
1. Install and configure Redis. There is a good tutorial [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-redis-on-debian-9).
2. Install the [Redis PECL module](http://pecl.php.net/package/redis) or compile from [source](https://github.com/phpredis/phpredis).
3. Add `object-cache.php` to the wp-content directory. It is a drop-in file, not a plugin, so it belongs in the wp-content directory, not the plugins directory.
4. By default, the script will connect to Redis at 127.0.0.1:6379. See the *Connecting to Redis* section for further options.

### Connecting to Redis ###

By default, the plugin uses `127.0.0.1` and `6379` as the default host and port when creating a new client instance; the default database of `0` is also used. Three constants are provided to override these default values.

Specify `WP_REDIS_BACKEND_HOST`, `WP_REDIS_BACKEND_PORT`, and `WP_REDIS_BACKEND_DB` to set the necessary, non-default connection values for your Redis instance.

### Prefixing Cache Keys ###

The constant `WP_CACHE_KEY_SALT` is provided to add a prefix to all cache keys used by the plugin. If running two single instances of WordPress from the same Redis instance, this constant could be used to avoid overlap in cache keys. Note that special handling is not needed for WordPress Multisite.

## Support

Support for this plugin can be had over at support@pressjitsu.com
