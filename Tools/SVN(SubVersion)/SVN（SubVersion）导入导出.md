## SVN（SubVersion）导入导出

### 版本库的数据移植

> svnadmin dump、svnadmin load

#### 导出

```shell
# 导出全部的库
svnadmin dump /data/svn/huihsuo > /data/svnback/rev-all.huishuo
# 导出制定版本的库
svnadmin dump /data/svn/huishuo -r 13629 /data/svnback/reb-13629.huishuo
```

导入

```shell
svnadmin loan huishuo < /data/svnback/reb-13629.huishuo
```
