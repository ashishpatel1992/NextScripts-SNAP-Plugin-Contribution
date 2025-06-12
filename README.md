

# NextScripts SNAP Plugin Contribution
Source code https://plugins.trac.wordpress.org/browser/social-networks-auto-poster-facebook-twitter-g/
## Overview
This repository contains my open-source contribution to the NextScripts Social Networks Auto-Poster (SNAP) plugin for WordPress. The plugin, which automates posting to social media, has not been maintained for several years, leading to compatibility issues with modern WordPress and database systems.
Issues Addressed
I encountered multiple database-related errors with the plugin (version 4.4.6) on WordPress 6.7.0 and MariaDB 10.6.22, including:

- SQL syntax errors due to incorrect table quoting (e.g., single quotes around table names like 'wp_nxs_log' and 'wp_nxs_query').
- Missing or unrecognized id column in the wp_nxs_query table, causing errors like Unknown column 'id' in 'SELECT'.

These issues were resolved by updating the plugin's PHP code to:

- Use backticks (`) for table names in SQL queries.
- Ensure proper table schema creation for wp_nxs_log and wp_nxs_query.
- Implement error handling and email notifications for database errors using wp_mail.

## Changelog
### Version 4.4.6-patch1 (June 12, 2025)
- **Fixed SQL Syntax Errors**: Updated queries in `nxs_do_this_hourly` and `nxs_checkQuery` to use backticks (`` ` ``) instead of single quotes for table names (`wp_nxs_log`, `wp_nxs_query`), resolving MariaDB 10.6.22 compatibility issues.
- **Fixed Missing `id` Column**: Ensured `wp_nxs_query` table schema includes the `id` column, fixing `Unknown column 'id'` errors.
- **Added Email Notifications**: Implemented `nxs_send_error_email` function to send `wp_mail` notifications for database errors, using SNAP’s existing email settings.

## Contribution
This contribution is provided as a patch for the free version of the NextScripts SNAP plugin. The changes fix the SQL query issues and improve compatibility with recent WordPress and MariaDB versions. The modified code is shared to help other users facing similar problems.

## Disclaimer
This code is provided as-is and should be used at your own risk. I am not responsible for any issues, data loss, or damages that may arise from using this contribution. Always test changes on a staging site and back up your database before applying updates. Since the plugin is unmaintained, consider exploring actively supported alternatives.

## Usage

Backup: Back up your WordPress database and files.
Apply Changes: Replace the relevant plugin files (e.g., those containing nxs_do_this_hourly and nxs_checkQuery) with the updated versions from this repository.
Test: Verify functionality on a staging site.
Monitor: Enable WordPress debugging (WP_DEBUG) to catch any additional issues.

## License
This contribution is released under the same license as the original NextScripts SNAP plugin (GPLv2 or later). See the plugin's license for details.
