========================
Upgrade guide
========================   

Regular Update
-----------------
To safely upgrade a GlobaLeaks installation please proceed with a backup of your setup by following the :doc:`Backup and Restore </BackupAndRestore>` guide.

This is necessary so that if something goes wrong and you need to rollback, you will be able to just uninstall the current package, then install the same version of globaleaks that was previously installed and working.

In order to update GlobaLeaks perform the following commands:

.. code::
   
   apt-get update && apt-get install globaleaks
   
Distribution Update
-----------------
For security and stability reasons it is recommended to not perform a distribution upgrade.

GlobaLeaks could be instead easily migrated to a new up-to-date Ubuntu System with the follwing recommended instructions:

- create an archive backup of /var/globaleaks
- instantiate the lates Ubuntu LTS available
- log on the new server and extract the backup in /var/globaleaks
- follow the :doc:`Installation Guide </InstallationGuide>`; GlobaLeaks while installing will recognize the presence of an existing data directory and will use it

In case of errors
-----------------
The above commands should allow you to perform regularly updates. On some conditions due to special updates it could be possible that those commands result in a failure. Consult this page for knowning specific FAQs on precise failures.

In case you do not find any specific documented solution for your failure, you could run the GlobaLeaks install script again that is designed to allow the update of GlobaLeaks and fixing most common compatibility issues.

To run the install script for updating globaleaks perform the following commands:

.. code::
   
   wget https://deb.globaleaks.org/install-globaleaks.sh
   chmod +x install-globaleaks.sh
   ./install-globaleaks.sh
