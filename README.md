# site-template-connextcms
This is a template for customizing ConnextCMS/KeystoneJS for a new website.
It's a slimmed down copy of the [ConnextCMS Plugin Template](https://github.com/skagitpublishing/plugin-template-connextcms),
with the ConnextCMS plugin code removed. This template contains the basic file system required to
customize a website served by KeystoneJS and managed with ConnextCMS.


This repository is being actively developed. It is not ready for general use.


# Installation
The easiest way to get started with ConnextCMS and KeystoneJS is to [clone a demo Droplet](http://connextcms.com/page/clone-your-own). 
This provides you with a operational website out-of-the-box. 

If you're not sold on using Droplets and want to develop your website on a different platform, seriously
consider [cloning the Docker image for ConnextCMS](https://github.com/christroutner/docker-connextcms). 
This will also allow you to easily get ConnextCMS and KeystoneJS up running on any OS or hardware platform
that can run Docker.

Regardless of platform, the installation instructions below assume you are starting with a working copy
of ConnextCMS and KeystoneJS.



# Plugin & New Site Considerations
The main things that a plugin or new site will need to modify on a ConnextCMS install is:
* Keystone Misc Files
  * /keystone.js - Probably want to add or modify parts of this file, or at least replace the original.
* KeystoneJS Routes
  * routes/index.js - need to modify or insert instructions into this file
  * routes/api/ - just need to copy files into this directory
  * routes/views/ - just need to copy files into this directory
* KeystoneJS Templates
  * templates/views/index.hbs - Will want to replace this default file.
  * templates/views/dashboard.hbs - Will want to append parts to this file. **Not sure how to do this**
    * *I may be able to create a div at the end of all the view divs. Make sure it's not of class 'container'. I can then create a Backbone view that loads the plugin views into this div.*
  * templates/views/layouts/default.hbs  - Will want to modify parts of this file.
  * templates/views/ - May want to add files to this directory.
* KeystoneJS Models
  * models/ - Will want to add or replace files in this directory.
* Public directory
  * /public/images/ - Will want to add images to this directory
  * /public/styles/ - Will want to add files to this directory
  * /public/js/ - Will want to add files to this directory
  * /public/js/lib/ - Will want to add files to this directory
  * /public/js/cms_common.js - Require.js file. Each plugin can have its own file like this that gets loaded after this one.
* Backbone
  * /public/app/model/ - Will want to add files to this directory
  * /public/app/templates/ - Will want to add or modify files in this directory
  * /public/app/views/ - Will want to add or modify files in this directory
  * /public/app/ - May want to add whole new directories here containing Backbone applications.
  * /public/app/templates/leftMenu.html - Will want to modify this to add new views to the menu. **Not sure how to do this.**
  * /public/app/views/leftMenuView.js - Will want to modify this to add new views to the menu. **Not sure how to do this.**


# New Site vs Plugin
Need to differentiate between Customizing a new site vs plugins:


* A plugin:
  * Will probably want to add an entry to the Left Menu View in the /dashboard.
    * If so, they'll want their own Backbone View and Template
  * Will probably need an API.
  * Will probably need both Backbone and Keystone Models.
  * May want to create a brand new Backbone app.
    * Which would need its own KeystoneJS View and Route
      * =2 new files + modification of routes/index.js file
  * Assumption: No need to modify the main keystone.js file.
  * Will probably want to load additional JavaScript libraries in the /public/js directory.
  * There can be zero to many plugins per site.
  * More appropriate if loaded into a `/private/plugins` directory
  
  
  * Examples of plugins:
    * eCommerce/Product Management
    * User Management
    * Logging work
    * Displaying website analytics summary
      
      
      
* A new site:
  * Will definitely want to replace the default.hbs and index.hbs files.
  * Will definitely want to replace the keystone.js file.
  * Will have its own JavaScript, CSS, and Font files.
  * There will only be one 'site' that may contain many 'plugins'
  * A site is more appropriate for a `./merge` file.