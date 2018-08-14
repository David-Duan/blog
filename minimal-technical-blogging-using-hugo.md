---
title: "Minimal Technical Blogging Using Hugo"
date: 2017-10-30T19:52:37+11:00
tags: [ "Hugo", "CentOS 7"]
categories: ["Operation"]
---
# Basically
1. Focus on your content, using Markdown write your blog with Atom.
2. Start Hugo server on local, check the layout is ok.
3. Generate static website and deploy it to your VPS.

# Steps
## Install Hugo

  macOS:

  ```shell
  brew install hugo
  ```

  CentOS 7:

  + add new yum repository file.

  ```shell
  cd /etc/yum.repos.d/
  vi Hugo.repo
  ```

  ```configuration
  [daftaupe-hugo]
  name=Copr repo for hugo owned by daftaupe
  baseurl=https://copr-be.cloud.fedoraproject.org/results/daftaupe/hugo/epel-7-$basearch/
  type=rpm-md
  skip_if_unavailable=True
  gpgcheck=1
  gpgkey=https://copr-be.cloud.fedoraproject.org/results/daftaupe/hugo/pubkey.gpg
  repo_gpgcheck=0
  enabled=1
  enabled_metadata=1
  ```

  + Install

  ```shell
  yun -y install hugo
  ```

  + check hugo installed

  ```shell
  hugo version
  ```

## Create New website

```shell
hugo new site blog
```
### add a theme
choose a theme from [here](https://themes.gohugo.io) and follow it's instructions, for instance:

+ install

```shell
cd blog
git clone https://github.com/olOwOlo/hugo-theme-even themes/even
```
+ Copy the config.toml file from the exampleSite directory to your site directory and change it.

### create new page
```shell
hugo new post/my-first-post.md
```
### write something

## Run server
```shell
hugo server -D
```
Now, the Hugo server has been stated with drafts enabled. You may start you journey now.

## Add new post
Use Atom with package "platformio-ide-terminal".
!["minimal-technical-blogging-using-hugo"](/post/images/minimal-technical-blogging-using-hugo-1.png)

Delete "draft: true" from the Front Matter, then
```shell
hugo server
```

## Deploy
Generate static website
```shell
hugo
```
a "public" folder generated and then, you may then deploy your site by copying the public/ directory to your production web server.


# Reference
+ [https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#images)
+ [https://gohugo.io/getting-started/usage/](https://gohugo.io/getting-started/usage/)
+ [https://themes.gohugo.io/hugo-theme-even/](https://themes.gohugo.io/hugo-theme-even/)
