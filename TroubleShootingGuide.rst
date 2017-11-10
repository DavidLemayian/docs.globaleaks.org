=====================
Troubleshooting guide
=====================

Enhance your administration skill, to better investigate issues, and send more detailed reports about them.


Change password
----------------

If you forget the admin password, but still have access to the database, changing it is possible by using a script called gl-reset-password

::
  
  gl-reset-password --help
  
  Usage: gl-reset-password [options]
  
  Options:
    -h, --help            show this help message and exit
    -f DB_PATH, --file=DB_PATH
                        change password on a provided database file
                        [default: /var/globaleaks/db/glbackend-5.db]
    -v, --verbose         enable verbose output of executed commands
                        [default: False]

Here is example usage:

::
  
  gl-reset-password --file /var/globaleaks/db/glbackend.db

  Editing DB at path /var/globaleaks/db/glbackend.db
  
  =================================
  ||   Your new admin password   ||
  =================================
       Username: admin
       Password: 7cJjfDJBMwp3JnBG
  =================================


Installation issue
------------------

If you encounter an installation issue and you are not able to successfully access GlobaLeaks web interface, you should always:

- Be sure to strictly follow the Installation Guide for installation
- Be sure to satisfy the Technical Requirements for hardware and operating system version.
- Having tried that without results, please go to our support forum: https://forum.globaleaks.org/c/support/glinstallation


Sanity Checks
-------------
Depending on your setup. There are a few things that are usually the first things to check to see if GlobaLeaks is working.

- Is the service running?

::
  
  service globaleaks status

- Is the service responding on the loopback interface?

:: 
  
  curl -vvv localhost:8082

- Is the service listening on external interfaces? Is Tor2Web service listening on 443?

::
  
  netstat -tap

- Are exceptions being generated?

::
  
  less /var/globleaks/logs/globaleaks.log



Log files
---------

There are a few useful logs and corresponding log files when GlobaLeaks is installed.

**GlobaLeaks process:**

::
  
  /var/globaleaks/logs/globaleaks.log


The verbosity is configurable at startup with the following options:

::
  
  --loglevel DEBUG --loglevel INFO --loglevel ERROR --loglevel CRITICAL (default option) -o, --orm-debug enable ORM debugging (AVAILABLE ONLY IN DEVEL MODE) -j, --request-log enable request/response logging (AVAILABLE ONLY IN DEVEL MODE)
  

.. NOTE::

  **Privacy Note**: some log entries of the orm-debug, request-log and the DEBUG and INFO level will contain information about users. These options should not be used in production.


**Tor:**

::
  
  /var/log/tor/log Iptables: /var/log/syslog AppArmor: /var/log/kern.log



Error reporting (via Email)
---------------------------

GlobaLeaks supports a method to catch all Python/Twisted language exceptions. These unexpected and unhandled exceptions are software bugs, which are sent via email to either the system administrator's address or to 
*globaleaks-stackexception@lists.globaleaks.org* by default.


You are strongly encouraged to change the exception mail address.


General overview
----------------

From the Administrator panel there are three overview options, they permit a general overview of the database content and initiative usage. some anomalies may be spotted from here. The three views are: Submission usage (frequency of access, time to live, etc), Files reference on the database and eventually inconsistency with files stored but not recorded on the database (nothing that can happen normally, but if the database is removed from a running installation, the files related would remain stored).

Submission overview
............

- **status**: is usually first, and means that the InternalTip has been delivered for the first time to the recipient.
- **creation_date**: aligned with the time-zone of the server, the creation date states the time the whistleblower accessed the submission interface.
- **wb_last_access**: A relative date showing if the wb has come back with the receipt
- **internalfiles**: size, filename and content-type of the submitted files.
- **recipienttips**: the status of users' submissions, notified means they have already received an email with the new Submission notification.
- **expiration_date**: Time when submission, related files and comment will be deleted, (check the [customization guide] to change it, search for "timetolive")
- **context**: Name of the context the submission is submitted under.
- **comments**: Comments authors and timing.

User overview
.............

- **User**: Name and link to the recipient
- **failed login**: Number of failed logins since the last successful access.
- **Recipient submissions**: A list containing the status of the available recipient-submission (notified, commonly), and the notification date, if available.
- **Files and download**: list of available files and the number of downloads.

Files overview
..............

- **Name**: Original filename, ID which belong to, date of submission and path on the disk
- **Info**: Content-type declared by the whistleblowers browser.
- **Size**: In byte.
- **References**: Number of Recipienttips associated to that file.

User Interface troubleshooting
------------------------------

When reporting an issue with the User Interface be sure to provide the following elements:


Platform details
................

- The **browser version**

- The **operating system version** you are using


Output of developer console
...........................

You should include the output (if any) of the developer console when the bug occurs. Be sure to open the developer console and then reproduce the bug.

In **Chrome** this can be done with:

- Windows: 
  ::
    
    CTRL-SHIFT-J
    
- Mac OS X: 
  ::
    
    ALT-⌘-J
    

In **Firefox** this can be done with: 

- Windows: 
  ::
    
    CTRL-SHIFT-K 
    
- Mac OS X: 
  ::
    
    ALT-⌘-K


A screenshot
............

If the issue is a flaw with the user interface (i.e. something that looks wrong) please attach a screenshot.

Look here for details on how to take a screenshot on **Windows** (http://www.wikihow.com/Take-a-Screenshot-in-Microsoft-Windows).

Look here for details on how to take a screenshot on **Mac OS X** (http://guides.macrumors.com/Taking_Screenshots_in_Mac_OS_X)

For **Linux|GNU**, pressing PrtScr usually brings up a screen-capture tool.
