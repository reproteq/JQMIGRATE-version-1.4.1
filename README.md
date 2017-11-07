# JQMIGRATE-version-1.4.1
JQMIGRATE: Migrate is installed, version 1.4.1
wordpress error solution

copy this function in your themes/yourtheme/functions.php

 /// JQMIGRATE: Migrate is installed, version 1.4.1 error remove
  function tt_jquery_migrate( $scripts ) {
	if ( ! is_admin() && ! empty( $scripts->registered['jquery'] ) ) {
		$jquery_dependencies = $scripts->registered['jquery']->deps;
		$scripts->registered['jquery']->deps = array_diff( $jquery_dependencies, array( 'jquery-migrate' ) );
	}
}
add_action( 'wp_default_scripts', 'tt_jquery_migrate' );


copy this code in your /themes/yourtheme/header.php

	<?php do_action('yourtheme_before_header'); // search this and copy downline) ?>
   <?php  do_action ('tt_jquery_migrate'); // add this  line   in your header.php?>
