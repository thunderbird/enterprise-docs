---
description: >-
  How you can customize Thunderbird's date and time formats using regional
  settings or override preferences.
---

# Customize Thunderbird's date and time formats

## Customize Thunderbird's date and time formats

### Thunderbird date and time formats defined by operating system or application locale

By default, Thunderbird will use date and time formats according to the regional settings of your operating system. If you have more than one language pack installed for Thunderbird, and if the regional settings of your operating system are different from your current Thunderbird user interface language, you can also choose the application locale for Date and Time Formatting:

```text
≡ > Preferences > General > Date and Time Formatting >
🞇 Application locale: German (Germany)
🞅 Regional settings locale: English (United States)
```

This will reflect in the underlying Thunderbird preference:

`intl.regional_prefs.use_os_locales = true` \(default: _Regional Settings locale_\)

`intl.regional_prefs.use_os_locales = false` \(modified: _Application locale_\)

Thunderbird will then format date and time according to your regional choice, for example:

* English \(United States\): `01/02/2022, 12 PM`
* German \(Germany\): `02.01.2022, 12:00`

Whilst such regional formats might be well understood in their original regions, they can be ambiguous in international contexts, for example due to the inversion of day and month in English, or \(if you're used to that\) the _absence_ of inversion in German, and the strange dots in between. Similarly, the English time 12 PM might leave many guessing if that's 12 noon or 12 midnight...

So if you are looking for an easy way to clarify your dates and times without resorting to Swedish regional settings, Thunderbird's date and time format override preferences will come in handy.

### How to create date and time format override preferences using Thunderbird's Config Editor

Thunderbird's date and time format override preferences will allow you to apply date and time formats which are different and independent of those defined by the regional localizations available in your operating system or Thunderbird. You need to create these preferences and set them to your preferred format.

This feature is currently available in Thunderbird Beta 90.0b2 and Daily 91.0a1, both available for [download from Thunderbird homepage](https://www.thunderbird.net/#channel).

The following string preferences are supported by the platform:

| Preference | Example value | Output | Description |
| :--- | :--- | :--- | :--- |
| `intl.date_time.pattern_override.date_short` | yyyy-MM-dd | 2025-12-31 | Short date |
| `intl.date_time.pattern_override.date_medium` |  |  | Medium date |
| `intl.date_time.pattern_override.date_long` |  |  | Long date |
| `intl.date_time.pattern_override.date_full` |  |  | Full date |
| `intl.date_time.pattern_override.time_short` | HH:mm | 09:59 | Short time |
| `intl.date_time.pattern_override.time_medium` |  |  | Medium time |
| `intl.date_time.pattern_override.time_long` |  |  | Long time |
| `intl.date_time.pattern_override.time_full` |  |  | Full time |

Note:

* For the preference values, you need to use valid Unicode date field symbols as listed in the [Date Field Symbol Table](https://unicode.org/reports/tr35/tr35-dates.html#Date_Field_Symbol_Table).

  The most useful preferences are `intl.date_time.pattern_override.date_short`  and `intl.date_time.pattern_override.time_short`. For example, these preferences are used to construct the date/time stamps in message reader, in combination with `intl.date_time.pattern_override.connector_short` described below.

You can use Thunderbird's inbuilt config editor to create these prefs: `≡ > Preferences > General > [Config Editor...]` button at the very bottom.

Type the full name of the pref which you want to create into the search box: `intl.date_time.pattern_override.date_short` As the pref does not exist, it will show up in the results list as a new pref which you can create by first selecting `(o) String` and then using the the `[+]` button. It will then ask you for a value, and you can enter `yyyy-MM-dd` \(you can always edit the value again later\). Then do the same by analogy for `intl.date_time.pattern_override.time_short`.

### How to change the date/time connector \(e.g. from comma to space\)

You might also want to change that Thunderbird will typically connect date and time with a comma.

First you need to create a preference called `intl.date_time.pattern_override.connector_short`.

The connector preference value must have date and time placeholders in curly brackets.

* Date: `{1}`
* Time: `{0}`
* Strings must be single-quoted to avoid parsing, but some simple characters like space \(```) or comma (``,\`\) work without quoting.
* Apparently the format follows [https://unicode.org/reports/tr35/tr35-dates.html\#Date\_Time\_Combination\_Examples](https://unicode.org/reports/tr35/tr35-dates.html#Date_Time_Combination_Examples)

`intl.date_time.pattern_override.connector_short` = `{1} {0}` \(single space between placeholders\) Result for the short date and short time combination \(as used in message display\): `2021-06-24 21:00`

Regular ASCII characters which you want to display must be single-quoted \(otherwise the date-time display may get truncated\):

`intl.date_time.pattern_override.connector_short` = `{1}'T'{0}`   
Result for the short date and short time combination: `2021-06-24T21:00`

