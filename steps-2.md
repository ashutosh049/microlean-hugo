##### Color updates
```
pale-green: #63b175
navbar-brand: #00FA9A
```

##### Repo sub modules
- https://github.com/ashutosh049/hugo-theme-cleanwhite-rsy.git
    ```shell
    git submodule add https://github.com/ashutosh049/hugo-theme-cleanwhite-rsy.git themes/hugo-theme-cleanwhite-rsy
    - ```

- https://github.com/ashutosh049/ashutosh049.github.io.git

    ```shell
    git submodule add -b master https://github.com/ashutosh049/ashutosh049.github.io.git public
    ```

#### Sample 
```shell
Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        .hugo_build.lock
        LICENSE
        README.md
        archetypes/
        config.toml
        content/
        deploy.sh
        layouts/
        resources/
        static/
        themes/

nothing added to commit but untracked files present (use "git add" to track)

Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$ git commit -m "Initial commit"
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
        .hugo_build.lock
        LICENSE
        README.md
        archetypes/
        config.toml
        content/
        deploy.sh
        layouts/
        resources/
        static/
        themes/

nothing added to commit but untracked files present (use "git add" to track)

Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$ git add --all
warning: LF will be replaced by CRLF in deploy.sh.
The file will have its original line endings in your working directory

Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$ git add --all

Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   .gitignore
        new file:   .hugo_build.lock
        new file:   LICENSE
        new file:   README.md
        new file:   archetypes/default.md
        new file:   archetypes/post.md
        new file:   config.toml
        new file:   content/post/binary-tree-lowest-common-ancestor-lca/binary-tree-lowest-common-ancestor-lca.md
        new file:   content/post/binary-tree-maximum-depthheight-of-deepest-node-using-recursive-and-iterative-way-hpp/binary-tree-maximum-depthheight-of-deepest-node-using-recursive-and-iterative-way-hpp.md
        new file:   content/post/demystifying_spring_task_executor/demystifying_spring_task_executor.md
        new file:   content/top/about.md
        new file:   deploy.sh
        new file:   layouts/_default/single.html
        new file:   layouts/partials/post_list.html
        new file:   resources/_gen/assets/scss/scss/main.scss_f300667da4f5b5f84e1a9e0702b2fdde.content
        new file:   resources/_gen/assets/scss/scss/main.scss_f300667da4f5b5f84e1a9e0702b2fdde.json
        new file:   static/images/about/profile-dummy-1.png
        new file:   static/images/banners/fUcdgux.gif
        new file:   static/images/banners/main_background.jpg
        new file:   static/images/banners/tenor.gif


Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$ git commit -m "Initial Commit"
[master (root-commit) 9465253] Initial Commit
 20 files changed, 2511 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 .hugo_build.lock
 create mode 100644 LICENSE
 create mode 100644 README.md
 create mode 100644 archetypes/default.md
 create mode 100644 archetypes/post.md
 create mode 100644 config.toml
 create mode 100644 content/post/binary-tree-lowest-common-ancestor-lca/binary-tree-lowest-common-ancestor-lca.md
 create mode 100644 content/post/binary-tree-maximum-depthheight-of-deepest-node-using-recursive-and-iterative-way-hpp/binary-tree-maximum-depthheight-of-deepest-node-using-recursive-and-iterative-way-hpp.md
 create mode 100644 content/post/demystifying_spring_task_executor/demystifying_spring_task_executor.md
 create mode 100644 content/top/about.md
 create mode 100644 deploy.sh
 create mode 100644 layouts/_default/single.html
 create mode 100644 layouts/partials/post_list.html
 create mode 100644 resources/_gen/assets/scss/scss/main.scss_f300667da4f5b5f84e1a9e0702b2fdde.content
 create mode 100644 resources/_gen/assets/scss/scss/main.scss_f300667da4f5b5f84e1a9e0702b2fdde.json
 create mode 100644 static/images/about/profile-dummy-1.png
 create mode 100644 static/images/banners/fUcdgux.gif
 create mode 100644 static/images/banners/main_background.jpg
 create mode 100644 static/images/banners/tenor.gif

Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$ git push
Enumerating objects: 41, done.
Counting objects: 100% (41/41), done.
Delta compression using up to 8 threads
Compressing objects: 100% (30/30), done.
Writing objects: 100% (41/41), 3.80 MiB | 1.58 MiB/s, done.
Total 41 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/ashutosh049/microlean-hugo.git
 * [new branch]      master -> master

Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$ git submodule add https://github.com/ashutosh049/hugo-theme-cleanwhite-rsy.git themes/hugo-theme-cleanwhite-rsy
Cloning into 'D:/PROJECTS/MICROLEAN_BLOG/microlean-hugo/themes/hugo-theme-cleanwhite-rsy'...
remote: Enumerating objects: 176, done.
remote: Counting objects: 100% (176/176), done.
remote: Compressing objects: 100% (150/150), done.
remote: Total 176 (delta 22), reused 172 (delta 18), pack-reused 0R
Receiving objects: 100% (176/176), 4.30 MiB | 1.52 MiB/s, done.
Resolving deltas: 100% (22/22), done.
warning: LF will be replaced by CRLF in .gitmodules.
The file will have its original line endings in your working directory

Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$ git submodule add -b master https://github.com/ashutosh049/ashutosh049.github.io.git public
Cloning into 'D:/PROJECTS/MICROLEAN_BLOG/microlean-hugo/public'...
remote: Enumerating objects: 267, done.
remote: Counting objects: 100% (267/267), done.
remote: Compressing objects: 100% (142/142), done.
remote: Total 267 (delta 94), reused 256 (delta 87), pack-reused 0 eceiving objects:  91% (243/267), 4.57 MiB | 1.80 MiB/s
Receiving objects: 100% (267/267), 4.86 MiB | 1.75 MiB/s, done.
Resolving deltas: 100% (94/94), done.
warning: LF will be replaced by CRLF in .gitmodules.
The file will have its original line endings in your working directory

Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$ hugo server -D
Start building sites …
hugo v0.92.2-CDF6A0D6 windows/amd64 BuildDate=2022-02-11T14:17:39Z VendorInfo=gohugoio
ERROR 2022/02/25 04:44:23 Page.URL is deprecated and will be removed in Hugo 0.93.0. Use .Permalink or .RelPermalink. If what you want is the front matter URL value, use .Params.url

                   | EN
-------------------+-----
  Pages            | 33
  Paginator pages  |  0
  Non-page files   |  0
  Static files     | 54
  Processed images |  0
  Aliases          | 10
  Sitemaps         |  1
  Cleaned          |  0

Built in 216 ms
Watching for changes in D:\PROJECTS\MICROLEAN_BLOG\microlean-hugo\{archetypes,content,layouts,static,themes}
Watching for config changes in D:\PROJECTS\MICROLEAN_BLOG\microlean-hugo\config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop

Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$ ./deploy.sh
Deploying updates to GitHub...


Committing changes to /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo
Start building sites …
hugo v0.92.2-CDF6A0D6 windows/amd64 BuildDate=2022-02-11T14:17:39Z VendorInfo=gohugoio
ERROR 2022/02/25 04:46:06 Page.URL is deprecated and will be removed in Hugo 0.93.0. Use .Permalink or .RelPermalink. If what you want is the front matter URL value, use .Params.url

                   | EN
-------------------+-----
  Pages            | 33
  Paginator pages  |  0
  Non-page files   |  0
  Static files     | 54
  Processed images |  0
  Aliases          | 10
  Sitemaps         |  1
  Cleaned          |  0

Total in 519 ms


Committing changes to /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo/public
warning: LF will be replaced by CRLF in categories/index.xml.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in categories/tech/index.xml.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in index.html.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in post/binary-tree-lowest-common-ancestor-lca/binary-tree-lowest-common-ancestor-lca/index.html.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in sitemap.xml.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in tags/index.xml.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in tags/spring/index.xml.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in tags/threads/index.xml.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in top/about/index.html.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in top/index.xml.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in post/binary-tree-maximum-depthheight-of-deepest-node-using-recursive-and-iterative-way-hpp/binary-tree-maximum-depthheight-of-deepest-node-using-recursive-and-iterative-way-hpp/index.html.
The file will have its original line endings in your working directory
warning: LF will be replaced by CRLF in post/demystifying_spring_task_executor/demystifying_spring_task_executor/index.html.
The file will have its original line endings in your working directory
[master 6ae8dc1] rebuilding site Fri Feb 25 04:46:04 IST 2022
 33 files changed, 1724 insertions(+), 70 deletions(-)
 create mode 100644 images/banners/main_background.jpg
 create mode 100644 post/binary-tree-maximum-depthheight-of-deepest-node-using-recursive-and-iterative-way-hpp/binary-tree-maximum-depthheight-of-deepest-node-using-recursive-and-iterative-way-hpp/index.html
 create mode 100644 post/demystifying_spring_task_executor/demystifying_spring_task_executor/index.html
Enumerating objects: 106, done.
Counting objects: 100% (106/106), done.
Delta compression using up to 8 threads
Compressing objects: 100% (53/53), done.
Writing objects: 100% (58/58), 157.10 KiB | 3.83 MiB/s, done.
Total 58 (delta 33), reused 1 (delta 1), pack-reused 0
remote: Resolving deltas: 100% (33/33), completed with 15 local objects.
To https://github.com/ashutosh049/ashutosh049.github.io.git
   ffc19cf..6ae8dc1  master -> master


Committing changes to /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo
warning: LF will be replaced by CRLF in .gitmodules.
The file will have its original line endings in your working directory
[master 9c6d74a] rebuilding site Fri Feb 25 04:46:04 IST 2022
 3 files changed, 9 insertions(+)
 create mode 100644 .gitmodules
 create mode 160000 public
 create mode 160000 themes/hugo-theme-cleanwhite-rsy
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 554 bytes | 184.00 KiB/s, done.
Total 4 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/ashutosh049/microlean-hugo.git
   9465253..9c6d74a  master -> master

Admin@DESKTOP-6G798VA MINGW64 /d/PROJECTS/MICROLEAN_BLOG/microlean-hugo (master)
$

```


##### Update to hugo extended version

1. Open windows powershell as admin
2. run `choco install hugo-extended -confirm`
3. Verify hugo version. Find `extended` word in verison info

```shell
$ hugo version
hugo v0.93.2-643B5AE9+extended windows/amd64 BuildDate=2022-03-04T12:21:49Z VendorInfo=gohugoio
```