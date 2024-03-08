---
title: "My First Post"
date: 2024-03-08T08:05:51+08:00
draft: false
---

一、yum无法直接安装hugo，首先添加repo

vim /etc/yum.repos.d/hugo.repo
输入以下内容

复制代码
1 [daftaupe-hugo]
2 name=Copr repo for hugo owned by daftaupe
3 baseurl=https://copr-be.cloud.fedoraproject.org/results/daftaupe/hugo/epel-7-$basearch/
4 type=rpm-md
5 skip_if_unavailable=True
6 gpgcheck=1
7 gpgkey=https://copr-be.cloud.fedoraproject.org/results/daftaupe/hugo/pubkey.gpg
8 repo_gpgcheck=0
9 enabled=1
复制代码
二、安装hugo

yum -y install hugo
三、生成博客根目录

hugo new site myblog
四、到https://themes.gohugo.io寻找喜欢的主题，进入博客根目录（myblog），利用git获取主题到本地themes文件夹

git clone https://github.com/vaga/hugo-theme-m10c.git themes/m10c
五、创建文章

hugo new firstblog.md
创建的.md文件会自动生成在根目录下的content文件夹里

六、本地启动

hugo server -t m10c --buildDrafts
七、将博客部署到远端服务器（利用GitHub Pages）

在GitHub上创建一个新仓库，仓库命名格式"GitHub用户名.github.io"，如下：



 

 回到博客根目录，执行如下命令，会在根目录下生成一个名为public的目录

hugo -theme=m10c --baseUrl="https://king0111.github.io/" --buildDrafts
进入public目录，执行如下命令

git init
git add .
git commit -m "my hugo_blog first commit"
git remote add origin https://github.com/king0111/king0111.github.io.git
git push -u origin master
 输入自己的GitHub用户名和密码