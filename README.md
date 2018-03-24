# Project 7 - WordPress Pentesting

Time spent: 14 hours spent in total

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
    - [DBA plugin](https://codecanyon.net/item/doctor-appointment-booking-wordpress-plugin/21215314)

4. SQL Injection of WordPress Events Plugin
  - [X] Summary: WordPress Events plugin version 2.3. allows remote attackers to execute arbitrary SQL commands via the wp-events-edit & edit_event line.
    - Vulnerability types: SQL Injection
    - Tested in version: WP 4.3 | Events 2.3
    - Fixed in version: Has not been corrected in current version 2.3.4
  - [X] GIF Walkthrough: ![](https://github.com/Shaimice/WordPress/blob/master/SQLIEvents.gif)
  - [X] Steps to recreate:
    - Login to http://WPDistillery/wp-admin/
    - Install WordPress Events plugin version <=2.3.4.
    - On the web browser address line enter: http://WPDistillery.vm/wp-admin/admin.php?page=wp-events-edit&edit_event=2+UNION+SELECT+1,CONCAT(user_login,char(58),user_pass),3,4,5,6,7,8,9,10,11,12,13,14+FROM+wp_users+WHERE+ID=1
    - WordPress Events plugin generates a new browser tab that has information from the wp_users table associated with the administrator's profile (ID=1)
  - [X] Affected source code:
    - [WP Events plugin](https://ajdg.solutions/?pk_campaign=plugin-url)

5. SQL Injection of WordPress Jobs Plugin
  - [X] Summary: WordPress Jobs plugin version 1.4 possesses a SQL injection vulnerability which allows authenticated users to execute arbitrary SQL commands via the jobid parameter to wp-admin/edit.php.
    - Vulnerability types: SQL Injection
    - Tested in version: WP 4.3 | Jobs 1.4
    - Fixed in version: Jobs 1.5
  - [X] GIF Walkthrough: ![](https://github.com/Shaimice/WordPress/blob/master/SQLIJobs.gif)
  - [X] Steps to recreate:
    - Login to http://WPDistillery/wp-admin/
    - Install WordPress Jobs plugin version <=1.4
    - On the web browser address line enter: http://wpdistillery.vm/wp-admin/edit.php?post_type=job&page=WPJobsJobApps&jobid=1+UNION+ALL+SELECT+NULL%2CNULL%2CNULL%2C%40%40version%2CNULL%2CNULL
    - WordPress Jobs plugin reveals the database version in the Email field
  - [ ] Affected source code:
    - [WP Jobs plugin](https://wordpress.org/plugins/wp-job-manager/)

## Assets

No additional assets, such as scripts or files were used during this exercise

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)
- [WPScan Vulnerability Database](https://wpvulndb.com/)
- [Packet Storm Security](https://packetstormsecurity.com/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Locating plugins that fell under the upload threshold requirements of php.ini was a challenge.  Those that exceeded the threshold resulted in an error being returned as follows:  The uploaded file exceeds the upload_max_filesize directive in php.ini.

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
