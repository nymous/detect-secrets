# What's New

Thanks to all our contributors, users, and the many people that make `detect-secrets` possible! :heart:

If you love `detect-secrets`, please star our project on GitHub to show your support! :star:

<!--
# A.B.C
##### MMM DD, YYYY

#### :newspaper: News
#### :mega: Release Highlights
#### :boom: Breaking Changes
#### :tada: New Features
#### :sparkles: Usability
#### :mortar_board: Walkthrough / Help
#### :performing_arts: Performance
#### :telescope: Precision
#### :bug: Bugfixes
#### :snake: Miscellaneous
#### :art: Display Changes

[#xxxx]: https://github.com/Yelp/detect-secrets/pull/xxxx
[@xxxx]: https://github.com/xxxx
-->

### 0.12.0
##### February 11th, 2019

#### :tada: New Features

- Added a `SlackDetector` plugin ([#122], thanks [@killuazhu])
- Added a `--use-all-plugins` argument to `--update` that adds all plugins to the baseline ([#124], thanks [@killuazhu])
- Added `--exclude-files` and `--exclude-lines` arguments to `scan` ([#127])

#### :boom: Breaking Changes

- Removed the `--exclude` CLI scan argument ([#127])

#### :telescope: Precision

- Reduced false-positives by excluding more characters (`!$&\';`) in the `BasicAuthDetector` regex ([#126], [#123], thanks [@killuazhu])
- Added more to the `FALSE_POSITIVES` dict for `KeywordDetector` plugin, **including** `password` ([#118])

#### :bug: Bugfixes

- Fixed a bug where `--update` was adding all plugins to the baseline, instead of respecting the plugins used in the baseline ([#124], thanks [@killuazhu])
- Fixed an uncaught `UnicodeEncodeError` exception when scanning non-ini files (e.g. markdown) containing unicode ([#128], thanks [@killuazhu])
- Fixed a bug where non-ini files (e.g. markdown) containing unicode caused a `UnicodeEncodeError` exception in the `audit` functionality ([#129], thanks [@killuazhu])
- Fixed a bug where non-posix end of line characters caused a "Secret not found on line...." error in the `audit` functionality ([#120], thanks [@killuazhu])
- Fixed a bug where `scan_diff`, called by [`detect-secrets-server`](https://github.com/Yelp/detect-secrets-server), was ignoring inline `pragma: whitelist secret` comments ([#127])

#### :snake: Miscellaneous

- Relaxed the number of spaces before inline `pragma: whitelist secret` comment ([#125], thanks [@killuazhu]]
- Added Python 3.7 to Travis CI and `tox.ini` testing ([#114], thanks [@cclauss])
- [Increased minimum test coverage from 97% to 98%](https://github.com/Yelp/detect-secrets/commit/876b523366057f8c0da14a36e3c972c3e74dfb77)

[#114]: https://github.com/Yelp/detect-secrets/pull/114
[#118]: https://github.com/Yelp/detect-secrets/pull/118
[#120]: https://github.com/Yelp/detect-secrets/pull/120
[#122]: https://github.com/Yelp/detect-secrets/pull/122
[#123]: https://github.com/Yelp/detect-secrets/pull/123
[#124]: https://github.com/Yelp/detect-secrets/pull/124
[#125]: https://github.com/Yelp/detect-secrets/pull/125
[#126]: https://github.com/Yelp/detect-secrets/pull/126
[#127]: https://github.com/Yelp/detect-secrets/pull/127
[#128]: https://github.com/Yelp/detect-secrets/pull/128
[#129]: https://github.com/Yelp/detect-secrets/pull/129
[@cclauss]: https://github.com/cclauss
[@killuazhu]: https://github.com/killuazhu


### 0.11.4
##### January 7th, 2019

#### :bug: Bugfixes
- Fixed a `TypeError` bug introduced in [#111]  ([#116])

[#116]: https://github.com/Yelp/detect-secrets/pull/116


### 0.11.3
##### January 4th, 2019

#### :bug: Bugfixes
- Fixed a bug where we were adding an extra-newline in `detect-secrets scan` output ([#111])

#### :snake: Miscellaneous

- Reorganized the code, mainly creating a `common/` directory ([#113])

[#111]: https://github.com/Yelp/detect-secrets/pull/111
[#113]: https://github.com/Yelp/detect-secrets/pull/113


### 0.11.2
##### January 4th, 2019

#### :telescope: Precision

- [Added `null` to the `FALSE_POSITIVES` tuple for `KeywordDetector` plugin, so we do not alert off of it](https://github.com/Yelp/detect-secrets/commit/58df82ce37d64f22cb885960c2031b5f8ebe4b75)


### 0.11.1
##### January 4th, 2019

#### :tada: New Features

- Turned the `KeywordDetector` plugin back on, with new regexes and accuracy improvements ([#86])
- Added an `AWSAccessKeyDetector` plugin ([#100])
- Added the ability to scan `.ini` types files that do not have a header ([#106])

[#86]: https://github.com/Yelp/detect-secrets/pull/86
[#100]: https://github.com/Yelp/detect-secrets/pull/100
[#106]: https://github.com/Yelp/detect-secrets/pull/106

#### :telescope: Precision

- Add blacklisting of PGP private key headers in `PrivateKeyDetector` plugin ([#104])
- Reduced false-positives by improving `BasicAuthDetector` plugin regex ([#98])

[#104]: https://github.com/Yelp/detect-secrets/pull/104

#### :bug: Bugfixes
- Fixed a bug where we were not showing removed lines in the `audit` functionality ([#98])

[#98]: https://github.com/Yelp/detect-secrets/pull/98

#### :snake: Miscellaneous

- Added whitelist directive regexes to match against inline comment syntaxes in more languages ([#105])
- Refactored various detectors to use `RegexBasedDetector` ([#103])
- Refactored the `BashColor` singleton into the `colorize` function ([#109])
- Small improvements to existing file parsers ([#107])
- Refactored the `BasePlugin` to use the `WHITELIST_REGEX` ([#99])
- Removed `unidiff` from standard dependencies ([#101])

[#99]: https://github.com/Yelp/detect-secrets/pull/99
[#101]: https://github.com/Yelp/detect-secrets/pull/101
[#103]: https://github.com/Yelp/detect-secrets/pull/103
[#105]: https://github.com/Yelp/detect-secrets/pull/105
[#107]: https://github.com/Yelp/detect-secrets/pull/107
[#109]: https://github.com/Yelp/detect-secrets/pull/109


### 0.11.0
##### November 26th, 2018

#### :tada: New Features

- Made the pre-commit hook automatically update the baseline ([#96])
- Added the `audit --diff` functionality ([#95])

[#95]: https://github.com/Yelp/detect-secrets/pull/95
[#96]: https://github.com/Yelp/detect-secrets/pull/96

#### :art: Display Changes

- Added display of secret type in audit functionality ([#94])

[#94]: https://github.com/Yelp/detect-secrets/pull/94


### 0.10.5
##### October 30th, 2018

#### :art: Display Changes

- Added a "Please git add the baseline" message ([#89])
- Improved the "Unable to open baseline file" message ([#91])

[#91]: https://github.com/Yelp/detect-secrets/pull/91

#### :bug: Bugfixes

- Update `scan --update` results to only propagate `is_secret` of new secrets  ([#90])

[#90]: https://github.com/Yelp/detect-secrets/pull/90


### 0.10.4
##### October 23rd, 2018

#### :boom: Breaking Changes
- Disabled `KeywordDetector` plugin temporarily ([#89])

#### :art: Display Changes

- Ordered baseline hashes, for better diffs ([#84])
- Added a "Please git add the baseline" message ([#89])
- Improved error messages for pre-commit hook ([#85])

[#84]: https://github.com/Yelp/detect-secrets/pull/84
[#89]: https://github.com/Yelp/detect-secrets/pull/89
[#85]: https://github.com/Yelp/detect-secrets/pull/85

#### :bug: Bugfixes

- Fixed a couple bugs in the `audit` functionality, one for small files and the other case-sensitivity in the `KeywordDetector` plugin ([#83], thanks [@jkozera])

[#83]: https://github.com/Yelp/detect-secrets/pull/83
[@jkozera]: https://github.com/jkozera


### 0.10.3
##### October 4th, 2018

#### :tada: New Features

- Added a `KeywordDetector` plugin, that was horrible and regretful ([#76])

#### :bug: Bugfixes

- Fixed a bug in `scan --update` where we would append the baseline exclude regex to itself ([#78])
- Fixed the regular expression in the `BasicAuthDetector` plugin so that it didn't run forever ([#80])
- Removed trailing whitespace from `scan` output ([#78])

#### :snake: Miscellaneous

- Added command line hints and baseline clarification in the README ([#81], thanks [@JoshuaRLi])

[#76]: https://github.com/Yelp/detect-secrets/pull/76
[#78]: https://github.com/Yelp/detect-secrets/pull/78
[#80]: https://github.com/Yelp/detect-secrets/pull/80
[#81]: https://github.com/Yelp/detect-secrets/pull/81

[@JoshuaRLi]: https://github.com/JoshuaRLi


### 0.10.2
##### September 12th, 2018

#### :tada: New Features

- Added a (b)ack option to 'Is this a valid secret?' ([#72], thanks [@cleborys])
- Added a `BasicAuthDetector` plugin ([#74])
- Added CLI functionality to check strings in an adhoc manner ([#73])

#### :bug: Bugfixes

- Added a check to only load json from stdin if it exists ([#69], thanks [@guykisel])

#### :snake: Miscellaneous

- Fixed a typo in the README ([#68], thanks [@whathejoe])

### 0.10.1
##### August 1st, 2018

#### :bug: Bugfixes

- Fixed a bug where we didn't skip sequential strings when we should have ([#67])

[#67]: https://github.com/Yelp/detect-secrets/pull/67


### 0.10.0
##### August 1st, 2018

#### :tada: New Features

- Scan `--all-files` option ([#57])
- Yaml inline whitelisting support ([#50])

#### :boom: Breaking Changes

- Changed `--audit` and `--scan` to `audit` and `scan` ([#51])
- Changed `scan --import <baseline>` to `scan --update <baseline>` ([#58])

#### :telescope: Precision

- Reduced false-positives caused by sequential strings, e.g. `ABCDEF` ([#64])

#### :bug: Bugfixes

- Fixed a bug where the pre-commit code would remove the `is_secret` attribute from
  audited baselines ([#65])
- Fixed an `audit` bug where we would crash if a file in the baseline did not exist
  ([#56])
- Improved the `audit` functionality to handle short files better ([#48])


[#48]: https://github.com/Yelp/detect-secrets/pull/48
[#50]: https://github.com/Yelp/detect-secrets/pull/50
[#51]: https://github.com/Yelp/detect-secrets/pull/51
[#56]: https://github.com/Yelp/detect-secrets/pull/56
[#57]: https://github.com/Yelp/detect-secrets/pull/57
[#58]: https://github.com/Yelp/detect-secrets/pull/58
[#64]: https://github.com/Yelp/detect-secrets/pull/64
[#65]: https://github.com/Yelp/detect-secrets/pull/65

[#68]: https://github.com/Yelp/detect-secrets/pull/68
[#69]: https://github.com/Yelp/detect-secrets/pull/69
[#72]: https://github.com/Yelp/detect-secrets/pull/72
[#73]: https://github.com/Yelp/detect-secrets/pull/73
[#74]: https://github.com/Yelp/detect-secrets/pull/74

[@cleborys]: https://github.com/cleborys
[@guykisel]: https://github.com/guykisel
[@whathejoe]: https://github.com/whathejoe


### 0.9.1
##### June 28th, 2018

#### :bug: Bugfixes

- Fixed numbering system with interactive audit
- Fixed "leapfrog" edge case for audit functionality ([#47])


[#47]: https://github.com/Yelp/detect-secrets/pull/47


### 0.9.0
##### June 27th, 2018

#### :tada: New Features

- Added ability to migrate baselines from an older version to a newer version
- Added functionality to audit baseline, to distinguish difference between
  false and true positives in the baseline file ([#44])
- Upgraded `PrivateKeyPlugin`: more search parameters, more lines searched,
  and secret hash created using payload (rather than the entire line content)

#### :boom: Breaking Changes

- Differentiate between `Base64HighEntropyStrings` and `HexHighEntropyStrings` through
  `secret_type` ([#26])
- Got rid of `SensitivityValues` as a means to store plugin configs

#### :telescope: Precision

- Improved the heuristic for `HexHighEntropyStrings`, reducing the false positive rates
  for large numbers identified in code

#### :bug: Bugfixes

- Baseline always outputs in sorted order now, to prevent unnecessary diffs ([#25])
- Escape exclude regex statements before compilation ([#39])
- Fixed case where details of plugins used were not included in the baseline,
  when the pre-commit hook updated it ([#40])

#### :snake: Miscellaneous

- Simplified logging by removing `CustomLog` ([#46])


[#25]: https://github.com/Yelp/detect-secrets/pull/25
[#26]: https://github.com/Yelp/detect-secrets/pull/26
[#39]: https://github.com/Yelp/detect-secrets/pull/39
[#40]: https://github.com/Yelp/detect-secrets/pull/40
[#44]: https://github.com/Yelp/detect-secrets/pull/44
[#46]: https://github.com/Yelp/detect-secrets/pull/46


### Before 0.9.0

#### :tada: New Features

- Allow scanning of non-git files ([#18])

#### :telescope: Precision

- Improved scanning of INI config files with `HighEntropyString` ([#13], [#17])
- Improved scanning of YAML files with `HighEntropyString` ([#16])

#### :bug: Bugfixes

- Fixed `PrivateKeyDetector` plugin analyze results' representation ([#15])

[#13]: https://github.com/Yelp/detect-secrets/pull/13
[#15]: https://github.com/Yelp/detect-secrets/pull/15
[#16]: https://github.com/Yelp/detect-secrets/pull/16
[#17]: https://github.com/Yelp/detect-secrets/pull/17
[#18]: https://github.com/Yelp/detect-secrets/pull/18
