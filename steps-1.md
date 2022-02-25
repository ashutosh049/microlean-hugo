### Creating a Github hosted hugo site

```jshelllanguage
  $ hugo new site .
  Error: D:\PROJECTS\ashutosh049.github.io already exists and is not empty. See --force.
```

```jshelllanguage
   Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/ashutosh049.github.io (main)
   $ hugo new site . --force

   Congratulations! Your new Hugo site is created in D:\PROJECTS\ashutosh049.github.io.

   Just a few more steps and you're ready to go:

   1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
   2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>\<FILENAME>.<FORMAT>".
   3. Start the built-in live server via "hugo server".

   Visit https://gohugo.io/ for quickstart guide and full documentation.
```


#### Install hugo there

> Clone a theme from hugo site to you remote github. I forked from
https://github.com/ashutosh049/hugo-theme-cleanwhite-rsy.git

#### Command

`git submodule add <theme-github-url> <target-directory>`

```jshelllanguage
$ git submodule add https://github.com/ashutosh049/hugo-theme-cleanwhite-rsy.git themes/hugo-theme-cleanwhite-rsy

Cloning into 'D:/PROJECTS/ashutosh049.github.io/themes/hugo-theme-cleanwhite-rsy'...
   remote: Enumerating objects: 176, done.
   remote: Counting objects: 100% (176/176), done.
   remote: Compressing objects: 100% (150/150), done.
   remote: Total 176 (delta 22), reused 172 (delta 18), pack-reused 0
   Receiving objects: 100% (176/176), 4.30 MiB | 1.07 MiB/s, done.
   Resolving deltas: 100% (22/22), done.
   warning: LF will be replaced by CRLF in .gitmodules.
   The file will have its original line endings in your working directory
```

#### Testing

```shell
$ hugo serve -t  hugo-theme-cleanwhite-rsy
Start building sites …
hugo v0.92.2-CDF6A0D6 windows/amd64 BuildDate=2022-02-11T14:17:39Z VendorInfo=gohugoio
ERROR 2022/02/24 23:27:20 Page.URL is deprecated and will be removed in Hugo 0.93.0. Use .Permalink or .RelPermalink. If what you want is the front matter URL value, use .Params.url
                   | EN
-------------------+-----
Pages            |  7
Paginator pages  |  0
Non-page files   |  0
Static files     | 50
Processed images |  0
Aliases          |  1
Sitemaps         |  1
Cleaned          |  0

Built in 101 ms
Watching for changes in D:\PROJECTS\ashutosh049.github.io\{archetypes,content,data,layouts,static,themes}
Watching for config changes in D:\PROJECTS\ashutosh049.github.io\config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

> Now visit http://localhost:1313/
