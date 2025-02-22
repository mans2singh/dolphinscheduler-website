# Apache DolphinScheduler Official Website

This project keeps all sources used for building up DolphinScheduler official website which is served at https://dolphinscheduler.apache.org/.

## Prerequisite

DolphinScheduler website is powered by [docsite](https://github.com/chengshiwen/docsite-ext).

Please also make sure your node version is 10+, version lower than 10.x is not supported yet.

## Prepare All Related Resource

Our latest documents are in DolphinScheduler [main repository](https://github.com/apache/dolphinscheduler.git) directory
`docs`, and the history documents is in branch [history-docs](https://github.com/apache/dolphinscheduler-website/tree/history-docs)
in this repository. In this case, you have to collect them from somewhere to current working path before you compile
them to HTML format.

Of course, you could collect all content manually, but we already provider convenience script to do that, all you have to
do is run a single command:

```shell
./scripts/prepare_docs.sh
```

It would do all prepare things for you.

> Note: When you failed to run the command and see some log like "unable to access" in your terminal, you can set and
> environment variable `export DEV_MODE=true` and then run command `./scripts/prepare_docs.sh` again. After setting the
> variable will clone source code in SSH instead of HTTPS, it will stable and fast in some cases.

## Build instruction 

1. Run `npm install` in the root directory to install the dependencies.
2. Run `npm run start` in the root directory to start a local server, you will see the website in 'http://localhost:8080'.
```
Note: if you clone the code in Windows, not Mac. Please read the details below.
If you execute the commands like the two steps above, you will get the exception "UnhandledPromiseRejectionWarning: Error: EPERM: operation not permitted, symlink '2.0.3' -> 'latest'".
When meeting this problem. You can run two steps in the cmd.exe as an ADMINISTRATOR MEMBER.
```
3. Run `npm run build` to build source code into dist directory.
4. Verify your change locally: `python -m SimpleHTTPServer 8000`, when your python version is 3 use :`python3 -m http.server 8000` instead.

If you have higher version of node installed, you may consider `nvm` to allow different versions of `node` coexisting on your machine.

1. Follow the [instructions](http://nvm.sh) to install nvm
2. Run `nvm install v10.23.1` to install node v10
3. Run `nvm use v10.23.1` to switch the working environment to node v10

Then you are all set to run and build the website. Follow the build instruction above for the details.


## How to send a PR

1. Do not use `git add .` to commit all the changes.
2. Just push your changed files, such as:
    * `*.md`
	* blog.js or docs.js or site.js
3. Send a PR to **master** branch.

## SEO

Make sure each .md starts with the following texts:

```
---
title: title
keywords: keywords1,keywords2, keywords3
description: some description
---
```


## Guide for adding a new document

### Add a new blog

1. Add new .md file under blog/en-us or blog/zh-cn. 
2. Update site_config/blog.js, add a new entry to the blog in either en-us or zh-cn.
3. Run docsite start locally to verify the blog can be displayed correctly.
4. Send the pull request contains the .md and blog.js only.


### Add a new article for development

1. Add new .md file under docs/en-us/development or docs/zh-cn/development.
2. Update site_config/development.js, add a new entry in either en-us or zh-cn.
3. Run docsite start locally to verify the article can be displayed correctly.
4. Send the pull request contains the *.md and development.js only.


### Add a new article for docs

1. Add new .md file under docs/en-us or docs/zh-cn.
2. Update site_config/docs.js, add a new entry in either en-us or zh-cn.
3. Run docsite start locally to verify the article can be displayed correctly.
4. Send the pull request contains the *.md and docs.js only.

Best Regards.  
				Thanks for reading :)
