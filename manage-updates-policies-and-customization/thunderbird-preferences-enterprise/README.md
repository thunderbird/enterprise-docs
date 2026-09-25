---
description: Preferences related to using Thunderbird in enterprises
---

# Thunderbird Preferences Relevant to Enterprises

### New Email Account Provisioning

Account Provisioning allows users to sign up for new email accounts from _gandi.net_ directly from within Thunderbird.

- **mail.provider.enabled**
  - Default: true
  - Default Action: If the user does not have an account set up, they will be presented with an option to sign up for a new account. They may choose to set up an existing account that they hold instead of obtaining a new one.

### Filelink \(cloud attachments\) <a id="Filelink"></a>

Filelink is a feature that allows users to upload big files to various servers and send a link to the attachment in the email, rather than the attachment itself. This has benefits for sending the email, especially when sending to multiple users. The message will be small in size and can be sent and received faster.

Thunderbird offers an option to use WeTransfer as a cloud service. It is possible to set up other providers.

- **mail.cloud_files.enabled**
  - Default: true
  - Default Action: Prompts the user to see if they wish to send a link for large file attachments, rather than the attachment itself.
  - Notes:
    - Set this preference to `false` to disable the Filelink user interface.
    - Enterprise administrators should normally use the `DisableFileLink` enterprise policy rather than setting this preference directly.

### Chat \(Instant Messaging\) <a id="Instant_Messaging"></a>

Thunderbird's chat component allows the user to access different types of instant messaging accounts.

- **mail.chat.enabled**
  - Default: true
  - Default Action: Enables access to the Instant Messaging user interface in Thunderbird.
  - Notes:
    - Set this preference to `false` to disable access to Thunderbird's Chat user interface.
    - Enterprise administrators should normally use the `DisableChat` enterprise policy rather than setting this preference directly.

### Community Features <a id="Community_Features"></a>

Thunderbird includes links and commands that connect users with community, donation, feedback, support and development resources.

- **mail.community_features.enabled**
  - Default: true
  - Default Action: Displays community-focused links and commands throughout Thunderbird.
  - Notes:
    - Set this preference to `false` to hide community-focused user interface elements.
    - These elements include community, donation and feedback commands in the Help and application menus, as well as community links in Account Central and Account Hub.
    - Enterprise administrators should normally use the `DisableCommunity` enterprise policy rather than setting this preference directly.
    - The `DisableCommunity` policy also disables the Thunderbird Start Page and the Thundermail option in Account Hub by locking `mailnews.start_page.enabled` and `mail.accounthub.thundermail.enabled` to `false`.

### Data Collection Settings <a id="Data_Collection_Settings"></a>

Thunderbird includes settings that allow users to control the collection of technical and interaction data.

- **mail.data_collection_settings.enabled**
  - Default: true
  - Default Action: Displays the Data Collection and Use section in Thunderbird's Privacy & Security settings.
  - Notes:
    - Set this preference to `false` to hide the Data Collection and Use settings from users.
    - This preference only controls access to the settings interface. It does not disable telemetry or change the underlying data collection preferences.
    - Enterprise administrators should normally use the `DisableDataCollectionSettings` enterprise policy rather than setting this preference directly.
    - Data collection behaviour should be managed separately using the appropriate policies, such as `DisableTelemetry`.

### Export for Mobile <a id="Export_for_Mobile"></a>

Export for Mobile allows users to transfer compatible Thunderbird account settings to Thunderbird for Android by scanning one or more QR codes. Depending on the available options and the user's selection, account passwords may also be included.

- **mail.qrexport.enabled**
  - Default: true
  - Default Action: Enables the Export for Mobile user interface and allows compatible account settings to be exported using QR codes.
  - Notes:
    - Set this preference to `false` to disable the Export for Mobile feature.
    - Enterprise administrators should normally use the `DisableQRExport` enterprise policy rather than setting this preference directly.

- **pref.privacy.disable_button.view_passwords**
  - Default: false
  - Default Action: Allows saved passwords to be revealed and enables the option to include them when exporting account settings to a mobile device.
  - Notes:
    - When set to `true`, the option to include passwords in Export for Mobile is unavailable.
    - This preference affects password access elsewhere in Thunderbird as well; it is not specific to Export for Mobile.
    - Enterprise administrators should normally use the `DisablePasswordReveal` enterprise policy rather than setting this preference directly.

### Experimental Features <a id="Experimental_Features"></a>

Thunderbird may provide experimental features that users can enable from Settings. The available experimental features can vary between Thunderbird versions and release channels.

- **mail.experimental_features_settings.enabled**
  - Default: true
  - Default Action: Displays available experimental feature controls in Thunderbird's Settings.
  - Notes:
    - Set this preference to `false` to hide experimental feature controls from users.
    - This preference controls the visibility of experimental options. It does not necessarily reset experimental features that were previously enabled through their individual preferences.
    - Enterprise administrators should normally use the `DisableExperimentalFeatures` enterprise policy rather than setting this preference directly.

### In-App Notifications <a id="In-App_Notifications"></a>

Thunderbird can display in-app notifications including product announcements, surveys, informational messages and fundraising campaigns.

- **mail.inappnotifications.enabled**
  - Default: true
  - Default Action: Enables all Thunderbird in-app notifications.

