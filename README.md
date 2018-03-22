# Project 7 - WordPress Pentesting

Time spent: 7 hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. User Enumeration
  - [X] Summary: Observed WordPress logon at http://WPDistillery/wp-admin/ allows for users to be enumerated by passing various usernames during login.  
    - Vulnerability types: User Enumeration
    - Tested in version: 4.3
    - Fixed in version: Not corrected due to severity disputed by WordPress
  - [X] GIF Walkthrough: ![](https://github.com/Shaimice/WordPress/blob/master/UserEnumeration.gif)
  - [X] Steps to recreate:
    - Navigate to http://WPDistillery.vm/wp-login.php
    - Attempt user enumeration by placing Admin in Username
    - Use any generic password
    - Website responds with "ERROR: The password you entered for the username admin is incorrect. Lost your password?"
  - [X] Affected source code:
    - [wp-login.php](https://core.trac.wordpress.org/browser/branches/4.3/src/wp-login.php)

2. Cross Site Scripting Media File
  - [X] Summary:
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: 4.3
    - Fixed in version: 4.6.1.
  - [X] GIF Walkthrough: ![](https://github.com/Shaimice/WordPress/blob/master/XSSMedia.gif)
  - [X] Steps to recreate:
    - Initiated an image upload using a .jpg file on http://WPDistillery
    - Appended the XSS to the image title: <img src=a ONERROR=alert('GetOut')>
    - In viewing the image an alert is thrown with the corresponding alert
  - [X] Affected source code:
    - [upload.php](https://core.trac.wordpress.org/browser/branches/4.3/src/wp-admin/upload.php)

3. Cross Site Scripting of Doctor Booking Plugin
  - [X] Summary: Sought to exploit a reported vulnerability located in the Doctor Appointment Booking (DAB) Plugin of WordPress. Vulnerability reported 1 Feb 2018 in packet storm.
    - Vulnerability types: Cross Site Scripting (XSS)
    - Tested in version: WP 4.2 | DAB 1.0
    - Fixed in version: Unresolved
  - [X] GIF Walkthrough:![](https://github.com/Shaimice/WordPress/blob/master/DrXSS.gif)
  - [X] Steps to recreate:
    - Login to http://WPDistillery/wp-admin.php.
    - Select Plugins on the menu and Add New
    - Enter "Doctor" in Search Plugins field and select Install Now
    - Enable the use of the the plugin by selecting Activate
    - Select the Doctor Chamber on the menu and select Patient
    - Click on + Add Patient
      - Enter the java script string under Name: john doejaVasCript:/*-/*`/*\\`/*\'/*\"/**/(/* */oNcliCk=alert(12345) ).
      - Enter the patient's email address and telephone number.
      - Save the record.
    - Select Edit to edit the patient record and when the mouse is selected (onclick) the alert window appears.
  - [X] Affected source code:
    - [DBA](https://codecanyon.net/item/doctor-appointment-booking-wordpress-plugin/21215314)

4. Privileged Escalation
  - [ ] Summary: WordPress allows for remote authenticated users to publish posts by leveraging the Contributor role, related to wp-admin/includes/post.php and wp-admin/includes/class-wp-posts-list-table.php.  A user with a contributor role can publish posts, which are reserved for users of the next-higher role.
    - Vulnerability types: Privilege Escalation
    - Tested in version: 3.8.1
    - Fixed in version: 3.8.2
  - [ ] GIF Walkthrough:
  - [ ] Steps to recreate:
    - Login to http://WPDistillery/wp-admin/
    - Create user account and assign the role of Contributor
    - Logoff as Admin and login under new account with Contributor permissions
    - Navigate to Posts
  - [ ] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/tags/version/src/source_file.php)

5. (Optional) Vulnerability Name or ID
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
- [WPScan Vulnerability Database](https://wpvulndb.com/)
- [Packet Storm Security](https://packetstormsecurity.com/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2018] [S. D. Somavia]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
