---
description: >-
  How to setup Thunderbird policies in cross-platform organisational
  environments
---

# Customizing Thunderbird using policies.json

Policy support can be implemented using a JSON file called policies.json. Unlike controlling Thunderbird [using Windows Group Policy](https://support.mozilla.org/en-US/kb/customizing-firefox-using-group-policy-windows), the policies.json is cross-platform compatible, making it the preferred method for organisational environments that have workstations running various operating systems.

To implement this policy support, a `policies.json` file needs to be created. This file goes into a directory called `distribution` within the Thunderbird installation directory. This directory is not usually included by default, so you may need to manually create it.

The policies.json file looks like this:

```text
{
 "policies": {
   "BlockAboutConfig": true
 }
}
```

In this example, we are setting the `BlockAboutConfig` policy to `true`, which means that the user will not have access to the `about:config` page.

The latest information about our policies is available in [the README on our GitHub repository](https://github.com/thundernest/policy-templates/blob/master/README.md).

{% hint style="warning" %}
**NOTE:** The above method will not work if Thunderbird is already being managed using Windows Group Policy.
{% endhint %}

\*\*\*\*

