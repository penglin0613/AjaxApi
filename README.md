# AjaxApi

下面列出的接口基本都是可以直接使用的，如有问题记得告诉我哦

## 1. 支持的请求方法

- GET（SELECT）：从服务器取出资源（一项或多项）。
- POST（CREATE）：在服务器新建一个资源。
- PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。
- PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）。
- DELETE（DELETE）：从服务器删除资源。
- HEAD：获取资源的元数据。
- OPTIONS：获取信息，关于资源的哪些属性是客户端可以改变的。

## 2. 通用返回状态说明

| _状态码_ | _含义_                | _说明_                                              |
| -------- | --------------------- | --------------------------------------------------- |
| 200      | OK                    | 请求成功                                            |
| 201      | CREATED               | 创建成功                                            |
| 204      | DELETED               | 删除成功                                            |
| 400      | BAD REQUEST           | 请求的地址不存在或者包含不支持的参数                |
| 401      | UNAUTHORIZED          | 未授权                                              |
| 403      | FORBIDDEN             | 被禁止访问                                          |
| 404      | NOT FOUND             | 请求的资源不存在                                    |
| 422      | Unprocesable entity   | [POST/PUT/PATCH] 当创建一个对象时，发生一个验证错误 |
| 500      | INTERNAL SERVER ERROR | 内部错误                                            |



## 3. 笑话

### 3.1 获取一条随机笑话

> 随机获取笑话的接口

- 请求地址：https://autumnfish.cn/api/joke
- 请求方法：get
- 请求参数：无
- 响应内容：随机笑话



### 3.2 获取多条随机笑话

> 随机获取笑话的接口

- 请求地址：https://autumnfish.cn/api/joke/list
- 请求方法：get
- 请求参数：num

  | 参数名 | 参数说明 | 备注 |
  | :----- | :------- | :----------------------------------- |
  | num | 笑话条数 | 类型为数字,不要给错了 |
- 响应内容：JSON

```json
{
  "msg": "获取5条笑话",
  "jokes": [
    "为什么古装剧里总是有女人会对恩人说：小女子无以为报，唯有以身相许，古代真的存在这种现象吗？ 扯淡，那是因为她喜欢他，要是不喜欢，她就会说：小女子无以为报，唯有来生再报了。",
    "刚才玩了一把狼人杀，网杀。 我是最后一头狼了，悍跳预言家。 游戏已经进行到了三对一，而我主导着好人阵营的风向，本来都已经说好了共同出4。然后我随便刀死一个获得胜利，美滋滋。 结果，在我的发言阶段……正在尽力表演的时候…… 我的舍友突然在旁边大喊了一声…… 卧槽，你居然是狼人！",
    "昨天从外地回来，没回家，今天到家看到老爸醉熏熏地在沙发上。老爸：“什么时候回来的？”我：“昨晚回来的”。他大怒道：“坐碗回来的？怎么不坐盆回来？”我。。。",
    "路上看到一个黑色塑料袋踢了一脚特么是一条睡着的大黑狗，涕泗横流的被追了三里地。",
    "一个胆小紧张的证人正在接受律师的询问。 律师厉声问道：“你是否结过婚？” “是的，我结过一次。”证人声音很小，还有些颤抖。 “那么你和谁结婚了？” “一个女人。” 律师有些发怒，“废话，你当然是和一个女人结婚了。你听说过有谁会和一个男人结婚吗？” 证人颤抖着说：“听说过，我姐姐”。",
  ]
}
```



## 4. 用户

### 4.1 用户验证

> 验证用户名是否可用

- 请求地址：https://autumnfish.cn/api/user/check
- 请求方法：post
- 请求参数：username

| 参数名   | 参数说明 | 备注     |
| :------- | :------- | :------- |
| username | 用户名   | 不能为空 |

- 响应内容：该用户名是否可用



### 4.2 用户注册

> 注册用户

- 请求地址：https://autumnfish.cn/api/user/register
- 请求方法：post
- 请求参数：username

| 参数名   | 参数说明 | 备注     |
| :------- | :------- | :------- |
| username | 用户名   | 不能为空 |

- 响应内容：注册成功或失败

## 5. 英雄

### 5.1 英雄外号查询

