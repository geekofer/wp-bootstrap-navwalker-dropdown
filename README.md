# wp-bootstrap-navwalker-dropdown
This is a version of navwalker dropdown multilevel menu.

#Installation

Place wp_bootstrap_navwalker.php in your WordPress theme folder /wp-content/your-theme/

Open your WordPress themes functions.php file /wp-content/your-theme/functions.php and add the following code:
```
// Custom Navigation Walker
require_once('wp_bootstrap_navwalker.php');
```
#Usage

Update your wp_nav_menu() function in header.php to use the new walker by adding a "walker" item to the wp_nav_menu array.
```php
<?php
// Menu Location
wp_nav_menu( array(
	'menu'              => 'Main Menu',
	'theme_location'    => 'main_menu',
	'depth'             => 3,
	'container'         => 'div',
	'container_class'   => 'collapse navbar-collapse',
	'container_id'      => 'bs-example-navbar-collapse-1',
	'menu_class'        => 'nav navbar-nav',
	'fallback_cb'       => 'wp_bootstrap_navwalker::fallback',
	'walker'            => new wp_bootstrap_navwalker())
 );
?>
```
Add custom ccs for levels on hover dropdown options

```css
/*Dropdown Css*/
.dropdown:hover > .dropdown-menu {
  display: block;
}
.dropdown-submenu {
    position: relative;
}
.dropdown-submenu>.dropdown-menu {
    top: 0;
    left: 100%;
    margin-top: -6px;
    margin-left: -1px;
    -webkit-border-radius: 0 6px 6px 6px;
    -moz-border-radius: 0 6px 6px;
    border-radius: 0 6px 6px 6px;
}
.dropdown-submenu:hover > .dropdown-menu {
    display: block;
}
.dropdown-submenu>a:after {
    display: block;
    content: " ";
    float: right;
    width: 0;
    height: 0;
    border-color: transparent;
    border-style: solid;
    border-width: 5px 0 5px 5px;
    border-left-color: #ccc;
    margin-top: 5px;
    margin-right: -10px;
}
.dropdown-submenu:hover>a:after {
    border-left-color: #fff;
}
.dropdown-submenu.pull-left {
    float: none;
}
.dropdown-submenu.pull-left>.dropdown-menu {
    left: -100%;
    margin-left: 10px;
    -webkit-border-radius: 6px 0 6px 6px;
    -moz-border-radius: 6px 0 6px 6px;
    border-radius: 6px 0 6px 6px;
}
/*./Dropdown Css*/
```
Add custom Jquery script for click on the first item in the dropdown menu

```javascript

jQuery(function($) {
  // Bootstrap menu magic
  $(window).resize(function() {
    if ($(window).width() < 768) {
      $(".dropdown-toggle").attr('data-toggle', 'dropdown');
    } else {
      $(".dropdown-toggle").removeAttr('data-toggle dropdown');
    }
  });
});
```