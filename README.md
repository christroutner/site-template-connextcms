# site-template-connextcms
This is a template for customizing ConnextCMS/KeystoneJS for a new website.
It's a slimmed down copy of the [ConnextCMS Plugin Template](https://github.com/skagitpublishing/plugin-template-connextcms),
with the ConnextCMS plugin code removed. This template contains the basic files required to
customize a website served by KeystoneJS and (optionally) managed with ConnextCMS.

## File Structure
    |--keystone/
    |  This is where the KeystoneJS specific files live.
    |  |--models/
    |  |  Add any KeystoneJS models that your plugin needs to this directory.
    |  |--routes/
    |  |  This directory contains the handlers for any new APIs
    |  |  |--exampleRouter.js
    |  |  |  KeystoneJS reads this file to add new View and API paths to the KeystoneJS router.
    |  |  |--exampleplugin.js
    |  |  |  This is a demo/example API handler file.
    |  |--templates/views/
    |  |  This directory contains the KeystoneJS Views
    |  |  |--test.hbs
    |  |  |  This is an example KeystoneJS view.
    |  |  |--loggedinuser.hbs
    |  |  |  This is an example KeystoneJS view that is only accessible to logged in users.
    |  |  |--index.hbs
    |  |  |  This files contains the HTML displayed on the homepage.
    |  |--template/views/layouts/
    |  |  |--default.hbs
    |  |  |  This files contains the HTML that make up the header (navigation menu) and footer of the site.
    |--merge-plugin
    |  Bash shell script for merging your site into a working installation of ConnextCMS and KeystoneJS.
    |  This file assumes you are installing into your home directory (~). If not, change the file paths in this script.


# Installation
The easiest way to get started with ConnextCMS and KeystoneJS is to [clone a demo Droplet](http://connextcms.com/page/clone-your-own). 
This provides you with a operational website out-of-the-box. Follow these [installation instructions](https://github.com/skagitpublishing/connextCMS/wiki/2.-Installation#cloning-the-live-demo)
after recieving your copy of the demo droplet.

If you're not sold on using Droplets and want to develop your website on a different platform,
consider [cloning the Docker image for ConnextCMS](https://github.com/christroutner/docker-connextcms). 
This will also allow you to easily get ConnextCMS and KeystoneJS up and running on any OS or hardware platform
that can run Docker.

Regardless of platform, the installation instructions below assume you are starting with a working copy
of ConnextCMS and KeystoneJS.

1. Start by creating a directory to host this repository. It's assumed that you are following
[ConnextCMS best practices](https://github.com/skagitpublishing/ConnextCMS/wiki/2.-Installation#installation-best-practice) 
and have a `keystone4` and `connextCMS` directory in your home directory. 
For documentation purposes, it's assumed the directory hosting this repository is `~/theme`.

2. Clone this repository and enter the newly created directory:
```
git clone https://github.com/skagitpublishing/site-template-connextcms
cd site-template-connextmcs
```

3. Run the merge script:
`./merge-plugin`

This will copy the index.hbs and default.hbs files that contain the HTML of the hompage and navigation menu, respectively.
You should notice that the homepage on the default installation of ConnextCMS will have changed after running the merge script.
Edit these files with your own HTML to customize the site.

