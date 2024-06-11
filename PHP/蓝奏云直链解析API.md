> [!bug] 蓝奏云直链解析 API
> EXE版本--> [[../编程语言/解释型语言/Python/蓝奏云直链生成器|蓝奏云直链生成器]]

```php
<?php //蓝奏云本次于11.23更新
header("Access-Control-Allow-Origin:*");
header('Content-Type:application/json; charset=utf-8');

$url = isset($_GET['url']) ? $_GET['url'] : "";
$pwd = isset($_GET['pwd']) ? $_GET['pwd'] : "";
$type = isset($_GET['type']) ? $_GET['type'] : "";

if (empty($url)) {
  $result = array("success" => false, "message" => "请输入需要解析的蓝奏云链接！");
  exit(json_encode($result,480));
}elseif (strpos($url,'lanzou') == false) {
  $result = array("success" => false, "message" => "你输入的不是蓝奏云链接！");
  exit(json_encode($result,480));
}

//根据传入的蓝奏云链接 自适应获取链接
$urls = parse_url($url);
//一个简单的链接处理
if(strstr($url, '.com/tp/')){
 //判断是否包含/tp
 $url = 'https://'.$urls['host'].'/'.explode('.com/tp/',$url)[1];
}else{
 $url = 'https://'.$urls['host'].'/'.explode('.com/',$url)[1];
}

$softInfo = MloocCurlGet($url);

if (strstr($softInfo, "文件取消分享了") != false) {
 $result = array("success" => false, "message" => "文件取消分享了");
 exit(json_encode($result,480));
}

//判断是否需要文件分享密码
if(strstr($softInfo, "function down_p(){") != false){
 if(empty($pwd)){
 $result = array("success" => false, "message" => "请输入文件分享密码！");
 exit(json_encode($result,480));
}
 //正则获取sign
preg_match_all("/var\s+skdklds\s*=\s*'([^']+)'/i", $softInfo, $segment);
$post_data = array(
"action" => 'downprocess',
"sign" => $segment[1][0],
"p" => $pwd
);
$softDownlink = MloocCurlPost($post_data, "https://".$urls["host"]."/ajaxm.php", $url);
$softName[1] = json_decode($softDownlink,true)['inf'];
preg_match('~<div class="n_filesize">大小：(.*?)</div>~', $softInfo, $softFilesize);
}else{
   preg_match('~style="font-size: 30px;text-align: center;padding: 56px 0px 20px 0px;">(.*?)<\/div>~', $softInfo, $softName);
   preg_match('~<span class="p7">文件大小：</span>(.*?)<br>~', $softInfo, $softFilesize);
   //正则获取链接
   preg_match('/(?<!<!--)<iframe.+?src="(.+?)".+?<\/iframe>/i', $softInfo, $link);
   //获取到的下载链接
   $softDown = MloocCurlGet('https://'.$urls['host'].$link[1]);
   //正则获取sign
   //preg_match_all("/var\s+sasign\s*=\s*'([^']+)'/i", $softDown, $downKeyArr);
   preg_match_all("/'sign':'([^']+)'/i", $softDown, $downKeyArr);

   //post数据
   $post_data = array(
   "action" => 'downprocess',
   "signs"=>'?ctdf',
   "websignkey"=>'Ypvp',
   "sign" => $downKeyArr[1][0],
   );
   $softDownlink = MloocCurlPost($post_data, "https://".$urls["host"]."/ajaxm.php", $url);

}
$softDownlink = json_decode($softDownlink,true);
$downUrl = $softDownlink['dom'] . '/file/' . $softDownlink['url'];

//判断zt值是否为1
if ($softDownlink['zt'] == 1) {
   $infoArr = array('file_name'=>isset($softName[1]) ? $softName[1] : "",'file_size'=>isset($softFilesize[1]) ? $softFilesize[1] : "");
   $result = array("success" => true, 'info' => $infoArr, "download" => $downUrl, "fileUrl" => restoreUrl($downUrl),'copyright'=>$info_copyright);
   if($type !== 'down'){
      exit(json_encode($result,480));
   }else{
      header("Location:$downUrl");
   }
} else {
   $result = array("success" => false, "message" => "文件不存在或获取超时！");
   exit(json_encode($result,480));
}

//HTTP_Get封装方式
function MloocCurlGet($url = '', $UserAgent = '')
{
   $curl = curl_init();
   curl_setopt($curl, CURLOPT_URL, $url);
   curl_setopt($curl, CURLOPT_FOLLOWLOCATION, 1);
   if ($UserAgent != "") {
       curl_setopt($curl, CURLOPT_USERAGENT, $UserAgent);
   }
   $ip = rand(0, 255) . '.' . rand(0, 255) . '.' . rand(0, 255) . '.' . rand(0, 255);
   curl_setopt($curl, CURLOPT_HTTPHEADER, array('X-FORWARDED-FOR:'.$ip, 'CLIENT-IP:'.$ip));
   #关闭SSL
   curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);
   curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
   #返回数据不直接显示
   curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
   $response = curl_exec($curl);
   curl_close($curl);
   return $response;
}
//HTTP_Post封装方式
function MloocCurlPost($post_data = '', $url = '', $ifurl = '', $UserAgent = '')
{
   $curl = curl_init();
   curl_setopt($curl, CURLOPT_URL, $url);
   curl_setopt($curl, CURLOPT_USERAGENT, $UserAgent);
   if ($ifurl != '') {
       curl_setopt($curl, CURLOPT_REFERER, $ifurl);
   }
   $ip = rand(0, 255) . '.' . rand(0, 255) . '.' . rand(0, 255) . '.' . rand(0, 255);
   curl_setopt($curl, CURLOPT_HTTPHEADER, array('X-FORWARDED-FOR:'.$ip, 'CLIENT-IP:'.$ip));
   #关闭SSL
   curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false);
   curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false);
   #返回数据不直接显示
   curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
   curl_setopt($curl, CURLOPT_POST, 1);
   curl_setopt($curl, CURLOPT_POSTFIELDS, $post_data);
   $response = curl_exec($curl);
   curl_close($curl);
   return $response;
}
// 连接转换封装
function restoreUrl($shortUrl)
{
 $ip = rand(0, 255) . '.' . rand(0, 255) . '.' . rand(0, 255) . '.' . rand(0, 255);
 $header[] = "accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9";
 $header[] = "accept-encoding: gzip, deflate, br";
 $header[] = "accept-language: zh-CN,zh;q=0.9";
 $header[] = "cache-control: max-age=0";
 $header[] = "sec-ch-ua: \"Google Chrome\";v=\"95\", \"Chromium\";v=\"95\", \";Not A Brand\";v=\"99\"";
 $header[] = "sec-ch-ua-mobile: ?0";
 $header[] = "sec-ch-ua-platform: \"Windows\"";
 $header[] = "sec-fetch-dest: document";
 $header[] = "CLIENT-IP:" . $ip;
 $header[] = "X-FORWARDED-FOR:" . $ip;
 $ch = curl_init();
 curl_setopt($ch, CURLOPT_URL, $shortUrl);
 curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
 curl_setopt($ch, CURLOPT_USERAGENT, "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.0.0 Safari/537.36"); //设置UA
 curl_setopt($ch, CURLOPT_NOBODY, 1);
 curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
 curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);
 curl_exec($ch);
 $info = curl_getinfo($ch, CURLINFO_EFFECTIVE_URL);
 curl_close($ch);
 return $info;
}
?>
```

 > [!INFO] 接口地址
 > https://www.yuanxiapi.cn/api/lanzou/

 > [!INFO] 请求方式 GET/POST

 > [!INFO] 返回格式 JSON

 > [!INFO] HTTP/HTTPS 支持

 > [!BUG] 请求示例 https://www.yuanxiapi.cn/api/lanzou/?url=https://lanzoui.com/iC0bLyrqmod

  > [!BUG] 带密码请求示例 https://www.yuanxiapi.cn/api/lanzou/?url=https://lanzoui.com/iWQJ808cflgd&pwd=密码

  > [!BUG] 直接下载请求示例 https://www.yuanxiapi.cn/api/lanzou/?url=https://lanzoui.com/iWQJ808cflgd&pwd=密码&type=down

![[ASLant_Images/a4e724f535e3d403f2cf49e62a8f2f94_MD5.jpg]]