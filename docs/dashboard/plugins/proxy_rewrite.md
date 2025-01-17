# 转发重写

### 插件信息

| 名称     | 字段          | 属性     |
| -------- | ------------- | -------- |
| 转发重写 | proxy_rewrite | 参数处理 |

### 功能描述

该插件用于对上游代理信息进行重写，支持对 `uri`、`host` 的重写，同时支持对转发请求头部header的值进行新增,修改或者删除。

注意事项：

* 对uri的重写支持静态重写，正则替换



### 配置参数说明

| 参数名    | 说明                                                         | 是否必填 | 默认值 | 值可能性     |
| --------- | ------------------------------------------------------------ | -------- | ------ | ------------ |
| uri       | 设置转发请求的新uri地址                                      | 否       |        | string       |
| regex_uri | 对原uri进行正则替换并将其设置到转发请求的新uri地址。该字符串数组有两个值，第一个表示匹配请求的uri所需要的正则表达式，第二个表示匹配成功后所需要的uri替换正则表达式。 | 否       |        | array_string |
| host      | 设置转发请求的新host地址                                     | 否       |        | string       |
| headers   | 能对转发请求的头部值进行新增或删除                           | 否       |        | object       |

**注意事项**：

* uri和regex_uri均用于修改uri，若都配置了，则uri的值优先。
* **headers配置字段**：能对转发请求的头部值进行新增,修改或删除
  * **新增，修改**：直接设置键值对即可。需要注意的是对以下特殊头部的修改只会在原有值的末尾添加上新值，除此之外的头部值会直接进行覆盖。
    * Content-Type
    * Content-Length
    * Connection
    * Cookie
    * Transfer-Encoding
    * Host
    * User-Agent

  * **删除**：配置的键值对里的值为空字符串时，即为删除指定头部

### 全局开启转发重写插件

![](http://data.eolinker.com/course/8yFRv9P8ce476d51deb01c88f29fccf9c5a00044fa49bd9.gif)

### 配置带有转发重写插件的服务

**配置说明**：将转发请求的路径`uri`设置为`/apinto/demo` ,`host`设置为 `127.0.0.1`，同时请求头部中新增`apinto:demo`。

![](http://data.eolinker.com/course/pGNdXtL71a32424aab010aff421925021a215ad3d2eb3a0.gif)

