# Project 7 - WordPress Pentesting

Time spent: **16** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
  - [X] Summary: Using the Youtube URL embed shortcode, a XSS attack could be made by inserting a script within a youtube url. This works because although characters such as backslash are filtered out using the HTML sanitzation function wp_kses(), it does not consider escape sequences such as \x3c or \x3c, which correspond to < and >, respectively.
    - Vulnerability types: XSS
    - Tested in version: 4.2.2
    - Fixed in version: 4.2.13
  - [X] GIF Walkthrough: <img src='http://i.imgur.com/ihzKndD.gif' title='Exploit1' width='' alt='Exploit1' />
  - [X] Steps to recreate: Log in as a user with atleast contributor permissions. Create a new post, then put in some url embed shortcode with any youtube video link. At the end of the youtube video link, insert the escape code sequence \x3c (<) followed by your xss code, ended with \x3e (>). Then post it and view the post's link. 
  - [X] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/changeset/40160/trunk/src/wp-includes/embed.php?old=38361&old_path=trunk%2Fsrc%2Fwp-includes%2Fembed.php)
1. (Required) Authenticated Shortcode Tags Cross-Site Scripting (XSS)
  - [X] Summary: By abusing unclosed HTML elements used within shortcode tags, a hacker could perform an XSS attack by inserting some script within the tag itself.
    - Vulnerability types: XSS
    - Tested in version: 4.2.2
    - Fixed in version: 4.2.5
  - [X] GIF Walkthrough: <img src='http://i.imgur.com/iphTk5m.gif' title='Exploit2' width='' alt='Exploit2' />
  - [X] Steps to recreate: Create a new page or post and add the following to the body: 
`Link[caption width="1" caption='<a href="' ">]</a><a href="http://onMouseOver='alert(1)'">HOVER OVER ME</a>>`
  - [X] Affected source code:
    - [Link 1](http://blog.checkpoint.com/2015/09/15/finding-vulnerabilities-in-core-wordpress-a-bug-hunters-trilogy-part-iii-ultimatum/)
1. (Required) Authenticated Stored Cross-Site Scripting (XSS)
  - [X] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2.2
    - Fixed in version: 4.2.3
  - [X] GIF Walkthrough: <img src='http://i.imgur.com/mkNbBnJ.gif' title='Exploit3' width='' alt='Exploit3' />
  - [X] Steps to recreate: Create a new page or post and add the following to the body: 
`<a href="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>`
  - [X] Affected source code:
    - [Link 1](https://klikki.fi/adv/wordpress3.html)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

Trying to find exploits with written out proof of concepts and explanations was hard.

## License

    Copyright 2017 Kenichi Yamamoto

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
