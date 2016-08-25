# UCenter 1.6 数据字典

## uc_admins  管理员权限表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| uid | mediumint(8) unsigned |   | NO | 是 | 用户ID |
| username | char(15) |   | NO |   | 用户名 |
| allowadminsetting | tinyint(1) |   | NO |   | 是否允许改变设置 |
| allowadminapp | tinyint(1) |   | NO |   | 是否允许管理应用列表，如: 添加|编辑|删除 应用 |
| allowadminuser | tinyint(1) |   | NO |   | 是否允许管理会员 |
| allowadminbadword | tinyint(1) |   | NO |   | 是否允许设置词语过滤 |
| allowadmintag | tinyint(1) |   | NO |   | 是否允许管理 tag |
| allowadminpm | tinyint(1) |   | NO |   | 是否允许管理短消息 |
| allowadmincredits | tinyint(1) |   | NO |   | 是否允许设置积分公式 |
| allowadmindomain | tinyint(1) |   | NO |   | 是否允许管理域名解析 |
| allowadmindb | tinyint(1) |   | NO |   | 是否允许管理数据库 |
| allowadminnote | tinyint(1) |   | NO |   | 是否允许管理通知 |
| allowadmincache | tinyint(1) |   | NO |   | 是否允许更新缓存 |
| allowadminlog | tinyint(1) |   | NO |   | 是否允许查看和管理日志 |

## uc_applications  应用列表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| appid | smallint(6) unsigned |   | NO | 是 | 应用的ID |
| type | varchar(16) |   | NO |   | 应用类型 DISCUZ|SUPESITE|UCHOME|XSPACE|SUPEV|ECSHOP|ECMALL|其他 |
| name | varchar(20) |   | NO |   | 应用名称 |
| url | varchar(255) |   | NO |   | 应用的URL地址 |
| authkey | varchar(255) |   | NO |   | 应用的密钥，注意: 每个应用的密钥都不一样 |
| ip | varchar(15) |   | NO |   | 应用的IP地址，注意：不填写的话，可能会影响速度，因为DNS解析比较耗费时间。 |
| viewprourl | varchar(255) |   | NO |   | 用户资料查看地址 |
| apifilename | varchar(30) | uc.php | NO |   | 接口文件名称 |
| charset | varchar(8) |   | NO |   | 应用的字符集 如: GBK|LATIN1|UTF-8 |
| dbcharset | varchar(8) |   | NO |   | 数据库的字符集 如: gbk|latin1|utf8 |
| synlogin | tinyint(1) |   | NO |   | 是否开启同步登陆 |
| recvnote | tinyint(1) |   | YES |   | 是否接受通知 |
| extra | text |   | NO |   | 附加参数，格式为序列化后的数组 |
| tagtemplates | text |   | NO |   | 显示 tag 的模板内容 |
| allowips | text |   | NO |   |   |

## uc_badwords  词语过滤表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| id | smallint(6) unsigned |   | NO | 是 | 编号 |
| admin | varchar(15) |   | NO |   | 添加该条记录的管理员用户名 |
| find | varchar(255) |   | NO |   | 原词语 |
| replacement | varchar(255) |   | NO |   | 替换为的词语 |
| findpattern | varchar(255) |   | NO |   | 原词语的正则表达式 |

## uc_domains  域名-IP 映射表，用来避免频繁的DNS解析。

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| id | int(10) unsigned |   | NO | 是 | 编号 |
| domain | char(40) |   | NO |   | 域名 |
| ip | char(15) |   | NO |   | IP |

## uc_failedlogins  记录登陆失败次数，用来防止暴力猜解管理员密码

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| ip | char(15) |   | NO |   | IP |
| count | tinyint(1) unsigned |   | NO |   | 登陆失败的次数 |
| lastupdate | int(10) unsigned |   | NO |   | 上次登陆失败的时间 |

