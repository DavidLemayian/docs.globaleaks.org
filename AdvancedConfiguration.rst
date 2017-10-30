============================
Advanced Configuration Guide
============================

The Advanced Customization Guide enables you to customize every aspect of the features in the GlobaLeaks application, like for example:

Tweak every setting;
add additional text or features by way of raw edit of the application core. This procedure is not immediate, like modifying a single .html file, because the "GlobaLeaks Client" is a JavaScript application optimized for use over a Tor Hidden Service, through a "build process"; So this guide applies only to advanced GlobaLeaks users aware of the possible security risks of the procedure.
This is not the best way to customize Globaleaks.

For the safe way to do it please refer to the Basic Customization Guide.

The steps needed to accomplish the Advanced Customization Guide are the following:

Development Environment
The development environment should be installed on a different server and it's needed mostly to develop the template because it runs immediately from sources. That way you can iteractively modify it and hit "Refresh" (F5) in your browser, without having to go through the client build process. Then, when you are satisfied with the development of your custom template, you can move onto your production server and follow the "automatic build procedure" just to build it.

Customize the client
With this you will be able to preview your template in real time (without having to build it) on your local system. The sysadmin can provide the web designer access to the template file via FTP/SFTP to facilitate customization workflow.

First you need to set up the GlobaLeaks development environment with GlobaLeaks client running from source code. Then, you will then by able to preview your template by running:

./backend/bin/globaleaks -z -k9 -d -t -n -l DEBUG
And then connecting to 127.0.0.1:8082.
