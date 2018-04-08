# Project 7 - WordPress Pentesting

Time spent: **2** hours spent in total

> Objective: Find, analyze, recreate, and document **three vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. WordPress <= 4.2 - Unauthenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2 
    - Fixed in version: 4.2.15
  - [ ] GIF Walkthrough: 
    - <img src="CommentXSS.gif" width="800">
  - [ ] Steps to recreate: 
    - Make a comment on a page that has at least 64KB of content, for example: 
    
    - `<a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a>`
    
  - [ ] Affected source code:
    - [Not the actual source code, but describes the vulnerability](https://klikki.fi/adv/wordpress2.html) 
2. WordPress 3.3-4.7.4 - Large File Upload Error XSS
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: 
    - <img src="LargeFileXSS.gif" width="800">
  - [ ] Steps to recreate: 
    - Upload a large file, atleast 100MB in size that has the desired payload as the file name, such as:
    - `Somefile<img src=x onerror=alert(“Vulnerability!”)>.png`.
  - [ ] Affected source code:
    - [Github Link](https://github.com/WordPress/WordPress/commit/8c7ea71edbbffca5d9766b7bea7c7f3722ffafa6)
3. WordPress < 4.2.3 Stored XSS
  - [ ] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: 
    - <img src="PageXSS.gif" width="800">
  - [ ] Steps to recreate: 
    - Requires you to be able to create pages, create a link like: 
    - `<a href=“[caption code=“>]</a><a title=“ onmouseover=alert(‘test’) “>link</a>`
    - Wordpress shortcode processing will turn this into 
    - `<a href="</a><a title=" onmouseover=alert('test')  ">link</a>`.
  - [ ] Affected source code:
    - [Not the actual source code, but describes the vulnerability](https://klikki.fi/adv/wordpress3.html)


## Assets

https://klikki.fi/adv/wordpress2.html
https://klikki.fi/adv/wordpress3.html

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [2018] [Joshua Kim]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
