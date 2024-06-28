首先去官网选择mac版本下载安装 typora下载

然后打开typora包内容找到

/Applications/Typora.app/Contents/Resources/TypeMark/ 

编辑器打开上面文件夹，这里我拉到vscode

找到page-dist/static/js/Licen..如下图 

![](https://img-blog.csdnimg.cn/6448e258546449a5b07a030efa630cd2.png)



输入 `hasActivated="true"==e.hasActivated `进行搜索

将它改为  `hasActivated="true"=="true"`

重新打开typora看到成功激活！！！
