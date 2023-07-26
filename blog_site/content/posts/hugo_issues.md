---
title: "Hugo Template Issues"
date: 2023-07-26
descripton: "A blog post for serving as documentation for troubleshooting issues observed while using Hugo with Hugo Winston Theme by Zerostatic Themes"
tags:
    - others
---


## 사이트 깨짐 (e.g. Home 페이지)
---
- resources folder delete (save copy as backup)  
- re-add resources folder  
  
Probable reason:  
1. site generator problems (theme site generator generates resource folder)  
2. Hugo theme problem  
3. GitHub Pages reading problem

<br>

## 404 Not Found
---
- due to editing `themes/assets/_content.scss`

Initial Solution (Succeeded then Failed)
- copy assets folder to path outside of themes folder (i.e. copy to website root folder)  
- edit those assets (not assets in themes folder)

- after adding .md (Day3&4)  
- deleted then re-added resources folder, then commit and push empty commit "trigger rebuild --> FAIL

<br>

## 404 Not Found - SOLUTION (FINAL)
---
#### Research
"hugo template working on hugo server but 404 not found on github pages" - Google Search Keyword

#### Ref 1.
Hugo site starts locally, only displays 404 on hosted GH page
https://stackoverflow.com/questions/56623432/hugo-site-starts-locally-only-displays-404-on-hosted-gh-page

"Meaning what you should be pushing if, from your `public` subfolder, only what Hugo has generated.

You should _not_ push your Hugo project (`config.toml`, `themes`, and so on): those should be pushed in a separate GitHub repository for safekeeping and versionning."

==**IDEA. Need to separate content and .toml, themes folder. Must only push project and not Hugo essential files to deployment.**==

#### Ref 2.

Github action deploy development branch to subdir of master bracnh
https://stackoverflow.com/questions/72857383/github-action-deploy-development-branch-to-subdir-of-master-bracnh/73311701#73311701

>" Considering that "[GitHub Pages now uses Actions by default](https://github.blog/2022-08-10-github-pages-now-uses-actions-by-default/)" "
>
>With the shift to GitHub Actions, GitHub Pages are now tracking deployments instead of builds.
>
>A source branch is not required anymore and is at the discretion of a workflow’s triggers.  We’ve made it so a deployment must happen in the context of an environment (`github-pages` by default).

==**IDEA. No need to define workflow into .yaml file**==



#### Method

- backup files to another folder then delete from github.io local folder, commit and push changes to repo  
- create README.md on github.io repo (optional - need at least one commit in github.io repo)  
- create new blog repo, git clone to local folder (blog_files)  
- hugo new site (blog_site) to blog local folder, add posts to blog local folder, edit or copy existing hugo.toml for blog configuration  
- open hugo site folder (blog_site), git submodule add theme repo to blog_site/themes  
- add assets/scss/_content.scss to local blog folder (after editing code block color)  
- test via hugo server  
- git submodule add -b main [github.io repo .git link] public -- connect github.io repo to public folder, push from public folder will add changes to github.io repo  
- do hugo -t [theme_name] -- adds theme files to public folder  
- open public folder then commit and push changes


`NOTE. Did not add .github/workflow/hugo.yaml and let github actions deploy automatically.`


#### Ref. Method

Creating a Blog with Hugo and Github in 10 minutes by [Ryan Schachte](https://www.youtube.com/@TheSimpleEngineer)
https://www.youtube.com/watch?v=LIFvgrRxdt4



