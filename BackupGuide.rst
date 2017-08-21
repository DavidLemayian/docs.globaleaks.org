=======================
Backup Guide
=======================

The following commands are required in order to create a backup of GlobaLeaks:

"date=`date +"%Y-%m-%d"`
version=`dpkg -l | awk '$2=="globaleaks" { print $3 }'`
tar zcvfp /tmp/globaleaks-backup-$date-$version.tar.gz /var/globaleaks/ /etc/default/globaleaks".
After the completion of the command you will find  a tar.gz archive within the /tmp (temporary directory named globaleaks-backup-YYYY-MM-DD-XX-YY.ZZ.tar.gz including the archived GlobaLeaks data necessary for backup and restoration.

If you want to archive the backup permanently, go ahead and save it anywhere you want.
