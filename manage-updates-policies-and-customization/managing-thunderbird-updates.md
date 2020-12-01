# Managing Thunderbird Updates

We recommend keeping automatic updates enabled for all Thunderbird deployments to ensure that the latest security patches are applied and all features are available, but your specific environment may prevent automatic updates.

{% hint style="success" %}
Thunderbird automatically benefits from all security updates of the underlying Mozilla platform technology.
{% endhint %}

## Thunderbird Releases

[Thunderbird releases](https://www.thunderbird.net/en-US/thunderbird/releases/) generally follow the Extended Support Release \(ESR\) schedule of Firefox, but the exact release dates might deviate by some days.  For a friendly overview of the scheduled Thunderbird release dates, you can consult the ESR column of Mozilla's [Release Calendar](https://wiki.mozilla.org/Release_Management/Calendar). You can also link to the  Thunderbird Release Calendar via this [ICS for Thunderbird/Lightning or your calendar app](https://www.google.com/calendar/ical/mozilla.com_2d37383433353432352d3939%40resource.calendar.google.com/public/basic.ics).

| Update type | TB Version example \(release\) | Frequency | Scope |
| :--- | :--- | :--- | :--- |
| Major | 78.0 | Every Year | New features delivered and bugs fixed in the last 12 months. |
| Minor | 78.1 | Every four weeks | Stability/correctness and security bug fixes. |
|  | 78.1.1 | As required | Critical stability or security bug fixes. |

Thunderbird's release and beta version numbers generally match those of Mozilla Firefox ESR and beta versions. Unlike Firefox, Thunderbird releases the rapid release versions between ESRs only as betas, so the major release version numbers will jump e.g. from TB 78 directly to TB 90.

## Disabling Thunderbird updates

Automatic updates are enabled by default, but you can disable them using the [DisableAppUpdate policy](https://github.com/thundernest/policy-templates/blob/master/README.md#disableappupdate).

