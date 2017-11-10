===================
Customization Guide
===================

Through the administrators control panel, GlobaLeaks has room for rich customization. Everything within the basic customization guide is well tested and safe, and caution is adviced using the advanced features. Some are experimental, and may be removed or changed in future versions of the software.


.. ATTENTION::
   This document is undergoing a review for contents. 
   The information in the following could be obsolete, not aligned with current features of the software.
   
   
Basic Customization Guide (default)
-----------------------------------

The **Basic Customization Guide** enables you to customize all the most important features of the application, like for example:

- Interface text;
- the look and feel (CSS, Fonts, Logos, Background)

All these settings are available through the admin panel offered by the application, and this is the safe way to customize the application.


Platform Info Customization
...........................

On page http://yoursite.com/#/admin/content, in the **Main Configuration tab** it is possible to customize the following options:

- Initiative logo
- Platform (Initiative) name
- Platform (Initiative) Subtitle
- Platform (Initiative) Description
- Platform Footer
- Platform (Initiative) Presentation
- Tor Hidden Service
- Public Site
- Look and Feel Customization

On page https://yoursite.com/#/admin/content, via the **Theme Customization tab** it is possible to customize the look and feel by uploading custom CSS.

.. CAUTION::
  **Be aware that you can easily compromise a whistleblowers identity by embedding custom fonts, images from external sources, and links to other websites. This is especially important if you are making the platform available over HTTPS.**


Uploaded files will override the default Globaleaks' CSS files.

On the same page it is possible to upload a custom file by clicking **Load Custom File**, (e.g., custom favicon.ico, robots.txt or a background.png).

Uploaded files are accessible in the http://yoursite.com/#/static path (e.g., static/file.ext).


Background Color Customization Example
......................................

This CSS example shows how to customize the Background Color of the application.

Let's create a file styles.css as follows:

.. code::
 
  body
  {
     background-color: red;
  }


Background Image Customization Example
......................................

This CSS example shows how to customize the background image of the application. Upload a background image through the **Load Custom File button**; let's call it 'background.png'.

Then we can pick and align it:

.. code::
  
  body
  {
     background-image:url('/static/background.png');
     background-repeat: repeat;
     background-position: top center;
     background-attachment: fixed;
  }


Font Customization Example
..........................

This CSS example shows how to customize the font of the application. Upload a custom font through the "Load Custom File button"; let's choose 'antani.ttf'.

Point to the file in styles.css as follows:

.. code::
  
  @font-face {
      font-family: 'Antani';
      src: url('static/antani.ttf') format('truetype');
      font-weight: normal;
      font-style: normal;
  }
  
  body {
      font-family: 'Antani', Helvetica, Arial, Sans;
      font-size: 16px;
  }


Translations Customization
..........................

On the page http://[…]/#/admin/content, via the **Translation Customization tab**, it is possible to enable available translation languages and eventually load custom translations.

GlobaLeaks is currently translated into many languages thanks to community effort. https://www.transifex.com/otf/globaleaks/dashboard/

.. HINT::
  Translations are added to the Globaleaks package whenever a new language reaches a coverage of more than 50% of translated sentences; if your language is missing, or its translation need improvement, the best you can do is to help translating it.


CSS #BodyDefault class extensions
..................................

The application also attaches the following CSS classes to the #bodyDefault <div> so that you can customize pages based on the application's location and state. For example, when a user navigates from /#/submission to /#/login the class .ext-public will be removed from #BodyDefault and .ext-login will be added.

**Class	Description**

- .ext-public	is appended to every page intended for Whistleblowers. These are the public pages.
- .ext-embed is always appended to #bodyDefault if the URL of page includes ?embedded=true
- .ext-authenticated is appended to every page when a user is authenticated. This field may be deprecated.

Refer to this file for an example on how to use these classes.

Translated links useful for landing pages
.........................................

GlobaLeaks offers the possibility to provide users links automatically localized in a chosen language, in order to avoid users having to switch between languages manually. For every link it would be possible to provide localized links by simply appending the short code of the language to the URL. For example to provide a internationalized landing page for http://[…]/#/admin/submission) it would be possible to use:

- http://[…]/#/admin/submission/it for an Italian page
- http://[…]/#/admin/submission/ru for the Russian equivalent

For the full list of available languages codes, please refer to the application page http://[…]/#/admin/content, via the **Translation Customization tab**.


Notification Templates Customization
....................................

On page http://[…]/#/admin/content, on the tabs called "Plaintext Notification Templates" and "Encrypted Notification Templates" it's possible to configure email templates for plaintext and encrypted notification respectively.

For example, by defining a notification template email with:

"Hello %ReceiverName%, there is a new submission for you in %ContextName%".
The recipient would get an email with %ReceiverName% replaced with their configured name, and %ContextName% with the name of the context of the submission in question.

There are four notification events (New submission, new comment, new message or new file uploaded) and for each one it is possible to configure a specific email template. In addition it's also possible to configure the template for a .txt file that will be included in all collection archives downloaded through the platform.

For each specific template there are some specific keywords available; for example, the encrypted version of a template allows more keywords.

The keyword available in encrypted template could contain sensitive data

To use a keyword, add percentage signs around it.

The following is the list of all availalbe keywords

Shared keywords available in all notification templates

Notification: Encrypted or plaintext email about a new submission, file, message or comment.

%EventTime%: Pretty timestamp with the name of the month in English (no localization available)
%NodeName%: The name of your node
%HiddenService%: The URL of the configured hidden service
%PublicSite%: The URL of the project reachable from the outside
%ReceiverName%: The name of the recipient
%ContextName%: The name of the context related (every submission is always under one and only one context)
Submission event

%TipTorURL%: URL of the hidden service + the submission ID, usable by the recipient (prior authentication) to access the submission.
%TipT2WURL%: This URL used for the public website (by default a tor2web extenal website) for use in reaching the submission. This is actually available only if the node is configured in to permit recipients access via Tor2Web (denied by default. Check Admin panel, Advanced Settings -> tor2web Accessibility)
%TipNum%: a "unique" three digit number assigned to every submission. Every recipient has a different %TipNum% for every submission. Used to supply an email subject, in order to easily follow the
encrypted submission event.

%TipFields%: The dump of the submission fields! This is sensitive, check the security consideration here: https://docs.google.com/a/apps.globaleaks.org/document/d/1niYFyEar1FUmStC03OidYAIfVJf18ErUFwSWCmWBhcA/edit#heading=h.la9gjvhg62sq
Comment event

%CommentSource%: is "Whistleblower" or "Recipient", useful for specifying which is the source of the comment.
all the submission event keywords
Encrypted comment event

%CommentContent%: This contains all comments, and can be sensitive, can be from either a whistleblower and a recipient.
File event

%FileName%: The name of the file
%FileType%: The content type of the file
%FileSize%: The size expressed in bytes
all the submission event keywords
Encrypted file event

(Not yet implemented, %FileDescription%, would contain the description of the file provided by the whistleblower)
Message event

%MessageSource%: A fixed string at the moment, with sole option of being: 'whistleblower', because messages are sent directly between one receipient and the whistleblower, and only recipients can get notifications,
all the submission event keywords
Encrypted Message event

%MessageContent%: This contains all messages, and can be sensitive, as it comes directly from the whistleblower.
Non notification template

When a recipient downloads the full collection of the available files (in .zip format) a file named DESCRIPTION.txt is added to the archive.

This file can be have it's content customized and has its own set of keywords (beside the Shared Keywords above)

Collection Archive Description

%FileList%: List of the files downloaded
%FilesNumber%: Number of the files
%TotalSize%: Total size of the files