> 根据英雄 姓名 查询英雄的 外号
>
> 英雄姓名例如：提莫  洛  霞   凯尔  盖伦

- 请求地址：https://autumnfish.cn/api/hero/simple
- 请求方法：get
- 请求参数：name

| 参数名 | 参数说明 | 备注     |
| :----- | :------- | :------- |
| name   | 英雄名   | 不能为空 |

- 响应内容：英雄的外号



### 5.2 英雄简略信息查询

> 根据英雄 姓名 查询英雄的简略信息

- 请求地址：https://autumnfish.cn/api/hero/info
- 请求方法：get
- 请求参数：name

| 参数名 | 参数说明 | 备注     |
| :----- | :------- | :------- |
| name   | 英雄名   | 不能为空 |

- 响应内容：英雄的简略信息

```json
{
  "title": "迅捷斥候",
  "name": "提莫",
  "bg": "http://img1.dwstatic.com/lol/1512/315320556654/1451366974753.jpg",
  "icon": "http://img.dwstatic.com/lol/1310/246295394773/1382341114833.png",
  "story": "Teemo还有个隐藏被动技能，就是长了个全球嘲讽脸。每次团战必然会被敌方坦克和刺客类英雄集火，你的工作就是要用蘑菇风筝每一个攻击你的人，保持活着，有可能的话顺便杀个人。"
}
```



### 5.3 英雄详情查询

> 根据英雄 姓名 查询英雄的 详细信息

- 请求地址：https://autumnfish.cn/api/hero/detail
- 请求方法：get
- 请求参数：name

| 参数名 | 参数说明 | 备注     |
| :----- | :------- | :------- |
| name   | 英雄名   | 不能为空 |

- 响应内容：英雄的详细信息

```json
{
  "title": "迅捷斥候",
  "name": "提莫",
  "bgs": [
    "http://img1.dwstatic.com/lol/1512/315320556654/1451366974753.jpg",
    "http://img4.dwstatic.com/lol/1512/315320556654/1451366988149.jpg",
    "http://img2.dwstatic.com/lol/1601/317240712104/1453285617943.jpg",
    "http://img3.dwstatic.com/lol/1601/317240712104/1453285624688.jpg",
    "http://img3.dwstatic.com/lol/1601/317240712104/1453285633565.jpg",
    "http://img.dwstatic.com/lol/1601/317240712104/1453285642044.jpg",
    "http://img2.dwstatic.com/lol/1601/317240712104/1453285650321.jpg",
    "http://img5.dwstatic.com/lol/1601/317240712104/1453285656991.jpg",
    "http://img2.dwstatic.com/lol/1601/317240712104/1453285664288.jpg"
  ],
  "tags": ["魔法", "射手"],
  "icons": [
    "http://img.dwstatic.com/lol/1310/246295394773/1382341114833.png",
    "http://img4.dwstatic.com/lol/1512/315320556654/1451366964489.jpg",
    "http://img5.dwstatic.com/lol/1601/317240712104/1453285557655.jpg",
    "http://img2.dwstatic.com/lol/1601/317240712104/1453285565958.jpg",
    "http://img.dwstatic.com/lol/1601/317240712104/1453285572965.jpg",
    "http://img.dwstatic.com/lol/1601/317240712104/1453285579908.jpg",
    "http://img.dwstatic.com/lol/1601/317240712104/1453285586550.jpg",
    "http://img4.dwstatic.com/lol/1601/317240712104/1453285592508.jpg",
    "http://img2.dwstatic.com/lol/1601/317240712104/1453285599012.jpg"
  ],
  "ability": {
    "life": "30",
    "physical": "50",
    "magic": "70",
    "difficulty": "40"
  },
  "story": "Teemo还有个隐藏被动技能，就是长了个全球嘲讽脸。每次团战必然会被敌方坦克和刺客类英雄集火，你的工作就是要用蘑菇风筝每一个攻击你的人，保持活着，有可能的话顺便杀个人。"
}
```



## 6. 克鲁塞德战纪

### 6.1 角色查询

> 根据英雄名查询英雄的 详细信息

- 请求地址：https://autumnfish.cn/api/cq
- 请求方法：get
- 请求参数：query

| 参数名   | 参数说明 | 备注                       |
| :------- | :------- | :------------------------- |
| query    | 英雄名   | 可以为空，为空获取所有数据 |

