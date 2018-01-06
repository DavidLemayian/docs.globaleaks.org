=============================
Installation guide
=============================

The following is intended to guide you through the installation and running of GlobaLeaks on a Debian based system.

Before starting the installation, make sure to read and understand the :doc:`Technical Requirements </TechnicalRequirements>`.

.. ATTENTION::
   GlobaLeaks is built to give the best technical anonimity to the Whistleblower, not to the node administrator nor to the node location. 
   GlobaLeaks does not implement security measures against de-anonymization of the node location ot of the node administrator.
   Furthermore, GlobaLeaks sends some very little information to the developers in order to early debug malfunctioning. The information sent are [to be completed]
   

**Install GlobaLeaks**

Copy & Paste the following commands in your terminal: ::

  wget https://deb.globaleaks.org/install-globaleaks.sh
  
  chmod +x install-globaleaks.sh
  
  ./install-globaleaks.sh

**Configure GlobaLeaks**

There is a :doc:`Configuration Guide </ConfigurationGuide>` for your new GlobaLeaks platform installation.

**Expose GlobaLeaks via HTTPS as a normal website**

GlobaLeaks is generally exposed only via Tor (which is preferable)

While not as secure, it is possible to run GlobaLeaks like a normal website through the admin interface under Network Settings. The interface will help you get a certificate. We recommend using `Let's Encrypt <https://letsencrypt.org/>`_ as your certificate authority.
