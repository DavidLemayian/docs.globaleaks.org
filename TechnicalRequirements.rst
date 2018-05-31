======================
Technical Requirements
======================

Make sure you understand and satisfy each of these technical requirements:

**Operating System**
--------------------
GlobaLeaks is designed to run on GNU/Linux.

The software is actively developed and tested specifically for Ubuntu Bionic 18.04

The software lifecycle of the platform includes full support for all Ubuntu LTS versions starting from Ubuntu Xenial 16.04.

On these platforms the support is guaranteed following the `Release End of Life <https://www.ubuntu.com/info/release-end-of-life>_` defined by Ubuntu.

Support for more distributions is planned.

**Server sizing**
-----------------
**Requirements**:

- CPU: Dual core 2.0GHz
- RAM: 2GB (Does not impact the maximum filesize that a platform installation can handle in upload)
- STORAGE: 20GB Allocate more based on data retention policy and (expected) traffic.
- I/O: 10Mbit/s (shared)
- Email account

GlobaLeaks makes use of email to handle submission notification. To this aim you need an email account to be used to send submission related notifications to recipients. This email account needs to be available and the respective SMTP server must support SMTPS or SMTP/TLS in order to securely manage sending of email.

For security and resource availability, GlobaLeaks needs a dedicated server. Depending on the architecture you may need one or two servers allocated to GlobaLeaks. The two-server hosting architecture requires that you use different data-centres for each of them. Refer to the `threat model <https://docs.google.com/document/u/1/d/1niYFyEar1FUmStC03OidYAIfVJf18ErUFwSWCmWBhcA/pub>_` description for more information on this topic.

**GNU/Linux skills**
----------------
To set up and maintain GlobaLeaks you should have basic GNU/Linux skills, practice in installing packages, upgrading, running web servers, basic debugging and analysis of email logs.
