# WP Maintenance Mode

Adds a splash page to your site that lets visitors know your site is down for maintenance. It's perfect for a coming soon page.

## Description
Add a maintenance page to your blog that lets visitors know your blog is down for maintenance, or add a coming soon page for a new website. User with admin rights gets full access to the blog including the front end.

Activate the plugin and your blog is in maintenance-mode, works and only registered users with enough rights can see the front end. You can use a date with a countdown timer for visitor information or set a value and unit for information. 
Also works with WordPress Multisite installs (each blog from the network has it's own maintenance settings).

**Features**

* Fully customizable (change colors, texts and backgrounds);
* Subscription form (export emails to .csv file);
* Countdown timer (remaining time);
* Contact form (receive emails from visitors);
* Coming soon page;
* Landing page templates;
* WordPress multisite;
* Responsive design;
* Social media icons;
* Works with any WordPress theme;
* SEO options;
* Exclude URLs from maintenance.

## F.A.Q.

**How to use plugin filters**

1. `wpmm_backtime` - can be used to change the backtime from page `Retry-After` header

```php
function new_backtime() {
    return 1800;
}

add_filter('wpmm_backtime', 'new_backtime');
```

Now... the search bots will retry to visit the page after 1800 seconds.

2. `wpmm_search_bots` - if you have `Bypass for Search Bots` option (from General) activated, it can be used to add new bots (useragents)

```php
function new_search_bots($bots) {
    // we delete a bot from array
    if(!empty($bots['AcoiRobot'])){ 
        unset($bots['AcoiRobot']);
    }

    // we add a new bot into array
    if(empty($bots['new_robot'])){ 
        $bots['new_robot'] = 'NewRobot'; // NewRobot is the user agent
    }

    return $bots;
}

add_filter('wpmm_search_bots', 'new_search_bots');
```

We deleted a bot from list and added a new one.

3. `wpmm_text` - can be used to change `Text` option

```php
function new_text($text) {
    $text = str_replace('http://www.designmodo.com', 'http://designmodo.com', $text);
    

    return $text;
}

add_filter('wpmm_text', 'new_text');
```

We replaced a string with another string. We can also add another text, add some extra html, etc.

4. `wpmm_styles` - can be used to embed new css files

```php
function new_css_styles($styles) {
    $styles['new-style'] = 'path_to_css_file/style.css'; // replace with the real path :)

    return $styles;
}

add_filter('wpmm_styles', 'new_css_styles');
```

We embedded a new css style on maintenance page. Same mechanism can be used for javascript files (see `wpmm_scripts` filter).

**Cache Plugin Support**

The plugin flush the cache on activate the maintenance mode form the plugins W3 Total Cache and WP Super Cache

## Other Notes
### License
Good news, this plugin is free for everyone! Since it's released under the GPL, you can use it free of charge on your personal or commercial blog.

### Translations
The plugin comes with various translations, please refer to the [WordPress Codex](http://codex.wordpress.org/Installing_WordPress_in_Your_Language "Installing WordPress in Your Language") for more information about activating the translation. If you want to help to translate the plugin to your language, please have a look at the .pot file which contains all defintions and may be used with a [gettext](http://www.gnu.org/software/gettext/) editor like [Poedit](http://www.poedit.net/) (Linux, Mac OS X, Windows).

### Contact & Feedback
Please let me know if you like the plugin or you hate it or whatever... Please fork it, add an issue for ideas and bugs.
