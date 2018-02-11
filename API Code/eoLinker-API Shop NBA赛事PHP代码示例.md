## eoLinker-API Shop
### 基于PHP的NBA赛事API接口调用代码示例
#### 一、接口名称：NBA赛事
#### 二、接口描述：NBA篮球赛事赛程相关信息
#### 三、接口平台：eoLinker-API Shop （apishop.net）

该套接口包含三个接口：

**接口一：按对战球队查询篮球赛事**
**接口二：按年份查询篮球赛事**
**接口三：按球队查询篮球赛事**

**1、接口一：按对战球队查询篮球赛事**

本代码示例是基于PHP的eoLinker-API Shop **按对战球队查询篮球赛事** API服务请求的代码示例，使用前你需要：

①：通过https://www.apishop.net/#/api/detail/?productID=125 申请API服务

**以下是完整代码示例：**
```
<?php
$method = "POST";
$url = "https://api.apishop.net/common/basketball/queryBasketballMatchByTeams";
$headers = NULL;
$params = array(
  "apiKey"=>"参数1",
  "team1"=>"参数2",
  "team2"=>"参数3",
  "page"=>"参数4",
  "pageSize"=>"参数5"
);
$result = apishop_curl($method, $url, $headers, $params);
If ($result) {
   $body = json_decode($result["body"], TRUE);
   $status_code = $body["statusCode"];
   If ($status_code == "000000") {
       //状态码为000000, 说明请求成功
       echo "请求成功：" . $result["body"];
   } else {
       //状态码非000000, 说明请求失败
       echo "请求失败：" . $result["body"];
   }
} else {
   //返回内容异常，发送请求失败，以下可根据业务逻辑自行修改
   echo "发送请求失败";
}

/**
  * 转发请求到目的主机
  * @param $method string 请求方法
  * @param $URL string 请求地址
  * @param null $headers 请求头
  * @param null $param 请求参数
  * @return array|bool
  */
function apishop_curl(&$method, &$URL, &$headers = NULL, &$param = NULL)
{
   // 初始化请求
   $require = curl_init($URL);
   // 判断是否HTTPS
   $isHttps = substr($URL, 0, 8) == "https://" ? TRUE : FALSE;
   // 设置请求方式
   switch ($method) {
       case "GET":
           curl_setopt($require, CURLOPT_CUSTOMREQUEST, "GET");
           break;
       case "POST":
           curl_setopt($require, CURLOPT_CUSTOMREQUEST, "POST");
           break;
       default:
           return FALSE;
   }
   if ($param) {
       curl_setopt($require, CURLOPT_POSTFIELDS, $param);
   }
   if ($isHttps) {
       // 跳过证书检查
       curl_setopt($require, CURLOPT_SSL_VERIFYPEER, FALSE);
       // 检查证书中是否设置域名
       curl_setopt($require, CURLOPT_SSL_VERIFYHOST, 2);
   }
   if ($headers) {
   // 设置请求头
   curl_setopt($require, CURLOPT_HTTPHEADER, $headers);
   }
   // 返回结果不直接输出
   curl_setopt($require, CURLOPT_RETURNTRANSFER, TRUE);
   // 重定向
   curl_setopt($require, CURLOPT_FOLLOWLOCATION, TRUE);
   // 把返回头包含再输出中
   curl_setopt($require, CURLOPT_HEADER, TRUE);
   // 发送请求
   $response = curl_exec($require);
   // 获取头部长度
   $headerSize = curl_getinfo($require, CURLINFO_HEADER_SIZE);
   // 关闭请求
   curl_close($require);
   if ($response) {
       // 返回头部字符串
       $header = substr($response, 0, $headerSize);
       // 返回体
       $body = substr($response, $headerSize);
       // 过滤隐藏非法字符
       $bodyTemp = json_encode(array(
            0 => $body
       ));
       $bodyTemp = str_replace("﻿", "", $bodyTemp);
       $bodyTemp = json_decode($bodyTemp, TRUE);
       $body = trim($bodyTemp[0]);
       // 将返回结果头部转成数组
       $respondHeaders = array();
       $header_rows = array_filter(explode(PHP_EOL, $header), "trim");
       foreach ($header_rows as $row) {
           $keylen = strpos($row, ":");
           if ($keylen) {
               $respondHeaders[] = array(
                   "key" => substr($row, 0, $keylen),
                   "value" => trim(substr($row, $keylen + 1))
               );
           }
       }
       return array(
           "headers" => $respondHeaders,
           "body" => $body
       );
   } else {
       return FALSE;
   }
}
```

