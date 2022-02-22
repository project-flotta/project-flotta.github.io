# animated-dollop

This template is based on jekyll, a static website generator. This template can be used to quickly setup a website, features include:

- Responsive layout
- Custom colors with variables 
- Responsive nav bar
- Easy documentation tab
- Search tab to filter blogs/posts
- Social media widgets

## Get Started 

### To run the template you need install Ruby,Bundler and Jekyll

1. Install Ruby & Bundler (as root):

   _Note: To become root, you must either run `su` or `sudo -s`_

   * **Fedora** / **RHEL** / **CentOS**:
     ```
     dnf install -y rubygem-bundler ruby-devel libffi-devel make gcc gcc-c++ \
     redhat-rpm-config zlib-devel libxml2-devel libxslt-devel tar nodejs
     ```
  
   * **Debian** / **Ubuntu**:
     ```
     apt update && apt install bundler zlib1g-dev
     ```

   * **macOS** / **OS X**:
   
     _Note: First, you must install Mac developer tools. Then, run the following:_
     
     ```
     gem update --system
     gem install bundler
     ```

2. Install gems (as user):
   ```
   bundle install
   ```

3. Run Jekyll:
   ```
   bundle exec jekyll server
   ```
## Work with the Site

As this site scaffolding is built on Jekyll, most all Jekyll documentation applies.

Useful references:
- [the official Jekyll documentation](http://jekyllrb.com/docs/home/)
- [CloudCannon Jekyll tutorials](https://learn.cloudcannon.com/)

### Posts

All the released notes and documentation are in the form of markdown files and can be found in `_posts` and `/documentation/files`

### Frontmatter

Each blog post will have a fronmatter which defines the properties of the post like title, author, date, etc., without which Jekyll will not process the blog posts.
```
---
layout: post
title:  "Welcome to Jekyll!"
date:   2021-08-10 11:44:17 -0400
categories: test 
author: dinesh
summary-1: Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod

---
```
More post frontmatter variables can be found in Jekyll official documentation - [the official Jekyll documentation](http://jekyllrb.com/docs/home/)
   
   
## Styling

Styling is simple, this template uses SCSS and the files can be found in `/assets`
All the colors for Navbar, footer etc are defined in `/assets/variables.scss` - here the colors can be customized accordignly 

## Responsive Layout

This template is responsive on default setting,to change the behavior of website based on the screen size - in `/assets/` all the individual .scss files will have 
```
@mixin large {
  @media screen and (min-width: #{$large-breakpoint}) {
    @content;
  }
}

@mixin medium {
  @media screen and (min-width: #{$medium-breakpoint}) and (max-width: #{$large-breakpoint}) {
    @content;
  }
}

@mixin small {
  @media screen and (max-width: #{$medium-breakpoint}) {
    @content;
  }
}
```
The above css elements will define the behavior of each screen size. Large will define breakpoint for PCs, Medium for Tablet, and Small for Mobile devices.
An example for responsive css element can be found below 
```
.page-header {
  position: fixed;
  width: 100%;
  color: $header-heading-color;
  text-align: center;
  background-color: $header-bg-color;
  //background-image: linear-gradient(120deg, $header-bg-color-secondary, $header-bg-color);

  @include large {
    padding: 5rem 6rem;
  }

  @include medium {
    padding: 3rem 4rem;
  }

  @include small {
    padding: 2rem 1rem;
  }
}
```
## Calendar 

Calendar can be found in the events tab in the website, code and logic can be found in `calendar.md` file. 
Calendar used in the template is from Toast UI Calendar plugin - [More resources on TUI Calendar] (https://ui.toast.com/tui-calendar)

### Add event 

To add event, 
- Go to `/meetings-meetups/_posts`
- Create a .md file with this naming convention `YYYY-MM-DD-your-title.md`
- In the .md file, add the following frontmatter with edited values
   ```
   ---
   layout: redirect
   redirect: Meeting link
   date-start: "2021-12-09 17:00"
   date-end: "2021-12-12 19:00"
   location: "Location"
   title: "Fest"
   hidden: true
   ---
   ```
- All the detials can be edited except **hidden: true**, which prevents the .md file from appearing in blog posts  
- To add a recurring event
  ```
  ---
  layout: redirect
  redirect: https://enterlink
  date-start: "2021-12-16 17:00"
  date-end: "2021-12-16 19:00"
  location: "Enter location"
  title: "Event1"
  rrule: "FREQ=MONTHLY;UNTIL=20220423T190000"
  hidden: true
  ---
  ```
- Add `rrule: "FREQ=MONTHLY;UNTIL=20220423T190000"`  FREQ can be `WEEKLY` or `MONTHLY` and UNTIL should determine the end of the event in `YYYYMMDDT1HHMMSS`