## uc_feeds  feed 数据表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| feedid | mediumint(8) unsigned |   | NO | 是 | FEED的ID |
| appid | varchar(30) |   | NO |   | 应用的ID |
| icon | varchar(30) |   | NO |   | feed 类型对应的图标 如: poll|post|trade|video |
| uid | mediumint(8) unsigned |   | NO |   | 用户id |
| username | varchar(15) |   | NO |   | 用户名 |
| dateline | int(10) unsigned |   | NO |   | feed 添加的时间 |
| hash_template | varchar(32) |   | NO |   | feed 显示的模板的 hash 值，用来判断合并多条类似的 feed |
| hash_data | varchar(32) |   | NO |   | 数据的 hash 值，用来判断合并多条类似的 feed |
| title_template | text |   | NO |   | 标题的模板 |
| title_data | text |   | NO |   | 标题的内容 |
| body_template | text |   | NO |   | 内容的模板 |
| body_data | text |   | NO |   | 内容数据 |
| body_general | text |   | NO |   | 附加数据 |
| image_1 | varchar(255) |   | NO |   | 第一张图片的 URL，一条 feed 最多可以有4张图片。 |
| image_1_link | varchar(255) |   | NO |   | 第一张图片的链接地址 |
| image_2 | varchar(255) |   | NO |   | 第一张图片的链接地址 |
| image_2_link | varchar(255) |   | NO |   | 第二张图片的链接地址 |
| image_3 | varchar(255) |   | NO |   | 第三张图片的 URL |
| image_3_link | varchar(255) |   | NO |   | 第三张图片的链接地址 |
| image_4 | varchar(255) |   | NO |   | 第四张图片的 URL |
| image_4_link | varchar(255) |   | NO |   | 四张图片的链接地址 |
| target_ids | varchar(255) |   | NO |   | 指定给哪些用户(uid)看，如: 1,2,3 |

## uc_friends  关系表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| uid | mediumint(8) unsigned |   | NO |   | 用户id |
| friendid | mediumint(8) unsigned |   | NO |   | 好友id |
| direction | tinyint(1) |   | NO |   | 好友关系标示，1:A加B为好友 2:B加了A为好友 3:A和B彼此都加为了好友 |
| version | int(10) unsigned |   | NO | 是 | 版本号，这个字段已经废除。现作为自增字段。 |
| delstatus | tinyint(1) |   | NO |   | 删除状态 |
| comment | char(255) |   | NO |   | 好友注释 |

## uc_mailqueue  发送邮件队列表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| mailid | int(10) unsigned |   | NO | 是 | 邮件ID |
| touid | mediumint(8) unsigned |   | NO |   | 邮件目标用户id |
| tomail | varchar(32) |   | NO |   | 收件人 |
| frommail | varchar(100) |   | NO |   | 发件人 |
| subject | varchar(255) |   | NO |   | 邮件标题 |
| message | text |   | NO |   | 邮件内容 |
| charset | varchar(15) |   | NO |   | 邮件编码 |
| htmlon | tinyint(1) |   | NO |   | 是否是html格式 |
| level | tinyint(1) | 1 | NO |   | 邮件紧急级别 |
| dateline | int(10) unsigned |   | NO |   | 记录插入时间 |
| failures | tinyint(3) unsigned |   | NO |   | 发送失败次数 |
| appid | smallint(6) unsigned |   | NO |   | 来源应用id |

## uc_memberfields  用户的扩展字段表，扩展 uc_members

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| uid | mediumint(8) unsigned |   | NO |   | 用户ID |
| blacklist | text |   | NO |   | 黑名单列表，用户名存放，以,隔开 |

## uc_members  用户表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| uid | mediumint(8) unsigned |   | NO | 是 | 用户ID |
| username | char(15) |   | NO |   | 用户名 |
| password | char(32) |   | NO |   | 密码 |
| email | char(32) |   | NO |   | 用户Email |
| myid | char(30) |   | NO |   | 漫游id |
| myidkey | char(16) |   | NO |   | 漫游id |
| regip | char(15) |   | NO |   | 注册IP |
| regdate | int(10) unsigned |   | NO |   | 注册时间 |
| lastloginip | int(10) |   | NO |   | 上次登陆的IP(程序转换成数值类型) |
| lastlogintime | int(10) unsigned |   | NO |   | 上次登录的时间 |
| salt | char(6) |   | NO |   | 密码干扰串，用来和密码进行配合验证，防止被暴力破解 |
| secques | char(8) |   | NO |   | 用户的安全提问 |

## uc_mergemembers  需要合并的用户名列表，用来解决应用合并时重名的问题。

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| appid | smallint(6) unsigned |   | NO |   | 应用id |
| username | char(15) |   | NO |   | 重复的用户名 |

## uc_newpm  新短消息表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| uid | mediumint(8) unsigned |   | NO |   | 有新消息的用户 |

## uc_notelist  通知列表，用来将 UCenter 的数据分发到各个应用

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| noteid | int(10) unsigned |   | NO | 是 | 通知ID |
| operation | char(32) |   | NO |   | 操作，如: updatepw|deleteuser|renameuser|test |
| closed | tinyint(4) |   | NO |   | 是否关闭，在通知成功，或者失败重试到极限后，会置为 1 |
| totalnum | smallint(6) unsigned |   | NO |   | 尝试通知的总次数 |
| succeednum | smallint(6) unsigned |   | NO |   | 尝试通知的总次数 |
| getdata | mediumtext |   | NO |   | 通过 GET 方式传递的数据 |
| postdata | mediumtext |   | NO |   | 通过 POST 方式传递的数据 |
| dateline | int(10) unsigned |   | NO |   | 通过 POST 方式传递的数据 |
| pri | tinyint(3) |   | NO |   | 优先级别，tag 相关的通知的优先级别比较低。 |