**2、接口二：按年份查询篮球赛事**

本代码示例是基于PHP的eoLinker-API Shop **按年份查询篮球赛事** API服务请求的代码示例，使用前你需要：

①：通过https://www.apishop.net/#/api/detail/?productID=125 申请API服务

**以下是完整代码示例：**
```
<?php
$method = "POST";
$url = "https://api.apishop.net/common/basketball/queryBasketballMatchByYear";
$headers = NULL;
$params = array(
  "apiKey"=>"参数1",
  "year"=>"参数2",
  "page"=>"参数3",
  "pageSize"=>"参数4"
);
$result = apishop_curl($method, $url, $headers, $params);
If ($result) {
   $body = json_decode($result["body"], TRUE);
   $status_code = $body["statusCode"];
   If ($status_code == "000000") {
       //状态码为000000, 说明请求成功
       echo "请求成功：" . $result["body"];
   } else {
       //状态码非000000, 说明请求失败
       echo "请求失败：" . $result["body"];
   }
} else {
   //返回内容异常，发送请求失败，以下可根据业务逻辑自行修改
   echo "发送请求失败";
}

/**
  * 转发请求到目的主机
  * @param $method string 请求方法
  * @param $URL string 请求地址
  * @param null $headers 请求头
  * @param null $param 请求参数
  * @return array|bool
  */
function apishop_curl(&$method, &$URL, &$headers = NULL, &$param = NULL)
{
   // 初始化请求
   $require = curl_init($URL);
   // 判断是否HTTPS
   $isHttps = substr($URL, 0, 8) == "https://" ? TRUE : FALSE;
   // 设置请求方式
   switch ($method) {
       case "GET":
           curl_setopt($require, CURLOPT_CUSTOMREQUEST, "GET");
           break;
       case "POST":
           curl_setopt($require, CURLOPT_CUSTOMREQUEST, "POST");
           break;
       default:
           return FALSE;
   }
   if ($param) {
       curl_setopt($require, CURLOPT_POSTFIELDS, $param);
   }
   if ($isHttps) {
       // 跳过证书检查
       curl_setopt($require, CURLOPT_SSL_VERIFYPEER, FALSE);
       // 检查证书中是否设置域名
       curl_setopt($require, CURLOPT_SSL_VERIFYHOST, 2);
   }
   if ($headers) {
   // 设置请求头
   curl_setopt($require, CURLOPT_HTTPHEADER, $headers);
   }
   // 返回结果不直接输出
   curl_setopt($require, CURLOPT_RETURNTRANSFER, TRUE);
   // 重定向
   curl_setopt($require, CURLOPT_FOLLOWLOCATION, TRUE);
   // 把返回头包含再输出中
   curl_setopt($require, CURLOPT_HEADER, TRUE);
   // 发送请求
   $response = curl_exec($require);
   // 获取头部长度
   $headerSize = curl_getinfo($require, CURLINFO_HEADER_SIZE);
   // 关闭请求
   curl_close($require);
   if ($response) {
       // 返回头部字符串
       $header = substr($response, 0, $headerSize);
       // 返回体
       $body = substr($response, $headerSize);
       // 过滤隐藏非法字符
       $bodyTemp = json_encode(array(
            0 => $body
       ));
       $bodyTemp = str_replace("﻿", "", $bodyTemp);
       $bodyTemp = json_decode($bodyTemp, TRUE);
       $body = trim($bodyTemp[0]);
       // 将返回结果头部转成数组
       $respondHeaders = array();
       $header_rows = array_filter(explode(PHP_EOL, $header), "trim");
       foreach ($header_rows as $row) {
           $keylen = strpos($row, ":");
           if ($keylen) {
               $respondHeaders[] = array(
                   "key" => substr($row, 0, $keylen),
                   "value" => trim(substr($row, $keylen + 1))
               );
           }
       }
       return array(
           "headers" => $respondHeaders,
           "body" => $body
       );
   } else {
       return FALSE;
   }
}
```