- 响应内容：JSON

```json
{
  "msg": "获取成功",
  "list": [
    {
      "name": "阎罗使者桂香",
      "icon": "http://p0.qhimg.com/dr/72__/t01d483a1c02dff97d3.png",
      "skill": "恶灵退散"
    },
    {
      "name": "自然的纳兹伦",
      "icon": "http://p7.qhimg.com/dr/72__/t01b33aca0e6daa64a4.png",
      "skill": "狩猎律动"
    },
    {
      "name": "黑桃王后爱丽丝",
      "icon": "http://p5.qhimg.com/dr/72__/t0142106a779023b5d6.png",
      "skill": "命运"
    },
    {
      "name": "稀世怪盗路尼昂",
      "icon": "http://p1.qhimg.com/dr/72__/t01dd39d1a917845d58.png",
      "skill": "怪盗出现"
    },
    {
      "name": "丰饶女神德米特尔",
      "icon": "http://p5.qhimg.com/dr/72__/t018014a8cbb95f7aa5.png",
      "skill": "麦田守卫者"
    },
    {
      "name": "魔法傀儡师贝萝特",
      "icon": "http://p4.qhimg.com/dr/72__/t0198b29952d7d17927.png",
      "skill": "傀儡术"
    }
  ]
}
```





### 6.2 根据类型查询角色

> 根据英雄类型查询英雄的 详细信息

- 请求地址：https://autumnfish.cn/api/cq/category
- 请求方法：get
- 请求参数：type

| 参数名 | 参数说明 | 备注                                                  |
| :----- | :------- | :---------------------------------------------------- |
| type   | 英雄类型 | 不能为空，可选值有:剑士，骑士，弓手，猎人，法师，祭司 |

- 响应内容：JSON

```json
{
    "msg": "获取法师英雄数据",
    "code": 200,
    "data": {
        "heros": [
            {
            "heroName": "黑袍魔女桃乐丝",
            "heroIcon": "http://p4.qhimg.com/dr/72__/t015a7af93e23e5c67c.png",
            "skillName": "奥能脉冲",
            "skillIcon": "http://p3.qhimg.com/dr/52__/t01179c3d8588da2733.png",
            "weaponName": "月之女王",
            "weaponIcon": "http://p2.qhimg.com/dr/45__/t01a05a602fe8a972b8.png"
            },
        ]
}
```



### 6.3 角色技能动态图查询

> 根据英雄名查询英雄的 技能动态图

- 请求地址：https://autumnfish.cn/api/cq/gif
- 请求方法：get
- 请求参数：name

| 参数名   | 参数说明 | 备注                       |
| :------- | :------- | :------------------------- |
| name    | 英雄名   | 不能为空   |


- 响应内容：JSON

```json
{
  "data": {
      "skillGif": "http://p7.qhimg.com/dr/340__/t019779314457e6a37d.gif",
      "heroName": "八神庵"
  },
  "msg": "八神庵的技能图片获取成功",
  "code": 200
}
```





## 7. 随机二次元图片获取