## uc_pm_indexes  用户短消息索引表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| pmid | mediumint(8) unsigned |   | NO | 是 | 短消息ID |
| plid | mediumint(8) unsigned |   | NO |   | 会话列表ID |

## uc_pm_lists  短消息会话表。

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| plid | mediumint(8) unsigned |   | NO | 是 | 会话列表ID |
| authorid | mediumint(8) unsigned |   | NO |   | 会话作者ID |
| pmtype | tinyint(1) unsigned |   | NO |   | 短消息类型 |
| subject | varchar(80) |   | NO |   | 短消息标题 |
| members | smallint(5) unsigned |   | NO |   | 短消息内容 |
| min_max | varchar(17) |   | NO |   | 会话关系 |
| dateline | int(10) unsigned |   | NO |   | 开始时间 |
| lastmessage | text |   | NO |   | 最后一条短消息内容 |

## uc_pm_members  用户短消息状态表。

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| plid | mediumint(8) unsigned |   | NO |   | 会话列表ID |
| uid | mediumint(8) unsigned |   | NO |   | 会话作者ID |
| isnew | tinyint(1) unsigned |   | NO |   | 是否未读短消息 |
| pmnum | int(10) unsigned |   | NO |   | 会话短消息数目 |
| lastupdate | int(10) unsigned |   | NO |   | 上一次会话时间 |
| lastdateline | int(10) unsigned |   | NO |   | 最后一次会话时间 |

## uc_pm_messages_n  用户短消息数据表。

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| pmid | mediumint(8) unsigned |   | NO |   | 短消息ID |
| plid | mediumint(8) unsigned |   | NO |   | 会话列表ID |
| authorid | mediumint(8) unsigned |   | NO |   | 作者ID |
| message | text |   | NO |   | 短消息内容 |
| delstatus | tinyint(1) unsigned |   | NO |   | 删除状态 1发起者删除, 2他人删除 |
| dateline | int(10) unsigned |   | NO |   | 时间 |

## uc_pms  短消息表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| pmid | int(10) unsigned |   | NO | 是 | 短消息ID |
| msgfrom | varchar(15) |   | NO |   | 发送人用户名 |
| msgfromid | mediumint(8) unsigned |   | NO |   | 发送人id |
| msgtoid | mediumint(8) unsigned |   | NO |   | 接收人id 接收id为0时，表示公共消息 |
| folder | enum('inbox','outbox') | inbox | NO |   | 收件箱/发件箱 |
| new | tinyint(1) |   | NO |   | 接收人是否看过 |
| subject | varchar(75) |   | NO |   | 短消息主题 |
| dateline | int(10) unsigned |   | NO |   | 发送时间 |
| message | text |   | NO |   | 短消息内容 |
| delstatus | tinyint(1) unsigned |   | NO |   | 删除状态，1:表示接受方删除，3:表示双方都已经删除 |
| related | int(10) unsigned |   | NO |   | 关联ID，用来标示哪些短消息关联同一个主题 |
| fromappid | smallint(6) unsigned |   | NO |   | 发信人应用来源APPID |

## uc_protectedmembers  保护用户记录表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| uid | mediumint(8) unsigned |   | NO |   | 用户ID |
| username | char(15) |   | NO |   | 用户名 |
| appid | tinyint(1) unsigned |   | NO |   | 应用ID |
| dateline | int(10) unsigned |   | NO |   | 受保护的时间 |
| admin | char(15) |   | NO |   | 操作的管理员名称 |

## uc_settings  UCenter 的各项设置

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| k | varchar(32) |   | NO |   | 名称 |
| v | text |   | NO |   | 值 |

## uc_sqlcache  缓存mysql查询记录的表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| sqlid | char(6) |   | NO |   | sql 语句的 hash 值 |
| data | char(100) |   | NO |   | 序列化存放的sql语句返回的结果 |
| expiry | int(10) unsigned |   | NO |   | 过期的时间 |

## uc_tags  tag 表

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| tagname | char(20) |   | NO |   | TAG 名称 |
| appid | smallint(6) unsigned |   | NO |   | 应用id |
| data | mediumtext |   | YES |   | 内容 |
| expiration | int(10) unsigned |   | NO |   | tag 过期时间 |

## uc_vars  存放运行期间产生的数据的临时内存表（可以随时清空）

| 字段名 | 数据类型 | 默认值 | 允许非空 | 自动递增 | 备注 |
| ------ | -------- | ------ | -------- | -------- | ---- |
| name | char(32) |   | NO |   | 名称 |
| value | char(255) |   | NO |   | 值 |

