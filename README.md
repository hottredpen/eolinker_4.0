### eolinker4.0开源版本

首先感谢eolinker官方对之前版本的开源，本项目为eolinker4.0开源版本。eoLinker是目前全球领先、国内最大的在线API接口管理平台，提供自动生成API文档、API自动化测试、Mock测试、团队协作等功能，旨在解决由于前后端分离导致的开发效率低下问题。

新版本的eolinker已不再开源，该版本为开源旧版本，本仓库仅供大家参考学习使用不会对其维护更新升级等，如需使用最新的eolinker请移步其官网：https://www.eolinker.com/ 感谢。

### 前端页面打包注意事项
##### 1、node版本
6.2.2

##### 2、包依赖
目前为了包管理直接保存了所有的node_modules,所有只要node版本为6.2.2就可以

##### 3、打包
先清除之前的文件,如果之前没打过包请忽略（如：lib,eolinker）
```
rm -rf ./lib
```

在frontend_source_code中执行
```
./node_modules/babel-cli/bin/babel.js src -d lib
```
会根据 src 生成一个lib文件
完成后，执行
```
./node_modules/gulp/bin/gulp.js
```

完成后会在当前目录生成一个`eolinker`文件夹

##### 4、发布
将backend_source_code命名为server放入eolinker内，就是一个发布包

##### 5、其他
数据库的配置在
server/RTP/config/eo_config.php没有的话请自行创建
```
<?php
//主机地址
defined('DB_URL') or define('DB_URL', 'localhost');

//主机端口,默认mysql为3306
defined('DB_PORT') or define('DB_PORT', '3306');

//连接数据库的用户名
defined('DB_USER') or define('DB_USER', 'root');

//连接数据库的密码，推荐使用随机生成的字符串
defined('DB_PASSWORD') or define('DB_PASSWORD', '123456');

//数据库名
defined('DB_NAME') or define('DB_NAME', 'eolinker');

//是否允许新用户注册
defined('ALLOW_REGISTER') or define('ALLOW_REGISTER', TRUE);

//是否允许更新项目，如果设置为FALSE，那么自动更新和手动更新都将失效
defined('ALLOW_UPDATE') or define('ALLOW_UPDATE', TRUE);

//网站名称
defined('WEBSITE_NAME') or define('WEBSITE_NAME', 'eoLinker开源版本');

//数据表前缀
defined('DB_TABLE_PREFIXION') or define('DB_TABLE_PREFIXION', 'eo');

//语言
defined('LANGUAGE') or define ('LANGUAGE', 'zh-cn');
?>
```

错误：
mac能再本地跑3.5版本但是跑不了4.0版本。但测试上可以跑4.0版本
会有类似以下的错误（可能是缺少某种字体）
```
Uncaught SyntaxError: Unexpected token '<'
```

修改：
以下几个文件可能在改变前端样式的时候会有修改
```
    modified:   app/component/footer/index.html
    modified:   app/component/navbar/nav0/index.html
    modified:   app/component/navbar/nav1/index.html
    modified:   app/component/navbar/nav2/index.html
    modified:   app/component/sidebar/index.js
    modified:   app/constant/trans.constants.js
    modified:   index.html
```


