# Change Log
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/).

## [Unreleased]

## [0.9.2](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.9.2) - 2024-04-30
### Changed
* Add a new regex rule for XMLRPC authentication failure to both filters (soft and hard)

## [0.9.0](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.9.0) - 2023-10-17
### Changed
* Bumps "Tested up to" version to 6.4
* Bumps minimum required PHP version to 7.0
* Bumps minimum required WP version to 5.5
* Update dependency package versions
* No changes to jail or filters in the release.

## [0.8.2](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.8.2) - 2021-08-08
### Changed
* Bumps "Tested up to" version to 5.8
* No changes to jail or filters in the release.

## [0.8.1](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.8.1) - 2021-06-01
### Changed
* Actually bumps "Tested up to" version to 5.7

## [0.8.0](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.8.0) - 2021-05-31
### Changed
* Bumps "Tested up to" version to 5.7

### Fixed
* Fix issue where logging out of WordPress could cause a blocked user log to be recorded

## [0.7.0](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.7.0) - 2021-01-05
### Changed
* Bumps "Tested up to" version to 5.6
* Move Composer dependencies to `require-dev` to reduce the number of packages installed when WP Fail2Ban Redux is installed via composer. See https://github.com/thebrandonallen/wp-fail2ban-redux/pull/17

## [0.6.0](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.6.0) - 2020-06-07
### Changed
* Bumps the minimum required version to WordPress 4.9.
* Bumps "Tested up to" version to 5.4.1

## [0.5.1](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.5.1) - 2019-09-05
### Fixed
* Fix issue where XML-RPC multicall authentication failures weren't correctly matched by Fail2Ban with the `wordpress-hard.conf` filter. [GH-12]

## [0.5.0](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.5.0) - 2018-10-27
### Added
* Add better support for use as a must-use plugin in the `mu-plugins` directory.

### Changed
* Moved all files/folders into a new directory `wp-fail2ban-redux/wp-fail2ban-redux`.

## [0.4.0](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.4.0) - 2018-01-15
### Added
* New filter, `wp_fail2ban_redux_openlog_ident`, because it's `ident` not `indent`.

### Changed
* Bumped the minimum required WordPress version to 4.5.
* Bumped the minimum required PHP version to 5.3. This is a soft bump, meaning, nothing changed that will break PHP 5.2 compatability. However, this could easily change in the future, and PHP 5.2 is no longer actively tested.

### Deprecated
* Deprecated the `wp_fail2ban_redux_openlog_indent` filter.

## [0.3.1](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.3.1) - 2017-05-18
### Added
* Introduce `WP_Fail2Ban_Redux_Logger` as the new logger class.
* Introduce `WP_Fail2Ban_Redux_Logger_Interface` as the new logger base class.

### Changed
* `WP_Fail2Ban_Redux::__construct()` is now public.
* Check if we're blocking user enumeration earlier. Should bring performance improvements.
* Bump minimum required WordPress version to 4.4.
* Refactored plugin loading.
* Use `wp_die` to exit, to allow for greater customization of exit messages. Exit messages are now escaped using `esc_html`.

### Deprecated
* Deprecated all `WP_Fail2Ban_Redux_Log` methods.

### Fixed
* Fix potential PHP errors during pingback logging.

## [0.3.0](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.3.0) - 2017-05-18 [YANKED]
* Superseded by 0.3.1.

## [0.2.1](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.2.1) - 2017-02-15

### Fixed
* Fix a stupid syntax error in the comment spam filter :( Thanks to [ichtarzan](https://profiles.wordpress.org/ichtarzan) for reporting!

## [0.2.0](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.2.0) - 2016-09-27
### Added
* Added a note to `wordpress.conf` about the `logpath` parameter, and common auth log locations. *There is no need to changed existing configurations.* This is merely to aid setup for future users.
* Introduced `WP_Fail2Ban_Redux::user_enumeration` to handle user enumeration at a better time than redirect canonical

### Changed
* User enumeration blocking now checks for both the `author` and `author_name` parameters. The `author_name` parameter could be used to validate the existence of a particular username, so blocking on this parameter as well will further reduce the attack surface.

### Deprecated
* `WP_Fail2Ban_Redux::redirect_canonical` is now deprecated. If you were doing anything with this function, or the hook that initialized it, you should look at `WP_Fail2Ban_Redux::user_enumeration` instead.

### Fixed
* Fixed PHP notices where `WP_Fail2Ban_Redux::comment_spam` expects two parameters. Decided it was probably a good idea to oblige.
* Fixes an issue where user enumeration blocking was overzealous and would prevent actions in the admin area. Props @pjv. [GH-2]

## [0.1.1](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.1.1) - 2016-07-23
### Added
* Add `WP_Fail2Ban_Redux::get_instance()` to make it easier to remove actions added.

### Fixed
* In PHP < 7.0, `exit` isn't allowed as a method name. `WP_Fail2Ban_Redux_Log::exit` is now `WP_Fail2Ban_Redux_Log::_exit`.

## [0.1.0](https://github.com/thebrandonallen/wp-fail2ban-redux/tree/0.1.0) - 2016-07-13
* Initial release.

[Unreleased]: https://github.com/thebrandonallen/wp-fail2ban-redux/compare/0.6.0...develop
[0.6.0]: https://github.com/thebrandonallen/wp-fail2ban-redux/compare/0.5.1...0.6.0
[0.5.1]: https://github.com/thebrandonallen/wp-fail2ban-redux/compare/0.5.0...0.5.1
[0.5.0]: https://github.com/thebrandonallen/wp-fail2ban-redux/compare/0.4.0...0.5.0
[0.4.0]: https://github.com/thebrandonallen/wp-fail2ban-redux/compare/0.3.1...0.4.0
[0.3.1]: https://github.com/thebrandonallen/wp-fail2ban-redux/compare/0.3.0...0.3.1
[0.3.0]: https://github.com/thebrandonallen/wp-fail2ban-redux/compare/0.2.1...0.3.0
[0.2.1]: https://github.com/thebrandonallen/wp-fail2ban-redux/compare/0.2.0...0.2.1
[0.2.0]: https://github.com/thebrandonallen/wp-fail2ban-redux/compare/0.1.1...0.2.0
[0.1.1]: https://github.com/thebrandonallen/wp-fail2ban-redux/compare/0.1.0...0.1.1
