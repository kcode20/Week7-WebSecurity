# Project 7 - WordPress Pentesting

Time spent: **7** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) User Enumeration in Login

- [x] Summary:
  - Vulnerability types: User Enumeration
  - Tested in version: 4.2
  - Fixed in version: N/A
- [x] GIF Walkthrough:
      <img src='UserEnumeration.gif' title='UserEnumeration' />
- [x] Steps to recreate:
  - Try to login with the username "user" and the password "1234"
  - Take notice to the 'Invalid User' error
  - Try to find a valid user by submitting "admin" as the username and "1234" as the password.
  - Note that the error is not the same, "admin" is a valid username.
  - Try to find the valid password by submitting "admin". You should now be logged into the wordpress admin console.
- [x] Affected source code:
  - [Login Source Code - V4.2](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-login.php)

2. (Required) XSS Vulnerability - Media Page

- [x] Summary:
  - Vulnerability types: XSS
  - Tested in version: 4.2
  - Fixed in version: 4.2.4
- [x] GIF Walkthrough:
      <img src='XSSVulnerability.gif' title='XSSVulnerability' />
- [x] Steps to recreate:
  - Go to the Media tab in Wordpress
  - Select 'Create New'
  - Upload a Picture
  - Click on the newly uploaded Picture
  - In the title field, insert the following: `filename<img src=a onerror=alert('123')>.png`
  - Now select the "View attachment page" button at the bottom of the form
  - When you are redirected to the attachment page, this should trigger the onerror in the image.
- [x] Affected source code:
  - [Media Source Code - V4.2](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-admin/includes/media.php)

3. (Required) XSS Vulnerability - Comment Section

- [x] Summary:
  - Vulnerability types: XSS
  - Tested in version: 4.2
  - Fixed in version: 4.2.4
- [x] GIF Walkthrough:
      <img src='XSSVulnerability2.gif' title='XSSVulnerability2' />
- [x] Steps to recreate:
  - Go to the Comment Section on one of the posts
  - Post: `I can do a lot of bad things here <img src=a onerror=alert('malicious intent')>.png`
  - Select the "Post Comment" button
  - This should trigger the onerror in the image and alert you of "malicious intent"
- [x] Affected source code:
  - [Comments in Themes - V4.2](https://core.trac.wordpress.org/browser/branches/4.2/src/wp-includes/theme.php)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2018] [Khristian Brooks]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
