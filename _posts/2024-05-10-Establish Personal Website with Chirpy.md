---
title: Establish Personal Website with Chirpy
description: Establish Personal Website with Chirpy
author: Qingspring
date: 2024-05-10
categories: [Blogging, tutorial]
tags: [tutorial]
pin: true
math: true
mermaid: true
---
## Create new repository
- Establish a new repository with following template
https://github.com/cotes2020/chirpy-starter
- Rame the new repository:
name the new repository USERNAME.github.io, where USERNAME represents your GitHub username.

## Config the file _config.yml
Update the variables of _config.yml as needed. Some of them are typical options:
- url
- avatar
- timezone
- lang

## Generate logo
- Generate your personal logo with a Text-to-Image model or Product, such as MetaAI: https://www.meta.ai/
- Customize the Favicon following the tutorial: https://chirpy.cotes.page/posts/customize-the-favicon/
- Upload the Favicon to the repository directory: /assets/img/favicons
- Upload the logo to the repository directory: /assets/avatar, and config the _config.yml file as avatar: /assets/avatar/logo.jpeg
- caution for the space after ":"
  
## Deploy
- Configure the Pages service.

- Browse to your repository on GitHub. Select the tab Settings, then click Pages in the left navigation bar. Then, in the Source section (under Build and deployment), select GitHub Actions from the dropdown menu.
Push any commits to GitHub to trigger the Actions workflow. In the Actions tab of your repository, you should see the workflow Build and Deploy running. Once the build is complete and successful, the site will be deployed automatically.

- At this point, you can go to the URL indicated by GitHub to access your site.

## Reference
- Jekyllthemes website: http://jekyllthemes.org
- Good Chinese tutorial: https://thesocialnetworkinbox.github.io/Tutorial
- Chirpy documents: 
https://chirpy.cotes.page/
