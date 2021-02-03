---
description: >-
  How to automatically configure Thunderbird using preferences in large-scale
  deployments
---

# Mission Control Desktop \(MCD\) - Thunderbird AutoConfig

## Introduction

This document provides a step by step instruction of configuring Thunderbird using a centralized application preferences file in large-scale deployments. Preferences are the internal settings used by Thunderbird to configure the application behaviour and define the properties of each Thunderbird account \(email, news, chat, etc.\) within a given Thunderbird profile. The classic example is an email account for a given email address with associated server settings and application behaviours. To achieve a completely automatic configuration of user-specific accounts in Thunderbird, user properties like name and email address will be retrieved either from system environment variables or from an organisation's LDAP directory.

## Scenario and objective

You can use Thunderbird AutoConfig \(MCD\) in scenarios of many users sharing computers. Hence a single computer might connect different users throughout the day, who have their personal OS account, maybe including an LDAP account for authentication. The objective is to provide users with Thunderbird as a combined email, communication and PIM client which is automatically configured via preferences at startup for the currently logged-in user on the computer. As Thunderbird can run on various operating systems, this will also work perfectly in mixed OS environments, e.g. with Windows and Linux systems. Instead of configuring individual preferences files for each end user \(prefs.js\), you can now use a centralized default set of preferences. This default configuration file can control preferences using a set of API functions and based on environment variables \(`USER`, `HOME`...\) and/or LDAP queries from an organisation's directory.

## Setting up autoconfiguration

Let's set up a default configuration for all users of a given installation on one computer. You need to create two files:

* A JavaScript file \(\*.js\) with a base name of your choice which acts as a caller for the default configuration file, let's use `autoconf.js` here.
* A JavaScript configuration file \(typically \*.cfg\) with a filename of your choice as specified in the caller, let's use `thunderbird.cfg` here. This file is encoded using byte-shift/rotary 13 by default, which can be removed if plain text is preferred.

The caller, `autoconf.js`, must be placed in the following folder:

* For Windows: _Thunderbird-install-path\defaults\pref_ , e.g.: `C:\Program Files\Mozilla Thunderbird\defaults\pref`
* For Linux: `/usr/lib/thunderbird/defaults/pref` 

For the sake of this tutorial, let's place the default configuration file, `thunderbird.cfg`, in the same folder.

The caller, `autoconfig.js`, has the following content:

* `pref("general.config.filename", "thunderbird.cfg");` \(required: specify the autoconfiguration file\)
*  `pref("general.config.obscure_value", 0);`  \(optional: specify or remove the byte-shift/rotary encoding of the autoconfiguration file; default: 13; remove encoding: 0\)

## The default configuration file

The default configuration file is an encoded JavaScript file \(see above\) which uses a JavaScript preferences API. The API is defined in a file called [prefcalls.js](https://searchfox.org/comm-central/source/mozilla/extensions/pref/autoconfig/src/prefcalls.js), which is packed in the main resource file `omni.ja` located in your Thunderbird installation folder. The following API functions are available:

```text
pref(prefName, value)
defaultPref(prefName, value)
lockPref(prefName, value)
unlockPref(prefName)
getPref(prefName)
clearPref(prefName)
setLDAPVersion(version)
getLDAPAttributes(host, base, filter, attribs, isSecure)
getLDAPValue(str, key)
displayError(funcname, message)
getenv(name)
```



## More information, tips and examples

[This blog](https://blog.deanandadie.net/tag/mission-control-desktop/) has further reading with more explanations, tips and tricks, and step by step examples.



