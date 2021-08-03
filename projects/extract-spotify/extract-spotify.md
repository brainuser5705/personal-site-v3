---
layout: page
title: Extract Spotify
permalink: /extract-spotify/
---

_**[View the project on Github](https://github.com/brainuser5705/extract-spotify)**_

#### **Try it out**
Here is the [website](https://extract-spotify.herokuapp.com/app).    
*Note*: The website will take a website to load because I am hosting with a free dyno on Heroku.    
---   
**Instructions**
1. *Download your Spotify data. In a few days/weeks, Spotify will email you a .zip file with a JSON of your streaming history (ex. StreamingHistory01.json).*
2. *Upload either the entire .zip file or JSON file into Extract Spotify (better to send JSON file).*
3. *View your visualizations!*

#### **Release Notes**
*Version 1.0 (2021-02-19)*
- As of now, Extract Spotify is a standalone bokeh server hosted with Heroku. Users have to download their Spotify data first, and then uploading it to the server which will display a timeline for when you listened to a particular artist or song and the corresponding stream minutes for that day.

- Future plans will be to use the Spotify API so users don't have to download any sensitive data and can directly log in with Spotify. It will also allow for more statistics and data to work with.

#### **Screen Captures**
![](https://i.imgur.com/GAkEkKe.png)
*This is what the interface looks like.*