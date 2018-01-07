=============================
Installation guide
=============================

The following is intended to guide you through the installation and running of GlobaLeaks on a Debian based system.

Before starting the installation, make sure to read and understand the :doc:`Technical Requirements </TechnicalRequirements>`.

GlobaLeaks is built to give the best technical anonimity to the Whistleblower.

The software with specific configurations enables the possibility to protect the identity of the node administrator and the server's location but this requires advanced setup procedures not considered in this simplified installation guide.

**Install GlobaLeaks**

Copy & Paste the following commands in your terminal::

   wget https://deb.globaleaks.org/install-globaleaks.sh
   chmod +x install-globaleaks.sh
   ./install-globaleaks.sh

By executing the above set of commands, the IP address of your server will be logged by our system, that will further receive requests for downloading GlobaLeaks installation files and reports of failure of execution of installation script with the commandline that failed and it's status code.

**Configure GlobaLeaks**

There is a :doc:`Configuration Guide </ConfigurationGuide>` for your new GlobaLeaks platform installation.

**Expose GlobaLeaks via HTTPS as a normal website**

GlobaLeaks is generally exposed only via Tor (which is preferable)

While not as secure, it is possible to run GlobaLeaks like a normal website through the admin interface under Network Settings. The interface will help you get a certificate. We recommend using `Let's Encrypt <https://letsencrypt.org/>`_ as your certificate authority.
