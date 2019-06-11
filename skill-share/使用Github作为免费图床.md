## 1. 新建一个repositories

## 2. 进入repositories下的wiki选项中

![](https://raw.githubusercontent.com/wiki/zhangpeng181818/images/skill-share/1.png)

## 3. 复制wiki对应的克隆地址

![](https://raw.githubusercontent.com/wiki/zhangpeng181818/images/skill-share/2.png)

## 4. 在本地克隆项目

```shell
git clone https://github.com/garuhester/ImageBed.wiki.git
```

![](https://raw.githubusercontent.com/wiki/zhangpeng181818/images/skill-share/3.png)

## 5. 进入文件夹，将要上传的图片放在文件夹中

![](https://raw.githubusercontent.com/wiki/zhangpeng181818/images/skill-share/4.png)

## 6. 打开命令行，依次输入命令：

```shell
git add photo.png

git commit -a -m "update"

git push 
```

## 7. 现在已经将图片放置Github图床，图片的地址为：

```
https://raw.githubusercontent.com/wiki/garuhester/ImageBed/photo.png
```

> `garuhester`为你的Github用户名（username）
> `ImageBed`为你创建的repository的名称（repository）
> `photo.png`为图片的名称



本文转载自：   [Github图床](https://www.jianshu.com/p/c794bad425e5)