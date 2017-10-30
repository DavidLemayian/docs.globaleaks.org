=================
Integration Guide
=================

This guide illustrates how GlobaLeaks can be integrated into an existing website.

Integration Architecture
------------------------

Usually, a media organization or an NGO wants to make the platform available through an existing HTTPS website. 
A key advantage of integrating GlobaLeaks into an HTTPS website is that it allows organizational partners present the initiative to the public in a shared, unified, and collaborative way.

When using an existing HTTPS website with GlobaLeaks, we recommend that the GlobaLeaks platform and Tor2Web – the service which makes GlobaLeaks accessible – be setup as a reverse proxy on a path like /globaleaks. Using a reverse proxy over HTTPS through the existing website improves the safety of whistleblowers because it lets them blend in with other users who are just visiting the website. This gives a whistleblower **plausible deniability** at the network level as well at the human level.

The following diagram illustrates the network architecture of the typical setup:

Source --HTTPS--> Public Website --HTTPS--> Tor2web --Tor--> GlobaLeaks

It is mandatory that the Public Website runs a webserver (e.g.: Apache2 or NGINX) that uses HTTPS with a reverse proxy configuration that proxies requests to Tor2web/GlobaLeaks.

Additional guidelines on this topic are available at:

https://github.com/globaleaks/GlobaLeaks/issues/1128
https://github.com/globaleaks/GlobaLeaks/issues/1130)

.. HINT::
   If you need to configure the subpath where GlobaLeaks handler answers because you are using a limited reverse-proxy (es: Cisco ACE 4700), then you need to configure it as documented on Reverse Proxy Hack.


Main Components to Integrate
----------------------------

There are two main components that need to be integrated into an initiative's website. They are:

The **Submission interface** (this lets a whistleblower make a new submission): /#/submission
The **Receipt interface** (this lets a whistleblower interact with an existing submission): /#/receipt

These are the main examples which are typically required. In general though, every URL in GlobaLeaks can be embedded on the host's website. If the URL Parameter ?embedded=true is appended to a GlobaLeaks URL, the page's header and footer is removed and the page becomes embeddable within another page.

Integration modes:

Then depending on the integration requirements the following configurations are possible:

Plugin based integration (suggested)
iframe based integration
Plugin Based Integration

GlobaLeaks provides a specific Javascript plugin to be used for integration. The platform makes it available at /js/plugin.js.

The plugin can be included on a website with a script tag like:

<script type="text/javascript" src="https://PublicWebsite/globaleaks/js/plugin.js"></script>
The plugin safely loads the platform as a widget by calling the function StartGlobaLeaks().

This function can be used to embed specific platform resources. In the following example the submission interface is loaded when the link is clicked.

<a href="javascript:startGlobaLeaks('https://PublicWebsite/globaleaks/#/submission')" style="text-decoration: none;">Blow the Whistle!</a>
Iframe Based Integration

Using iframes to integrate GlobaLeaks into a website is not recommended because browsers are known to leak information about a whistleblowers browsing activity. However, they have been used in the past in low-risk environments and are worth mentioning. Including the two main components is similar to the plugin based solution discussed above.

Submission interface

<iframe width="100%" height="100%" frameborder="0" src="https://PublicWebsite/globaleaks/#/submission">
</iframe>
Receipt Interface

<iframe width="100%" height="100%" frameborder="0" src="https://PublicWebsite/globaleaks/#/receipt"></iframe>
GlobaLeaks Parameters

There are several URL parameters that a web developer can use to change the GlobaLeaks platform's behaviour when integrating the platform into a website.

Language Selection

The lang URL parameter pre-selects the language used in the interface. The example below loads the submission interface in English.

https://PublicWebsite/globaleaks/#/submission?lang=en
Context Selection

The context URL parameter selects a specific submission context to load by passing a UUID. For example:

https://PublicWebsite/globaleaks/#/submission?context=06cb60d2-13a4-4aa3-926f-85b64f12239d
Note that a context's UUIDs can be found on the platform in the context configuration section of the administration interface.

Recipients Selection

The receivers URL parameter selects specific recipients to the submission by passing a list of UUIDs. For example:

https://PublicWebsite/globaleaks/#/submission?context=06cb60d2-13a4-4aa3-926f-85b64f12239d&receivers=["06cb60d2-13a4-4aa3-926f-85b64f12239d","03cb60d2-13a4-43a3-926f-85b64f12232z"]
This configuration requires that the context parameter is set and the recipients are selected from among those configured for the specified context.

The UUIDs of recipients can be found on the platform in configuration section for each context.
