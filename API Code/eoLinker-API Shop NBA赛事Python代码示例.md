## eoLinker-API Shop
### 基于Python的NBA赛事API接口调用代码示例
#### 一、接口名称：NBA赛事
#### 二、接口描述：NBA篮球赛事赛程相关信息
#### 三、接口平台：eoLinker-API Shop （apishop.net）

该套接口包含三个接口：

**接口一：按对战球队查询篮球赛事**
**接口二：按年份查询篮球赛事**
**接口三：按球队查询篮球赛事**

**1、接口一：按对战球队查询篮球赛事**

本代码示例是基于Python的eoLinker-API Shop **按对战球队查询篮球赛事** API服务请求的代码示例，使用前你需要：

①：通过https://www.apishop.net/#/api/detail/?productID=125 申请API服务

**以下是完整代码示例：**
```
//post请求
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# 测试环境: python2.7
# 安装requests依赖 => pip install requests/ easy_install requests

# 导入requests依赖
import requests
import json
import sys

reload(sys)
sys.setdefaultencoding("utf-8")
   '''
   转发请求到目的主机
   @param method str 请求方法
   @param url str 请求地址
   @param params dict 请求参数
   @param headers dict 请求头
   '''
   if method == "POST":
       return requests.post(url=url, data=params, headers=headers)
   elif method == "GET":
       return requests.get(url=url, params=params, headers=headers)
   else:
       return None

method = "POST"
url = "https://api.apishop.net/common/basketball/queryBasketballMatchByTeams
headers = None
params = {
   apiKey : "参数1",
   team1 : "参数2",
   team2 : "参数3",
   page : "参数4",
   pageSize : "参数5"
}
result = apishop_send_request(method=method, url=url, params=params, headers=headers)
if result:
   body = result.text
   response = json.loads(body)
   status_code = response["statusCode"]
   if (status_code == "000000"):
       # 状态码为000000, 说明请求成功
       print("请求成功：%s" % (body,))
   else:
       # 状态码非000000, 说明请求失败
       print("请求失败: %s" % (body,))
   else:
       # 返回内容异常，发送请求失败
       print("发送请求失败"")
```

**2、接口二：按年份查询篮球赛事**

本代码示例是基于Python的eoLinker-API Shop **按年份查询篮球赛事** API服务请求的代码示例，使用前你需要：

①：通过https://www.apishop.net/#/api/detail/?productID=125 申请API服务

**以下是完整代码示例：**
```
//post请求
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# 测试环境: python2.7
# 安装requests依赖 => pip install requests/ easy_install requests

# 导入requests依赖
import requests
import json
import sys

reload(sys)
sys.setdefaultencoding("utf-8")
   '''
   转发请求到目的主机
   @param method str 请求方法
   @param url str 请求地址
   @param params dict 请求参数
   @param headers dict 请求头
   '''
   if method == "POST":
       return requests.post(url=url, data=params, headers=headers)
   elif method == "GET":
       return requests.get(url=url, params=params, headers=headers)
   else:
       return None

method = "POST"
url = "https://api.apishop.net/common/basketball/queryBasketballMatchByYear
headers = None
params = {
   apiKey : "参数1",
   year : "参数2",
   page : "参数3",
   pageSize : "参数4"
}
result = apishop_send_request(method=method, url=url, params=params, headers=headers)
if result:
   body = result.text
   response = json.loads(body)
   status_code = response["statusCode"]
   if (status_code == "000000"):
       # 状态码为000000, 说明请求成功
       print("请求成功：%s" % (body,))
   else:
       # 状态码非000000, 说明请求失败
       print("请求失败: %s" % (body,))
   else:
       # 返回内容异常，发送请求失败
       print("发送请求失败"")
```

**3、接口三：按球队查询篮球赛事**

本代码示例是基于Python的eoLinker-API Shop **按球队查询篮球赛事** API服务请求的代码示例，使用前你需要：

①：通过https://www.apishop.net/#/api/detail/?productID=125 申请API服务

**以下是完整代码示例：**
```
//post请求
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# 测试环境: python2.7
# 安装requests依赖 => pip install requests/ easy_install requests

# 导入requests依赖
import requests
import json
import sys

reload(sys)
sys.setdefaultencoding("utf-8")
   '''
   转发请求到目的主机
   @param method str 请求方法
   @param url str 请求地址
   @param params dict 请求参数
   @param headers dict 请求头
   '''
   if method == "POST":
       return requests.post(url=url, data=params, headers=headers)
   elif method == "GET":
       return requests.get(url=url, params=params, headers=headers)
   else:
       return None

method = "POST"
url = "https://api.apishop.net/common/basketball/queryBasketballMatchByTeam
headers = None
params = {
   apiKey : "参数1",
   team : "参数2",
   page : "参数3",
   pageSize : "参数4"
}
result = apishop_send_request(method=method, url=url, params=params, headers=headers)
if result:
   body = result.text
   response = json.loads(body)
   status_code = response["statusCode"]
   if (status_code == "000000"):
       # 状态码为000000, 说明请求成功
       print("请求成功：%s" % (body,))
   else:
       # 状态码非000000, 说明请求失败
       print("请求失败: %s" % (body,))
   else:
       # 返回内容异常，发送请求失败
       print("发送请求失败"")
```