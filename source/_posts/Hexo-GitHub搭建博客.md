---
title: Hexo+GitHub搭建博客
date: 2020-12-27 21:14:28
top_img: https://wx2.sinaimg.cn/mw2000/81f937cely1g01qgte4ulj20xc0jjjuw.jpg
categories: 
           - 技术博客
tags:
        - web
---





#### 准备


 - GitHub账号
 - 安装nodejs
 - 安装git
 #### 1. GitHub创建仓库
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201227212754535.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1MDA4MTQ4,size_16,color_FFFFFF,t_70)
 - 仓库名为 username.github.io

#### 2.本地搭建博客网站


 1. 安装nodejs


	```bash
	//确认是否安装成功
	npm -v
	```
 2. 安装git
	```bash
	//确认是否安装成功
	git --version
	```
 3. 安装hexo
	```bash
	npm install hexo-cli -g
	```
 4. 创建博客
	```bash
	hexo init blog
	cd blog
	npm install
	```
 5. 测试
	```bash
	hexo g
	hexo server
	```
	访问[http://localhost:4000/](http://localhost:4000/)查看本地搭建的网站
#### 本地无密码连接GitHub

 6. 在git命令行中设置用户名和邮箱
 7. 在Powershell（cmd）输入 ssh-keygen -t rsa -C "your email"回车，一直回车
 8. 在输出信息中找到生产密钥地址，一般是在.ssh文件夹，id_rsa.pub公钥文件，id_rsa是私钥文件。
 9. 复制id_rsa.pub文件中的内容，在GitHub设置中新建ssh key并填入生成公钥内容
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201227214320329.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1MDA4MTQ4,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201227214443408.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1MDA4MTQ4,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20201227214500715.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1MDA4MTQ4,size_16,color_FFFFFF,t_70)

 10. 测试能否连接成功
		```bash
		ssh -T git@github.com
		```
		命令行中输入上面的命令，提示连接成功则配置成功
#### 将网站部署到GitHub上

 1. 修改项目目录中_config.yml文件，具体修改内容如下


	```bash
	deploy:
	  type: git
	  repo: https://github.com/GeJi133/GeJi133.github.io.git
	  branch: main
	  message: update
	```
	branch的具体分支查看GitHub仓库>>Setting>>Options>>githubPages设置的分支
	![在这里插入图片描述](https://img-blog.csdnimg.cn/202012272154594.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ1MDA4MTQ4,size_16,color_FFFFFF,t_70)

2. 将搭建的网站push到GitHub上
	```bash
	hexo clean
	hexo d
	```
3. 输入username.github.io就可以看到自己的博客啦

