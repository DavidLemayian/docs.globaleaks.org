=============================
Installation guide
=============================

The following is intended to guide you through the installation and running of GlobaLeaks on a Debian based system.

Before starting the installation, make sure to read and understand the :doc:`Technical Requirements </TechnicalRequirements>`.

.. Important::
   If you want to support our research you can follow the :doc:`guidelines to set up the GlobaLeaks Experimental Release </ExperimentalReleasesGuidelines>`.

**Install GlobaLeaks**

Copy & Paste the following commands in your terminal: ::

  wget https://deb.globaleaks.org/install-globaleaks.sh
  
  chmod +x install-globaleaks.sh
  
  ./install-globaleaks.sh
  

**Configure GlobaLeaks**

There is a :doc:`Configuration Guide </ConfigurationGuide>` for your new GlobaLeaks node.

**Expose GlobaLeaks via HTTPS as a normal website**

GlobaLeaks is generally exposed only via Tor (which is preferable)

While not as secure, it is possible to run GlobaLeaks like a normal website through the admin interface under Network Settings. The interface will help you get a certificate. We recommend using `Let's Encrypt <https://letsencrypt.org/>`_ as your certificate authority.
