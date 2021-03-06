## 更新日志

### 1.4 (2015-06-05)
* 优化后台部分逻辑
* 加入邮件服务
* 移出kindeditor相关文件

### 1.4.2 (2015-09-20)
* 加入新的评论邮件通知选项
* 多说绑定页面，不用手动输入
* IP 黑名单
* 文件 html,css,js 支持在线编辑

### 1.4.3 (2015-12-20)
* 优化对接多说相关代码（Map -> Bean）
* 更改 ehcache 默认配置（ehcache内存申请过多，内存较小的主机被杀JVM进程）

### 1.4.4 (2016-1-16)
* JFinal 升级至 2.1
* 添加后台检索文章功能
* 优化编辑文章代码
* 加入主题预览
* 修复黑名单无法正确的拦截所有请求的问题

### 1.5 (2016-4-12)

#### 新特
* 构建全新的插件模式
* 多说，七牛，备份数据库，邮件服务改为插件方式实现（需要进行下载才可以使用）
* 记录管理界面的侧边栏状态，可设置默认管理界面的主题
* 移除大量并未使用到的静态文件 （war包体积缩小到7M左右）
* 可在zrlog主题中心下载主题，插件
    
#### 优化
* 使用Maven管理jar文件,JFinal 升级到 2.2
* 优化主题管理页面
* 管理员登录忽略大小写
* 优化文章管理页面的弹出框，弃用Zdialog，使用eModal
* log4j 日志文件分天存储，方便查找
* 开启静态化后，只是储存 /post/* 的文章页
* 其他css问题

#### 修复
* 修复 v1.4.4 搜索乱码
* 修复 editor.md 与 bootstrap 的样式问题 (升级 editor.md 到v1.5)
* 修复 editor.md z-index 问题
* 修复在编辑过程中尚未触发存草稿导致就尝试预览 `NullPointerException`

### 1.6 (2016-12-13)

#### 新特
* 自动更新功能
* 博客搜索结果高亮检索的关键字
* 七牛插件支持全站静态资源托管
* 添加本地主题上传
* 主题数据可以存放到数据库（及主题可以配置）
* 全新的后台管理界面
* 管理博客时支持按时间，浏览量等信息进行排序
* 提供多语言
* 添加mysql数据版本信息在管理后台主页

#### 优化
* 重构管理相关代码，实现了接口数据与模板数据渲染的控制器代码分离
* 简化分页数据的遍历，优化模板数据，更加轻松的编写主题
* 独立后台页面的javascript部分
* 优化安装引导界面
* 部分图标的优化
* 优化默认主题的一些样式
* 移除`Ehcache`，改用内存的方式存放全局数据（war体积减小到6M）

#### 修复
* 部分平台插件默认编码问题
* 程序停止后，对应的插件服务无法停止的问题
* 修复静态化开启后部分平台乱码问题

### 1.7 (2017-5-31)

#### 新特
* 文章，分类别名支持中文
* 更新管理界面添加手动检测按钮
* 增强了主题开发（引入dev.jsp可以快速浏览存放在request域的数据，便于模板页面读取的渲染）
* https的支持，需要在nginx.conf文件的http块里面添加 `proxy_set_header X-Forwarded-Protocol $scheme;`
* 在网站设置里添加对会话过期时间的控制
* 改进了插件功能，使用vue.js客户端渲染替换原有使用freemarker服务端渲染
* 备份插件支持window系统
* 增加新的畅言评论框（原多说已宣布关闭，实在令人惋惜）
* 开源协议由GPLv2变更到Apache

#### 优化
* 升级JFinal到3.1，将Java版本提升至1.7
* 优化对后台管理页面的静态资源缓存
* 优化插件服务的内存占用
* 下载插件核心服务时关闭缓存
* 优化程序更新流程，更新的检查机制
* 管理主面板添加系统编码信息
* 默认主题添加标题设置，避免域名过长的情况下，样式被破坏的问题
* 优化主题管理界面
* 废弃session的方式控制权限，变更为Cookie验证
* 优化/api/\*的错误请求，改为响应json数据
* 优化编辑文章的方式，由原来的弹窗标题改为跳转到撰写文章界面进行编辑
* 安装界面添加安装需要的注意事项
* 启动插件使用java的完整路径进行启动，避免部分云平台没有将java添加到PATH中，无法正常启动的问题
* 删除一些没有使用资源文件，默认主题的使用通用的头像图片
* 优化文章编辑页的文章分类的选择框的样式，优化一些其它的样式
* 完善一些页面的i18n，后台管理界面添加主题预览状态的提示

#### 修复
* 导航条数据无法更新
* 默认主题无法上传图片
* 关闭更新功能后，无法正常启动的bug（感谢 [@说好不上学](https://www.weekdragon.cn/) 发现的bug）
* 修复上一篇，下一篇的请求地址错误
* 修复主题无法上传的问题
* 修复IE浏览器，管理员登陆成功后无法正常的跳转
* 修复website表value的长度不够的问题
* 修复mysql5.7以上版本，需要配置`sql_mode`（group by语法无法正常执行）的问题
* 修复Window系统下，升级过程中无法正常解压生成新的war文件
* 修复标签添加后，无法通过标签进行定位文章
* 修复主题预览状态，预览文章页面主题的资源文件路径错误的问题
* 修复IE下使用 localhost 进行访问，无法进行进行登陆（IE限制Cookie的domain字段，不能设置为localhost）
* 修复插件的运行路径无法跟随程序路径变化而变化的问题（Windows的文件完整路径到Linux下面文件却成了文件名）

### 1.8 (2017-12-12)

#### 新特
* 文章编辑添加插入封面图片
* 文章编辑器添加黑色皮肤，晚上写文章也不再那么费力
* 文章编辑工具支持上传附件
* 删除主题
* 备份的数据库文件仅保留最近20条记录

#### 优化
* 优化文章编辑页面，看上去不再那么的空旷
* 页面禁用Session
* 优化添加评论
* 优化畅言插件发邮件样式
* 对登录中密码进行加密（请求阶段）
* 优化文章的检索，搜索 div 这类关键字也不怕
* 优化其它多处页面样式，调整多处布局
* 优化更新程序的界面和体验
* JFinal 升级到3.3
* 管理后台，校验部分表单必填字段

#### 修复
* 修复了1.7无法变更管理员密码的bug
* 修复管理文章列表中部分字段无法排序

### 1.9

#### 新特
* 加入一套新的主题（涉水轻舟-2018）
* 支持视频上传，页面使用videojs播放视频文件
* 更加简洁管理后台登录页

#### 优化
* 安装向导过程填写数据信息时，提示更加完善
* 文章配图自动填充时，支持外站链接
* 优化大量的代码，重构maven的结构，代码间的依赖更加清晰
* 超过数10余项的页面细节优化

#### 修复
* 1.8 更新后需要重启webserver后才能保存文章
* 其它已知bug修复