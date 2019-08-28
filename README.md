# zcyang668.github.io
上传hexo blog源文件的步骤及闭坑指南<br>
其实目前只有一个坑 以下步骤执行前 先到themes文件夹下把你克隆的主题文件夹下的.git文件夹删除<br>
在自己建的本地博客文件夹内执行，我的是blog<br>
```bash
cd blog<br>
git init #初始化git<br>
git add source _config.yml themes scaffolds package-lock.json package.json  #添加要上传的文件和文件夹<br>
git commit -m "任意"<br>
git push origin hexo #上传到hexo分支<br>
