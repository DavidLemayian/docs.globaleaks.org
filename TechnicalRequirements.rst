======================
Technical Requirements
======================

Make sure you understand and satisfy each of these technical requirements:

**Operating System**
--------------------
GlobaLeaks is designed to run on GNU/Linux. Ubuntu Xenial 16.04 LTS is the officially supported platform.
Support for more distributions is planned.

**Server sizing**
-----------------
For security and resource availability, GlobaLeaks needs a dedicated server. Depending on the architecture you may need one or two servers allocated to GlobaLeaks. The two-server hosting architecture requires that you use different data-centres for each of them.

**Minimum requirements**:

- CPU : Dual core 2.0GHz
- RAM : 4GB (Does not impact the maximum filesize that a node can handle in upload)
- STORAGE: 40GB Allocate more based on data retention policy and (expected) traffic.
- I/O : 10Mbit/s (shared)
- Email account

GlobaLeaks makes use of email to handle submission notification. To this aim you need an email account to be used to send submission related notifications to recipients. This email account needs to be available and the respective SMTP server must support SMTPS or SMTP/TLS in order to securely manage sending of email.

**GNU/Linux skills**
----------------
To set up and maintain GlobaLeaks you should have basic GNU/Linux skills, practice in installing packages, upgrading, running web servers, basic debugging and analysis of email logs.
