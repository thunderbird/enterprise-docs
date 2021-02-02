---
description: >-
  IT admins can pre-configure Thunderbird installations for automated deployment
  on Windows using the MSI installers provided by Thunderbird.
---

# Deploy Thunderbird with MSI installers

## MSI Installers

Thunderbird offers MSI installers per locale and per release channel for 64bit Windows systems to help system administrators customize and deploy Thunderbird in their environments. The MSI installer \(supported on Windows 7 and later versions\) is a wrapper of the full _installer.exe_ that allows customizations e. g. through the use of an MST file prior to deploying through standard Windows deployment tools such as Active Directory or Microsoft System Center Configuration Manager.

Visit our [Systems and Languages](https://www.thunderbird.net/en-US/thunderbird/all/) download page and choose your preferred language to download a `Windows MSI 64-bit` installer for the [Thunderbird release](https://www.thunderbird.net/en-US/thunderbird/all/) update channel. We also offer localized MSI installers for the [Thunderbird Beta](https://www.thunderbird.net/en-US/thunderbird/beta/all/) and [Thunderbird Daily](http://ftp.mozilla.org/pub/thunderbird/nightly/latest-comm-central-l10n/) update channels \(note that _Thunderbird Daily_ is an unstable testing and development platform not intended for production environments; make sure to back up important data regularly!\).

## MSI configuration options for automated deployment

MSI transforms \(MSTs\) for the Thunderbird MSI installers can be created or edited using the tool of your choice \([MS Orca](https://docs.microsoft.com/en-us/windows/desktop/msi/orca-exe) or other\) to customize the installation. This article describes the options available.

## Thunderbird custom MSI options

Thunderbird provides a number of custom MSI options for convenient automated installation. These options can be used alongside the _msiexec_ common options supported by Thunderbird MSI installers. There are several ways of applying Thunderbird custom MSI options for automated deployment, for example via direct MSI editing, creating transform configurations \(.mst\), or command line. More details on these methods can be found below. Here's the list of Thunderbird custom MSI options:

* **Set an application folder path: `INSTALL_DIRECTORY_PATH="path"`** _path_ \(quoted string\): Absolute folder path specifying the complete install location. This folder does not need to exist already \(but it can\). If INSTALL\_DIRECTORY\_NAME is set, then this setting will be ignored.
* **Set an application folder name: `INSTALL_DIRECTORY_NAME="name"`** _name_ \(quoted string\): Name of the installation directory to create within _Program Files_ folder. For example, if INSTALL\_DIRECTORY\_NAME is set to "Thunderbird Release", then the installation path will be something like "C:\Program Files\Thunderbird Release". The _Program Files_ path used will be the correct one for the architecture of the application being installed and the locale/configuration of the machine; this setting is mainly useful to keep you from having to worry about those differences. If this is set, then INSTALL\_DIRECTORY\_PATH will be ignored.
* **Create a taskbar shortcut: `TASKBAR_SHORTCUT=true|false`**

  Set to _false_ to disable pinning a shortcut to the taskbar. _true_ by default. This feature only works on Windows 7 and 8; it isn’t possible to create taskbar pins from the installer on later Windows versions.

* **Create a desktop shortcut: `DESKTOP_SHORTCUT=true|false`** Set to _false_ to disable creating a shortcut on the desktop. _true_ by default.
* **Create a start menu shortcut: `START_MENU_SHORTCUT=true|false`** Set to _false_ to disable creating a Start menu shortcut. _true_ by default.
* **Disable the maintenance service: `INSTALL_MAINTENANCE_SERVICE=true|false`** Set to _false_ to disable installing the Mozilla Maintenance Service. This will effectively prevent users from installing Thunderbird updates if they do not have write permissions to the installation directory. _true_ by default.
* **Disable removing** _**distribution**_ **subfolder: `REMOVE_DISTRIBUTION_DIR=true|false`** Set to _false_ to disable removing the _distribution_ subfolder from an existing installation that’s being paved over. By default this is true and the folder is removed. The default folder path of the _distribution_ subfolder is "C:\Program Files\Mozilla Thunderbird\distribution\".
* **Prevent rebooting: `PREVENT_REBOOT_REQUIRED=true|false`** Set to _true_ to keep the installer from taking actions that would require rebooting the machine to complete, normally because files are in use. This should not be needed under normal circumstances unless you’re paving over a copy of Thunderbird that was running while the installer was trying to run, and setting this option in that case may result in an incomplete installation. _false_ by default.
* **Bundle extensions: `OPTIONAL_EXTENSIONS=true|false`** Set to _false_ to disable installing any bundled extensions that are present. _true_ by default.
* **Application files extraction directory: `EXTRACT_DIR="directory"`** Extract the application files to the given directory and exit without actually running the installer. Of course, this means all other options will be ignored.

## MSIEXEC command line options

The command line options for _msiexec.exe_ \(the Windows component responsible for installing, uninstalling, and otherwise working with MSI files\) are documented [here](https://docs.microsoft.com/en-us/windows/desktop/Msi/command-line-options) and also by the output of the /? option. Our MSI packages, because they wrap an _installer.exe_ and do not really use the MSI framework, do not support many of the command line options available to _msiexec_. This document lists the _msiexec_ options that are supported and unsupported for use with our MSI packages.

### Supported MSIEXEC options

* **/i** or **/package**

  Installs the product.

* **/L** or **/log**

  Generates an MSI log file. All of this option's configuration parameters are supported.

* **/m**

  Generates an SMS status .mif file.

  Without having a copy of Systems Management Server I've been unable to test this, but it should work.

* **/q**, **/quiet**, and **/passive**

  Sets the UI mode. The full UI option \(/qf\) is accepted but ignored, because we have no full UI.

* **/norestart**, **/forcerestart**, and **/promptrestart**

  The default behavior is always /norestart, but the other options behave as expected.

* **/?**, **/h**, **/help**, **/y**, **/z** Options that do not operate on a package file.
* **CUSTOM\_OPTION=VALUE**

  Configuration via command line options is supported for all custom MSI options provided by Thunderbird \(i. e. those with UPPERCASE\_NAMES\).

### Unsupported MSIEXEC options

* **/f**

  Repairs the product.

* **/a**

  Administrative installation.

* **/x** or **/uninstall**

  Uninstalls the product.

* **/j** along with **/t**, **/g**, and **/c**

  Advertises the product.

* **/n**

  Specifies a particular instance of the product.

* **/p** or **/update**

  Applies a patch \(.msp\) file.

## Example configuration

Here’s an example of a valid .mst file to help understand how options can be changed along with the MSI directory for mozilla central:

* [MST file example](https://drive.google.com/file/d/1QiV9zDcpd42_xTOhjs4bOuHvYyg_hlyS/view)
* [MSI installer nightly builds](https://archive.mozilla.org/pub/Thunderbird/nightly/latest-mozilla-central/)
* [MSI installer current release build](https://download.mozilla.org/?product=Thunderbird-msi-latest-ssl&os=win64&lang=en-US)

Logging can be [configured](https://docs.microsoft.com/en-us/windows/desktop/Msi/command-line-options) on the MSI to help troubleshoot installation issues.

## Ways of using Thunderbird custom  options with MSI installers

There are several ways to use Thunderbird's default MSI file with your preferred configuration of custom options exposed in the MSI:

### By using an external MSI editor \(e.g. [ORCA](https://docs.microsoft.com/en-us/windows/desktop/msi/orca-exe)\)

1. `File > Open...` and select the Thunderbird MSI to be edited.
2. Find the Property table and select it.
3. Change the values for the CUSTOM\_OPTIONS you want to set.
4. From ORCA, select `File > Save as...` and save your  modified MSI installer.

Note that this will invalidate the MSI file's signature; if you need the file to be signed, you'll have to sign it again using your organization's certificate.

### By using a transform \(.mst\) configuration

1. Use Orca to open the Thunderbird MSI.
2. Select **Transform &gt; New Transform** from the menu bar.
3. Change the values for the CUSTOM\_OPTIONS you want to set.
4. Select **Transform &gt; Generate Transform** to save your changes as a transform \(.mst\) file.
5. Run:

   ```text
   msiexec /i “Thunderbird.msi” TRANSFORMS=”custom.mst”
   ```

### By using command line options

1. Rename the Thunderbird MSI file as default.msi
2. Move the file in a C:\MSI directory
3. Specify the desired CUSTOM\_OPTIONS in the command line and run:

   ```text
   msiexec.exe /i "c:\MSI\default.msi"
   INSTALL_DIRECTORY_PATH="C:\Thunderbird\" TASKBAR_SHORTCUT=false
   DESKTOP_SHORTCUT=false INSTALL_MAINTENANCE_SERVICE=false /quiet`
   ```

All Thunderbird custom MSI options \(the UPPERCASE\_OPTIONS\) can be used in the command line alongside the supported common options provided by _msiexec_ \(like /i and /quiet in the above example\).