[原接口地址文档地址](http://acg.bakayun.cn/)，此接口只是整理了网上的免费接口，并把文档调整了格式

* 请求地址:http://acg.bakayun.cn/randbg.php
* 请求方法：get
* 请求参数：Type,t,https

| 参数名 | 参数说明      | 备注                                                         |
| :----- | :------------ | :----------------------------------------------------------- |
| Type   | 类型          | 301 = 301跳转(301 Moved Permanently)<br/> 302 = 302跳转<br/> json = JSON数据 |
| t      | 专辑          | dfproject = 东方16:9壁纸(495张) <br/>dfzh = 东方竖图(6239张) <br/>ecyzh = 二次元综合(1991张)<br/> 不填 = 全部图片随机 |
| https  | 是否使用https | true或者为空                                                 |

- 响应内容:根据设置的结果会略有区别

```json
{
    "ImgUrl": "http://img.badapple.top/东方Project/八坂神奈子/img (11).jpg",
    "Color": "175,133,124"
}
```



## 8. 获取 json 格式的天气

   根据城市名获取 城市天气

- 请求地址：http://wthrcdn.etouch.cn/weather_mini
- 请求方法：get
- 请求参数：city

| 参数名 | 参数说明     | 备注                                       |
| :----- | :----------- | :----------------------------------------- |
| City   | 查询的城市名 | 不能为空，不能写错(注意是城市名不是省份名) |

- 响应内容：json

```json
{
  "data": {
    "yesterday": {
      "date": "15日星期三",
      "high": "高温 31℃",
      "fx": "无持续风向",
      "low": "低温 26℃",
      "fl": "<![CDATA[<3级]]>",
      "type": "多云"
    },
    "city": "深圳",
    "forecast": [
      {
        "date": "16日星期四",
        "high": "高温 32℃",
        "fengli": "<![CDATA[<3级]]>",
        "low": "低温 27℃",
        "fengxiang": "无持续风向",
        "type": "阵雨"
      },
      {
        "date": "17日星期五",
        "high": "高温 32℃",
        "fengli": "<![CDATA[<3级]]>",
        "low": "低温 27℃",
        "fengxiang": "无持续风向",
        "type": "雷阵雨"
      },
      {
        "date": "18日星期六",
        "high": "高温 32℃",
        "fengli": "<![CDATA[<3级]]>",
        "low": "低温 27℃",
        "fengxiang": "无持续风向",
        "type": "雷阵雨"
      },
      {
        "date": "19日星期天",
        "high": "高温 32℃",
        "fengli": "<![CDATA[<3级]]>",
        "low": "低温 25℃",
        "fengxiang": "无持续风向",
        "type": "雷阵雨"
      },
      {
        "date": "20日星期一",
        "high": "高温 29℃",
        "fengli": "<![CDATA[<3级]]>",
        "low": "低温 24℃",
        "fengxiang": "无持续风向",
        "type": "阵雨"
      }
    ],
    "ganmao": "各项气象条件适宜，发生感冒机率较低。但请避免长期处于空调房间中，以防感冒。",
    "wendu": "30"
  },
  "status": 1000,
  "desc": "OK"
}
```



## 9.获取 xml 格式菜单

- 请求地址：https://autumnfish.cn/api/food.xml

- 请求方法：get
- 请求参数：无



- 响应内容：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<breakfast_menu>
	<food>
		<name>Belgian Waffles</name>
		<price>$5.95</price>
		<description>Two of our famous Belgian Waffles with plenty of real maple syrup</description>
		<calories>650</calories>
	</food>
	<food>
		<name>Strawberry Belgian Waffles</name>
		<price>$7.95</price>
		<description>Light Belgian waffles covered with strawberries and whipped cream</description>
		<calories>900</calories>
	</food>
	<food>
		<name>Berry-Berry Belgian Waffles</name>
		<price>$8.95</price>
		<description>Light Belgian waffles covered with an assortment of fresh berries and whipped cream</description>
		<calories>900</calories>
	</food>
	<food>
		<name>French Toast</name>
		<price>$4.50</price>
		<description>Thick slices made from our homemade sourdough bread</description>
		<calories>600</calories>
	</food>
	<food>
		<name>Homestyle Breakfast</name>
		<price>$6.95</price>
		<description>Two eggs, bacon or sausage, toast, and our ever-popular hash browns</description>
		<calories>950</calories>
	</food>
</breakfast_menu>

```



## 10. 图灵机器人

> 智能机器人接口，使用需要注册，官网地址是 [http://www.turingapi.com/](http://www.turingapi.com/)

- 请求地址：http://www.tuling123.com/openapi/api
- 请求方法：post
- 请求参数：key,info

| 参数名 | 参数说明           | 备注     |
| :----- | :----------------- | :------- |
| key    | 申请的机器人 key   | 不能为空 |
| info   | 要跟机器人聊的内容 |          |

- 响应内容：聊天的信息

```json
{ "code": 100000, "text": "你好吗" }
```

测试用 key：如果次数都用完了建议自己注册一个机器人即可，免费的

- bb2067dc6a1a47cca31ecdff91cc07a8
- dc503c455cad44b1a028b651613aded8
- caf4e221ccca4e46a5eafbd7b2ff65a0
- 932f61cbc52b46a4bccc6e166a210c5b
- d7c82ebd8b304abeacc73b366e42b9ed  (每天5000条)
