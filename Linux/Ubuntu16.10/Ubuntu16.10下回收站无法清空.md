## Ubuntu16.10下回收站无法清空

在ubuntu/ubuntu Kylin下，删除了某些文件，而当准备清空回收站的时候，却发现无法清空，打开回收站，在里面进行文件删除时提示“Failed to delete the item from the trash”。如果你也遇到此问题，那么可以按以下步聚清除回收站的内容。

> 解决方法：

```shell
cd /home/shenyifei/.local/share/Trash/files
sudo rm -rf *
```