**3、接口三：按球队查询篮球赛事**
   
本代码示例是基于PHP的eoLinker-API Shop **按球队查询篮球赛事** API服务请求的代码示例，使用前你需要：

①：通过https://www.apishop.net/#/api/detail/?productID=125 申请API服务

**以下是完整代码示例：**
```
<?php
$method = "POST";
$url = "https://api.apishop.net/common/basketball/queryBasketballMatchByTeam";
$headers = NULL;
$params = array(
  "apiKey"=>"参数1",
  "team"=>"参数2",
  "page"=>"参数3",
  "pageSize"=>"参数4"
);
$result = apishop_curl($method, $url, $headers, $params);
If ($result) {
   $body = json_decode($result["body"], TRUE);
   $status_code = $body["statusCode"];
   If ($status_code == "000000") {
       //状态码为000000, 说明请求成功
       echo "请求成功：" . $result["body"];
   } else {
       //状态码非000000, 说明请求失败
       echo "请求失败：" . $result["body"];
   }
} else {
   //返回内容异常，发送请求失败，以下可根据业务逻辑自行修改
   echo "发送请求失败";
}

/**
  * 转发请求到目的主机
  * @param $method string 请求方法
  * @param $URL string 请求地址
  * @param null $headers 请求头
  * @param null $param 请求参数
  * @return array|bool
  */
function apishop_curl(&$method, &$URL, &$headers = NULL, &$param = NULL)
{
   // 初始化请求
   $require = curl_init($URL);
   // 判断是否HTTPS
   $isHttps = substr($URL, 0, 8) == "https://" ? TRUE : FALSE;
   // 设置请求方式
   switch ($method) {
       case "GET":
           curl_setopt($require, CURLOPT_CUSTOMREQUEST, "GET");
           break;
       case "POST":
           curl_setopt($require, CURLOPT_CUSTOMREQUEST, "POST");
           break;
       default:
           return FALSE;
   }
   if ($param) {
       curl_setopt($require, CURLOPT_POSTFIELDS, $param);
   }
   if ($isHttps) {
       // 跳过证书检查
       curl_setopt($require, CURLOPT_SSL_VERIFYPEER, FALSE);
       // 检查证书中是否设置域名
       curl_setopt($require, CURLOPT_SSL_VERIFYHOST, 2);
   }
   if ($headers) {
   // 设置请求头
   curl_setopt($require, CURLOPT_HTTPHEADER, $headers);
   }
   // 返回结果不直接输出
   curl_setopt($require, CURLOPT_RETURNTRANSFER, TRUE);
   // 重定向
   curl_setopt($require, CURLOPT_FOLLOWLOCATION, TRUE);
   // 把返回头包含再输出中
   curl_setopt($require, CURLOPT_HEADER, TRUE);
   // 发送请求
   $response = curl_exec($require);
   // 获取头部长度
   $headerSize = curl_getinfo($require, CURLINFO_HEADER_SIZE);
   // 关闭请求
   curl_close($require);
   if ($response) {
       // 返回头部字符串
       $header = substr($response, 0, $headerSize);
       // 返回体
       $body = substr($response, $headerSize);
       // 过滤隐藏非法字符
       $bodyTemp = json_encode(array(
            0 => $body
       ));
       $bodyTemp = str_replace("﻿", "", $bodyTemp);
       $bodyTemp = json_decode($bodyTemp, TRUE);
       $body = trim($bodyTemp[0]);
       // 将返回结果头部转成数组
       $respondHeaders = array();
       $header_rows = array_filter(explode(PHP_EOL, $header), "trim");
       foreach ($header_rows as $row) {
           $keylen = strpos($row, ":");
           if ($keylen) {
               $respondHeaders[] = array(
                   "key" => substr($row, 0, $keylen),
                   "value" => trim(substr($row, $keylen + 1))
               );
           }
       }
       return array(
           "headers" => $respondHeaders,
           "body" => $body
       );
   } else {
       return FALSE;
   }
}
```