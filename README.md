# Project 7 - WordPress Pentesting

Time spent: 7 hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. User Enumeration
  - [ ] Summary:
    - Vulnerability types: User Enumeration
    - Tested in version: 4.3
    - Fixed in version: Not corrected due to severity disputed by WordPress
  - [ ] GIF Walkthrough: ![](my_gif_walkthrough_url)
  - [ ] Steps to recreate:
    - Navigate to http://WPDistillery.vm/wp-login.php
    - Attempt user enumeration by placing Admin in Username
    - Use any generic password
    - Website responds with "ERROR: The password you entered for the username admin is incorrect. Lost your password?"
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/branches/4.3/src/wp-login.php)
1. (Required) Vulnerability Name or ID
  - [ ] Summary:
    - Vulnerability types:
    - Tested in version:
    - Fixed in version:
  - [ ] GIF Walkthrough:
  - [ ] Steps to recreate:
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
1. (Required) Vulnerability Name or ID
  - [ ] Summary:
    - Vulnerability types:
    - Tested in version:
    - Fixed in version:
  - [ ] GIF Walkthrough:
  - [ ] Steps to recreate:
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
1. (Optional) Vulnerability Name or ID
  - [ ] Summary:
    - Vulnerability types:
    - Tested in version:
    - Fixed in version:
  - [ ] GIF Walkthrough:
  - [ ] Steps to recreate:
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)
1. (Optional) Vulnerability Name or ID
  - [ ] Summary:
    - Vulnerability types:
    - Tested in version:
    - Fixed in version:
  - [ ] GIF Walkthrough:
  - [ ] Steps to recreate:
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2018] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