- **mail.inappnotifications.donation_enabled**
  - Default: true
  - Default Action: Enables fundraising and donation notifications.

- **mail.inappnotifications.blog_enabled**
  - Default: true
  - Default Action: Enables survey and blog-style notifications.

- **mail.inappnotifications.message_enabled**
  - Default: true
  - Default Action: Enables informational message notifications.

- **Notes**
  - Setting `mail.inappnotifications.enabled` to `false` disables all in-app notifications.
  - The individual `*_enabled` preferences can be used to selectively enable or disable specific notification categories.
  - Enterprise administrators should normally use the `InAppNotification` enterprise policy rather than setting these preferences directly.

### Message Filter Forwarding <a id="Message_Filter_Forwarding"></a>

Thunderbird message filters can automatically forward matching messages to a specified email address.

- **mail.filters.forward.enabled**
  - Default: true
  - Default Action: Allows users to create message filters that automatically forward messages and allows forwarding actions in existing filters to run.
  - Notes:
    - Set this preference to `false` to remove the Forward action from the message filter editor and prevent forwarding actions in existing filters from running.
    - Other actions after a blocked forwarding action in the same filter continue to run.
    - This preference does not disable manually forwarding messages.
    - Enterprise administrators should normally use the `DisableMessageForwardingFilters` enterprise policy rather than setting this preference directly.

### Offline Download / Synchronisation <a id="HTML"></a>

- **mail.server.default.offline_download**
  - Default: true
  - Default Action: Used to determine if newly created folders are set to take part in offline download or not.
  - Notes: This is the default value for all servers/accounts when the mail.server.server&lt;n&gt;.offline_download preference is not set.
- **mail.server.server&lt;n&gt;.offline_download**
  - Default: true
  - Default Action: Used to determine if newly created folders are set to take part in offline download or not.
  - Notes:
    - This value is typically not present unless it has been specifically overridden.
    - Overrides mail.server.default.offline_download for server&lt;n&gt;

Both preferences now also have the behaviour that if offline_download is true for an account/server, then on upgrade from Thunderbird 2, all existing IMAP folders will be updated to take part in offline download.

### HTML rendering in message reader

By default all HTML elements are interpreted by the Thunderbird HTML parser. For the message reader, there are some options to control which HTML elements will get rendered. Note that some of these preferences may not be effective for composition, especially when using Edit as New Message or Forward, which may load remote content and media anyway.

- **mailnews.display.html_as**
  - Default: 0
  - Default Action: Show original HTML
  - Custom values: 1 or 3
  - Notes:
    - This preference can be controlled through the menu: `View` &gt; `Message Body As` &gt; `Original HTML (0)` \| `Simple HTML (3)` \| `Plain Text (1)`
    - Original HTML \(0\) renders all elements, subject to global and per-message or per-origin Remote Content Options.
    - Simple HTML \(3\) prevents the display of any remote content. Furthermore, this display mode can be finetuned using the html_sanitizer preferences below.
    - Plain Text \(0\) prevents the display of remote content and displays HTML downgraded to plain text.
- **mailnews.display.html_sanitizer.drop_media**
  - Default: false
  - Default Action: Allows all media files.
  - Notes:
    - Only applies to messages viewed as Simple HTML \(mailnews.display.html_as = 3, see above\).
    - To prevent rendering &lt;img&gt;, &lt;audio&gt; and &lt;video&gt; elements, i.e. to prevent images, audios, and videos from being displayed, set this preference to true.
    - The following related pref is obsolete: mailnews.display.html_sanitizer.allowed_tags

- **mailnews.display.html_sanitizer.drop_non_css_presentation**
  - Default: true
  - Default Action: Drop non-CSS presentational HTML elements and attributes, such as &lt;font&gt;, &lt;center&gt; and _bgcolor._
  - Notes:
    - Only applies to messages viewed as Simple HTML \(mailnews.display.html_as = 3, see above\).

### Application Update Settings <a id="Application_Update_Settings"></a>

Thunderbird's application update settings allow users to view and configure update behaviour.

- **mail.update_settings.enabled**
  - Default: true
  - Default Action: Displays the application update section in Thunderbird's General settings.
  - Notes:
    - Set this preference to `false` to hide the application update settings from users.
    - This preference only controls access to the settings interface. It does not disable application updates.
    - Update behaviour continues to be determined by the applicable update policies and deployment configuration.
    - Enterprise administrators should normally use the `DisableUpdateSettings` enterprise policy rather than setting this preference directly.

### Version Upgrades <a id="Version_Upgrades"></a>

#### Prompt for third-party Add-ons \(untested\)

Note: Starting with Thunderbird 78, traditional add-ons have been discontinued for security reasons. Add-ons are now generally expected to be Web Extensions using the APIs provided by Thunderbird.

- **extensions.autoDisableScopes**
  - Default: 15
  - Default Action: **When upgrading to a build from before Thunderbird 10 to after, the user will be prompted about add-ons installed by third parties.**
  - Notes:
    - This preference is a bit-wise OR of values that control the locations for which add-ons are prompted about as third-parties. **Organizations typically want to set this to 11 if they are installing their own add-ons.** The bit values are as follows:
      - 1: Installed in the profile
      - 2: Installed for all of this user's profile
      - 4: Installed and owned by the Application
      - 8: Installed for all users of the computer
