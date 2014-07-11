[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/Jalle19/xbmc-video-server/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/Jalle19/xbmc-video-server/?branch=master)

XBMC Video Server
=================

This is a standalone web interface for XBMC which allows users to browse the library and download or stream the movies and TV shows in it.

Features
--------

* Browse and filter movies and TV shows
* Browse seasons and episodes for a TV show
* Stream media using an M3U playlist with one click
* User management (application requires login), including logging to see who's doing what and restricting access based on a whitelist
* Supports multiple XBMC instances and allows easy switching between them, including the ability to wake them using WOL if it's not available
* No configuration files
* Multiple languages
* Customizable interface

Screenshots
-----------

[![screenshot1](http://t.imgbox.com/E9TRJ1gS.jpg)](http://i.imgbox.com/E9TRJ1gS.jpg) [![screenshot2](http://t.imgbox.com/d8VVi46K.jpg)](http://i.imgbox.com/d8VVi46K.jpg) 
[![screenshot3](http://t.imgbox.com/actvy5rQ.jpg)](http://i.imgbox.com/actvy5rQ.jpg) 
[![screenshot4](http://t.imgbox.com/acwlf35k.jpg)](http://i.imgbox.com/acwlf35k.jpg)  [![screenshot5](http://t.imgbox.com/PDzqmqG4.jpg)](http://i.imgbox.com/PDzqmqG4.jpg) 
[![screenshot6](http://t.imgbox.com/UxvIw9vB.jpg)](http://i.imgbox.com/UxvIw9vB.jpg) 
[![screenshot7](http://t.imgbox.com/acumBdVg.jpg)](http://i.imgbox.com/acumBdVg.jpg) 
[![screenshot8](http://t.imgbox.com/acoIuF8V.jpg)](http://i.imgbox.com/acoIuF8V.jpg)

Requirements
------------

* PHP 5.4
* allow_url_fopen = On in php.ini
* Apache with .htaccess support enabled
* XBMC 12 "Frodo" (seeking works reliably on v13 "Gotham" only)

Installation
------------

Instructions for Linux, Windows and Mac OS X are available on the [wiki](https://github.com/Jalle19/xbmc-video-server/wiki/Installation-instructions).

Initial setup
-------------

Once the installation is complete, use your web browser to browse to /xbmc-video-server on your web server (if you did the installation steps on your local machine the URL would be http://localhost/xbmc-video-server). You will be presented with a login form. Log in with username "admin" and password "admin" (you'll be able to change this later).

Once logged in, you will be asked to configure a backend. A backend is an instance of XBMC that the application connects to and displays library contents from. Here you should specify XBMC's hostname and port as well as the username and password for XBMC's web server.

If you generally put your XBMC computer to sleep you can enter its MAC address when configuring the backend. When a MAC address is present, XBMC Video Server will automatically wake the computer using Wake on LAN if it is deemed unconnectable. A loading screen is presented while this happens.

If you specify more than one backend, a "Change backend" menu item will appear which allows you to switch which backend is being used. This way you don't have to install this application once for every XBMC instance you have, or you can use it to connect to a friend's library (provided he has opened the relevant ports in his firewall).

Proxy Location
--------------

See the [wiki](https://github.com/Jalle19/xbmc-video-server/wiki/Configuring-a-reverse-proxy) on how and why to configure a reverse proxy.

User management
---------------

Once you've configured the application you should be able to browse your library. You can configure new users from the Settings menu. There are three user roles; user, administrator and spectator. A standard user cannot see (and cannot access by other means) the settings pages, a spectator can't stream or download anything (just "spectate"), and an administrator can naturally do everything.

### Restricting access

You can restrict access to specific IP addresses, networks and domains by using the whitelist feature. The restriction applies globally (ie. regardless of backends) and is configured from the Settings page. The application will warn you if you're about to lock yourself out of the application.

Security implications
---------------------

This application is insecure by virtue of design. Since there is only one set of credentials for XBMCs API and the only way to authenticate from a media player (such as VLC) is by passing the credentials in the URL. You can avoid exposing the actual API and API credentials to your users by configuring a proxy location, but that exposes the XBMC virtual filesystem on an authentication-less URL. Thus, if you use a proxy location, you should specify a non-guessable one so that outsiders can't accidentally gain access to your media files.

Regardless of whether you use a reverse proxy or not, your smb:// login credentials will be visible in the URLs generated by the application. If this is a concern you should consider mounting the network share in your OS instead of via XBMC.

Interface customization
-----------------------

If for some reason you're not satisfied with the look and feel of the application, you can customize it by adding your own stylesheets. There are two stylesheets you can add, `custom-login.css` and `custom-styles.css`. These files should be placed in the `src/css` directory. If they exist they are loaded after the applications default stylesheet, which means you can override anything you want. The `custom-login.css` is only used on the login page so if you don't need to customize anything there you don't have to create the file.

Credits
-------

XBMC (http://xbmc.org/)

Yii framework (http://www.yiiframework.com/)

Yiistrap (http://www.getyiistrap.com/)

Yii-less (https://github.com/Crisu83/yii-less)

yii-consoletools (https://github.com/Crisu83/yii-consoletools)

eventviva/php-image-resize (https://github.com/eventviva/php-image-resize)

phpass (http://www.openwall.com/phpass/) (https://github.com/hautelook/phpass)

Zend framework (http://framework.zend.com/)

mobiledetectlib (https://github.com/serbanghita/Mobile-Detect) and gavroche/browser (https://github.com/gabrielbull/php-browser)

jsonmapper (https://github.com/netresearch/jsonmapper)

Bootswatch (http://bootswatch.com/)

Font Awesome (http://fortawesome.github.io/Font-Awesome/)

jQuery Unveil (http://luis-almeida.github.io/unveil/)

typeahead.js (http://twitter.github.io/typeahead.js/)


License
-------

This software is licensed under the GNU GENERAL PUBLIC LICENSE Version 3.
