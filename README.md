=== Post Expiration Unposter ===
Contributors: AlecWilcoxMedia
Tags: expiration, cron, schedule, unpublish, post
Requires at least: 4.0
Tested up to: 6.8
Stable tag: 0.3
License: GPLv2 or later
License URI: https://www.gnu.org/licenses/gpl-2.0.html

Automatically unpublish WordPress posts when they reach a set expiration date.

== Description ==

Post Expiration Unposter lets you choose an expiration date for any post. On that date (and beyond), the plugin will automatically switch the post’s status from **Publish** to **Draft**, effectively “unpublishing” it.

- **Easy set‑and‑forget**: Choose a date and forget—your post will unpublish itself.  
- **Lightweight**: Uses WordPress’s built‑in cron to run a daily check.  
- **Internationalized**: All admin strings use the `post-expiration-unposter` text domain.

## Installation

1. Upload the `post-expiration-unposter` folder to the `/wp-content/plugins/` directory.  
2. Activate the plugin through the **Plugins** screen in WordPress.  
3. Edit any post, and in the **Expiration Date** meta box (in the sidebar), pick your date.  
4. Save or update the post—on the chosen date, it’ll be moved to Draft.

## Usage

### Setting an Expiration Date

1. Open the post you want to expire.  
2. In the **Expiration Date** box (right sidebar), select the date.  
3. Click **Update** or **Publish**.  

After midnight on that date (your site’s timezone), the post status will change to **Draft** automatically.

### WP‑Cron Behavior

- **Activation**: Schedules a daily event (`peu_daily_event`) to run at the next available hourly interval.  
- **Deactivation**: Clears the scheduled event so no daily check will run.  
- **Daily Check**: Queries all published posts with a `_peu_expiration_date` meta value ≤ today’s date, and updates them to draft.

## Hooks & Filters

- **Action** `peu_daily_event`  
  Runs the expiration check.  
- **Activation hook** `peu_activate`  
  Sets up the daily cron.  
- **Deactivation hook** `peu_deactivate`  
  Clears the cron.  
- **Meta box** added via `add_meta_box('peu_meta_box', …)` on post edit screens.  
- **Save hook** `save_post` with `peu_save_meta_box_data()` to persist or delete the `_peu_expiration_date` meta.

## Changelog

### 0.2
- Initial public release:  
  - Daily WP‑Cron scheduling  
  - Expiration date meta box and saving  
  - Automatic unpublish on expiration

## Upgrade Notice

### 0.2
First release—no upgrade path needed.

## License

This plugin is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License version 2 or later.

