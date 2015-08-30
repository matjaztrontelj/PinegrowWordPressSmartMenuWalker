# PinegrowWordPressSmartMenuWalker
Easily adjust the layout of WordPress navigation menus with this menu walker class.

## Instructions

### 1. Include wp_smart_navwalker.php into functions.php of your theme

For example, add this at the end of functions.php:

```
require_once "wp_smart_navwalker.php";
```

### 2. Output the menu in your theme

For example:

```
<?php 
    PG_Smart_Walker_Nav_Menu::$options['template'] = '<li class="{CLASSES}" id="{ID}"><a {ATTRS}>{TITLE}</a></li>';
    PG_Smart_Walker_Nav_Menu::$options['current_class'] = 'active';
    wp_nav_menu( array(
        'container' => '',
        'items_wrap' => '<ul class="right %2$s" id="%1$s">%3$s</ul>',
        'walker' => new PG_Smart_Walker_Nav_Menu()
    ) ); ?>
```
Tell the walker which layout to use for menu items by assigning the template to PG_Smart_Walker_Nav_Menu::$options['template'] before calling wp_nav_menu.

Assign the current class to PG_Smart_Walker_Nav_Menu::$options['current_class'].

The menu item template can contain the following tokens:

* {CLASSES} - replaced by WP classes of the menu item
* {ID} - replaced by WP menu item id
* {ATTRS} - replaced by WP link attributes like href, target, ref and title
* {TITLE} - replaced by the menu item title
* {SUB} - optional, tells the walker where to put sub-menu items, default is before the last closing tag of the template

## Build WP themes faster with Pinegrow Web Editor

[Pinegrow](http://pinegrow.com/wordpress-theme-builder.html) is a visual HTML and CSS editor for Mac, Windows and Linux. It also included a WordPress theme builder that includes this smart menu walker. To use it in Pinegrow, just assign the Navigation menu action to the HTML menu element and set the menu type to Smart. Pinegrow will auto-detect the menu item template and items wrap layout and automatically add and setup the menu walker to your theme. [Read more about making navigation menus with Pinegrow](http://docsbeta.pinegrow.com/wordpress-themes/navigation-menus).

## License

[GPL 2.0](http://www.gnu.org/licenses/gpl-2.0.txt)
