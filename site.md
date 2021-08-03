---
layout: page
title: Personal Website
permalink: /site/
--- 

Over the past year, I have been developing my personal website and gone through several iterations while I experimented with different web development technologies. Here is a visual timeline of the landing page of my website. I will also include some notes about the features, the languages/technologies I used, and the general development process for each version.

---

## (V1) Github Pages Static HTML and CSS
 
 [_*Visit the site*_](https://brainuser5705.github.io/website/)

![](https://i.imgur.com/QCN9UMQ.png)

**Languages/Technologies/Tools**
- HTML/CSS
- Github Pages

**Features**
- A static site with very crude HTML and CSS
- Features a blog page, but I never updated it (at this time, I wasn't aware of Jekyll)
- Largely inspired by [bgreco](https://bgreco.net)'s page

**Development Process**  
Nothing special, it's front end HTML and CSS.

---

## (V2) Django Web Application

[_*Visit the site*_](https://brainuser5705-website.herokuapp.com/)

![](https://i.imgur.com/OugkFVs.png)

**Languages/Technologies**
- HTML/CSS, Python
- Django framework
- Heroku (for hosting) with PostgreSQL addon

**Features**
- Status updates and updatable personal stats
- Includes a database where I can store all the data
- Admin page for easy data insertion (posting status updates, links, etc.)
- More refined frontend design

**Development Process**  
I had experience with the Django framework for a now defuncted project and wanted to use a database to store my site's content. I worked on this for about a month or so.

---

## (V3) LAMP stack

[_*Visit the site*_](https://ashleyliew-prod.herokuapp.com/)

![](https://i.imgur.com/dxjEZNf.png)

**Languages/Technologies**
- HTML/CSS, PHP
- Heroku with PostgreSQL

**Features**
- Formatted status updates and can support links, images
- Automated processes for data insertion [(had to remove this after hosting with Heroku)](https://ashleyliew-prod.herokuapp.com/blog/How-My-Website-Works-(PHP)/)
- Own domain (removed for new version)

**Development Process**  
My intentions of creating this version was to create a website "from scratch", using pure HTML/CSS and PHP. I came across the LAMP technology stack and started researching. Before starting, I had to learn PHP and re-learn SQL. I used XAMPP as a development environment with its built-in Apache and MariaDB. After that, I tried hosting it on my own Linux machine, but switched to Heroku. With Heroku hosting, I had to substantially change the backend design of my website including reworking file upload processes intended for my projects and blogs. You can read more about it in the link provided under Features. 

---

## (V4, *Current version*) Jekyll Site

![](https://i.imgur.com/hF062eS.png)

**Languages/Technologies**
- Jekyll
- Github Pages

**Features**
- Using Jekyll templates instead of creating from scratch
- Jekyll blogging system
- Large of use of Markdown for writing (as of now)
- No backend or database

**Development Process**  
The backend of the previous version was very insecure and inefficient. After multiple tweaks and fixes, it ended up like a static site that didn't need a database at all. I wanted to use Jekyll's "blog awareness" feature, clean file structure and easy workflow (at least compared to my LAMP stack), so I switched over. After a few hours of research and a full night of rewriting content, the site is up and hosting with Github Pages. Majority of the activity of my website lies in [status updates](https://status.ashleyliew.com), so to keep it I modified the LAMP stack to only be for status updates. As for blogging, it will be done on this site with Jekyll. 

