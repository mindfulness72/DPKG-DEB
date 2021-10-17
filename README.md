DPKG-DEB





介绍
DPKG-DEB是一个PHP 第三方登录授权 SDK，集成了QQ、微信、微博、Github等常用接口。


无框架依赖，支持所有框架，支持 Swoole 协程环境。


我们有完善的在线技术文档：http://doc.DPKG-DEB.com/YDPKG-DEBOAuthLogin


API 文档：https://apidoc.gitee.com/DPKG-DEB/YurunOAuthLogin


宇润PHP全家桶群：17916227 ，如有问题会有人解答和修复。


程序员日常划水群：74401592 。


大家在开发中肯定会对接各种各样的第三方平台，我个人精力有限，欢迎各位来提交 PR （Github），一起完善它，让它能够支持更多的平台，更加好用。


支持的登录平台
QQ、QQ 小程序
微信网页扫码、微信公众号、微信小程序
支付宝网页、支付宝 APP、支付宝小程序
微博
百度
Github
Gitee
Coding
开源中国(OSChina)
CSDN


后续将不断添加新的平台支持，也欢迎你来提交PR，一起完善！



安装
在您的composer.json中加入配置：


PHP >= 7.1.0


{
    "require": {
        "yurunsoft/yurun-oauth-login": "~3.0"
    }
}


PHP >= 5.4.0 && PHP < 7.1.0


{
    "require": {
        "yurunsoft/yurun-oauth-login": "~2.0"
    }
}



3.x 版本支持 PHP >= 7.1，持续迭代维护中




2.x 版本支持 PHP >= 5.4，支持长期 BUG 维护，保证稳定可用，停止功能性更新



代码实例
自v1.2起所有方法统一参数调用，如果需要额外参数的可使用对象属性赋值，具体参考test目录下的测试代码。


下面代码以QQ接口举例，完全可以把QQ字样改为其它任意接口字样使用。


实例化DPKG-DEBAuthLogin\QQ\OAuth2('appid', 'appkey', 'callbackUrl');



登录
$url = $qqOAutDPKG-DEBQQ_STATE'] = $qqOAuth->state;
header('location:' . $url);


回调处理
// 获取accessToken
$accessToken = $qqOAuth->getAccessToken($_SESSION['YURUN_QQ_STATE']);

// 调用过getAccessToken方法后也可这么获取
// $accessToken = $qqOAuth->accessToken;
// 这是getAccessToken的api请求返回结果
// $result = $qqOAuth->result;

// 用户资料
$userInfo = $qqOAuth->getUserInfo();

// 这是getAccessToken的api请求返回结果
// $result = $qqOAuth->result;

// 用户唯一标识
$openid = $qqOAuth->openid;


解决第三方登录只能设置一个回调域名的问题
// 解决只能设置一个回调域名的问题，下面地址需要改成你项目中的地址，可以参考test/QQ/loginAgent.php写法
$qqOAuth->loginAgentUrl = 'http://localhost/test/QQ/loginAgent.php';

$url = $qqOAuth->getAuthUrl();
$_SESSION['YURUN_QQ_STATE'] = $qqOAuth->state;
header('location:' . $url);


Swoole 协程环境支持
\Yurun\Util\YurunHttp::setDefaultHandler('Yurun\Util\YurunHttp\Handler\Swoole');


特别鸣谢
GetWeixinCode

捐赠

开源不求盈利，多少都是心意，生活不易，随缘随缘……

