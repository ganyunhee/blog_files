---
title: "Hugo Installation & GitHub Pages Theme Setting"
date: 2023-07-19
descripton: "A blog post for documenting the installation of Hugo on Windows 11 and setting up a Hugo theme for GitHub Pages."
tags:
    - others
---

A blog post for documenting the installation of Hugo on Windows 11 and setting up a Hugo theme for GitHub Pages.

ref. https://www.youtube.com/watch?v=psyz4UPnGAA . https://gohugo.io/getting-started/quick-start/ .

--- 
## Prerequisites

#### - Git
	- required to build Hugo from source
	- required to use hugo Modules feature
	- required to install a theme as a Git submodule
	- required to access commit information from local Git repo
	- required to host site (for GitHub Pages, GitLab Pages, Netlify, etc.)
#### -  Go
	- required to build Hugo from source
	- required to use Hugo Modules feature
#### - Dart Sass
	- used to transpile Sass to CSS
	- install to use latest features of Hugo
	- compatible with Hugo v0.114.0 and later
#### - Chocolatey
	- Package Manager for Windows
	- used to install Hugo, Dart Sass

---

<br>

## Check GIT version

![](/posts/posts_images/hugo_install/git1.png)

<br>

## Install Go

https://go.dev/doc/install

![](/posts/posts_images/hugo_install/go1.png)
![](/posts/posts_images/hugo_install/go2.png)
![](/posts/posts_images/hugo_install/go3.png)
![](/posts/posts_images/hugo_install/go4.png)
![](/posts/posts_images/hugo_install/go5.png)
![](/posts/posts_images/hugo_install/go6.png)
![](/posts/posts_images/hugo_install/go7.png)
![](/posts/posts_images/hugo_install/go8.png)

<br>

## Install Chocolatey PM

https://chocolatey.org/install

![](/posts/posts_images/hugo_install/choco1.png)
Open PowerShell as admin

Run `Get-ExecutionPolicy`. If it returns `Restricted`, run `Set-ExecutionPolicy AllSigned` or `Set-ExecutionPolicy Bypass -Scope Process`

![](/posts/posts_images/hugo_install/choco2.png)
![](/posts/posts_images/hugo_install/choco3.png)
![](/posts/posts_images/hugo_install/choco4.png)

Run following command

```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

![](/posts/posts_images/hugo_install/choco5.png)

Restart powershell (as admin). 
Type `choco` (if installed, shows installed version) or `choco -?` (shows instructions).

![](/posts/posts_images/hugo_install/choco6.png)

<br>

## Install Dart Sass via Chocolatey

https://gohugo.io/hugo-pipes/transpile-sass-to-css/#dart-sass
https://community.chocolatey.org/packages/sass

```
choco install sass
```

![](/posts/posts_images/hugo_install/dart1.png)

<br>

## Install Hugo via Chocolatey


Install Hugo (Extended edition)

https://gohugo.io/installation/windows/
https://community.chocolatey.org/packages/hugo-extended

```
choco install hugo-extended
```


![](/posts/posts_images/hugo_install/hugo1.png)

Check hugo version

```
hugo version
```

![](/posts/posts_images/hugo_install/hugo2.png)

Go to directory where files will be saved.

```
hugo new site blog
```

![](/posts/posts_images/hugo_install/hugo3.png)

```
cd [hugo_blog_folder_name]
```

Start server. Check website contents.

```
hugo server
```

![](/posts/posts_images/hugo_install/hugo4.png)

Open http://localhost:1313
(note. `Page Not Found` will appear due to no template. `Ctrl+C` to stop server)

<br>

## Select theme from Hugo Themes

Hugo Winston
https://themes.gohugo.io/themes/hugo-winston-theme/
https://github.com/zerostaticthemes/hugo-winston-theme
- uses Hugo Pipes (comes in extended version)


Initialize git repo. Commit files to repo.

```
git init
git add.
git commit -m "Initial commit"
```
![](/posts/posts_images/hugo_install/theme1.png)

```
git submodule add [hugo_theme_repo]
```

```
git submodule add https://github.com/zerostaticthemes/hugo-winston-theme.git themes/hugo-winston-theme
```

![](/posts/posts_images/hugo_install/theme2.png)

Edit hugo.toml (Hugo config file) on VS Code

![](/posts/posts_images/hugo_install/theme3.png)
Edit `.toml` file as necessary. Refer to exampleSite folder in github repo for corresponding Hugo theme.

https://github.com/zerostaticthemes/hugo-winston-theme/tree/master/exampleSite

Create post / content

```
hugo new content_name.md
```

![](/posts/posts_images/hugo_install/theme4.png)

Edit md file on VS Code

![](/posts/posts_images/hugo_install/theme5.png)

<br>

## Commit changes and connect to GitHub Pages Website

```
git add .
git commit -M "Update contents"
git branch -M main
git remote add origin https://github.com/ganyunhee/ganyunhee.github.io
git push origin main
```

Create `.github/workflows/hugo.yaml`

https://gohugo.io/hosting-and-deployment/hosting-on-github/

Copy and paste YAML contents from link above.

```
# Sample workflow for building and deploying a Hugo site to GitHub Pages 
name: Deploy Hugo site to Pages 

on: # Runs on pushes targeting the default branch 
	push: 
		branches: 
			- main # Allows you to run this workflow manually from the Actions tab 
	workflow_dispatch: # Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages 
permissions: 
	contents: 
	read pages: write 
	id-token: write 
	
# Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued. 
# However, do NOT cancel in-progress runs as we want to allow these production deployments to complete. 
concurrency: 
	group: "pages" 
	cancel-in-progress: false 
# Default to bash 
defaults: 
	run: 
		shell: bash 
jobs: 
	# Build job
	build: 
		runs-on: ubuntu-latest 
		env: 
			HUGO_VERSION: 0.115.1 
		steps: 
			- name: Install Hugo CLI 
			  run: | 
				  wget -O ${{ runner.temp }}/hugo.deb https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb \ 
				  && sudo dpkg -i ${{ runner.temp }}/hugo.deb 
			- name: Install Dart Sass 
			  run: sudo snap install dart-sass 
			- name: Checkout 
			  uses: actions/checkout@v3
			  with: 
				  submodules: recursive 
				  fetch-depth: 0 
		    - name: Setup Pages 
		      id: pages 
		      uses: actions/configure-pages@v3 
		    - name: Install Node.js dependencies 
		      run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true" 
		    - name: Build with Hugo env: # For maximum backward compatibility with Hugo modules 
			    HUGO_ENVIRONMENT: production 
			    HUGO_ENV: production 
			  run: | 
				  hugo \ 
				  --gc \ 
				  --minify \ 
				  --baseURL "${{ steps.pages.outputs.base_url }}/" 
		    - name: Upload artifact 
		      uses: actions/upload-pages-artifact@v1 
		      with: 
			      path: ./public 
			      
# Deployment job 
deploy: 
	environment: 
		name: github-pages 
		url: ${{ steps.deployment.outputs.page_url }} 
	runs-on: ubuntu-latest 
	needs: build 
	steps: 
		- name: Deploy to GitHub Pages 
		  id: deployment
		  uses: actions/deploy-pages@v2
```

<br>

## Others
___
How to remove non-empty dir in PowerShell
https://stackoverflow.com/questions/1752677/how-to-recursively-delete-an-entire-directory-with-powershell-2-0

```
rm -r -fo 'dir_path'
```

```
Remove-Item -Recurse -Force 'dir_path'
```