========================
Upgrade guide
========================   

To safely upgrade a GlobaLeaks installation please proceed with a backup of your setup by following the :ref:`backup-and-restore` guide.

This is necessary so that if something goes wrong and you need to rollback, you will be able to just uninstall the current package, then install the same version of globaleaks that was previously installed and working.

In order to update GlobaLeaks perform the following commands:

.. code::
   
   apt-get update && apt-get install globaleaks


In case of errors
-----------------

The above commands should allow you to perform regularly updates. On some conditions due to special updates it could be possible that those commands result in a failure. Consult this page for knowning specific FAQs on precise failures.

In case you do not find any specific documented solution for your failure, you could run the GlobaLeaks install script again that is designed to allow the update of GlobaLeaks and fixing most common compatibility issues.

To run the install script for updating globaleaks perform the following commands:

.. code::
   
   curl https://deb.globaleaks.org/install-globaleaks.sh | bash


FAQs
----

Missing or expired PGP key
++++++++++++++++++++++++++

If your system will report a missing or expired PGP key (W: GPG error: http://deb.globaleaks.org trusty/ Release: The following signatures were invalid: KEYEXPIRED) for the repository be sure to fetch the updated key:

.. code:: 
  
  curl https://deb.globaleaks.org/globaleaks.asc | apt-key add -


HTTPS is disabled and I can no longer connect to GlobaLeaks
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

If you accidentally disabled HTTPS or determined from /var/globaleaks/log/globaleaks.log that the service is no longer serving HTTPS, you may have limited options to connect safely to the platform. If you are running Tor, the platform will be available at its onion address through the Tor browser. If you have specifically removed Tor you may have to proxy your http connections from the application server to re-access the service to repair the configuration.


GlobaLeaks fails to update due to Tor version incompatibility
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

If while running apt-get install globaleaks in order to update the platform you encounter a Tor version incompatibility be sure to have added to your distribution the official Tor repository. This requirement has been probably added after your first setup and to fix the inconvenience and perform you should just run the install script again that will recognize the existing setup, apply the needed fixes and perform the update.


How do I use the built in HTTPS server instead of Tor2Web?
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Version 2.66 of GlobaLeaks introduced HTTPS functionality directly controllable from the administration interface (under Network Settings > HTTPS Settings). In order to migrate an existing installation of GlobaLeaks that uses Tor2Web as the public web proxy you can do the following.

.. note::

Note that this guide assumes you can still connect to the service over Tor.

* Update to a version later than 2.66
* Add the hostname that will appear on the SSL certificate to Network Settings > Hostname
* Disable Network application sand boxing under Network Settings
* Stop GlobaLeaks with:
  
  .. code::
     
     service globaleaks stop
     
* Remove Tor2Web from the system with:
  
  .. code:: 
     
     apt-get remove tor2web
     
* Start GlobaLeaks with:
  
  .. code::
     
     service globaleaks start

* Check iptables is disabled with:
  
  .. code::
     
     iptables --list

* Connect through Tor and upload your private key, certificate, chain file to Network Settings > HTTPS Settings

* Click enable in Network Settings > HTTPS Settings

* Verify that the service is listening on port 80 with:
  
  .. code::
   
     netstat -tulpen 
  
  If the output does not look like the following you may need to remove the following line to /etc/default/globaleaks and restart the service.
  
  Netstat output
  
  .. code:: 
     
     ubuntu@ip-172-1-0-2:~$ netstat -tulpen
     Active Internet connections (only servers)
     Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
     tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      0          34391       python         
     tcp        0      0 127.0.0.1:9040          0.0.0.0:*               LISTEN      0          31936       tor            
     tcp        0      0 0.0.0.0:8082            0.0.0.0:*               LISTEN      0          31592       python         
     tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      0          30134       tor          
  
  Line to add to /etc/default/globaleaks
  
  LISTENING_IP=0.0.0.0
  
  Try to visit the URL displayed in Network Settings > HTTPS Settings with a normal web browser.
  If the steps worked subprocesses managed by GlobaLeaks should be listening publicly on port 443. You can test the connect against an external service like ssl labs to verify the quality of the session.
