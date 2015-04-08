# force_fid_download
This is a simple Drupal 7 module which aim is to help generating a link from custom modules to ensure file is forced to be download.

It does this by creating a new menu item called _download_ to which one can pass a file id to be downloaded. When this path is reached by user, the module checks if a user can actually download the file by using file_download_access() function. If it can, module then sets HTTP header to 'Content-Disposition' and calls file_download() function.

## Installation
Install and enable this module the usual Drupal 7 way:

* Copy the _force_fid_download_ directory to _sites/all/modules_
* Enable the module
* Clear all caches

## Usage
This module persumes you have already obtained a fid.

Example:
	
	function my_custom_page_callback($node){
		$path = 'download/' . $node->field_brochure[LANGUAGE_NONE]['fid'];
		$page['link']['#markup'] = l(t('Download brocuhre'), $path);
		return drupal_render($page);
	}

