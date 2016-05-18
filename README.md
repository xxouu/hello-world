###判断移动端/pc端/安卓/苹果浏览器的方法总结

js常见的判断移动端或者pc端或者安卓和苹果浏览器的方法总结

js 判断安卓或者ios 之indexOf方式

//判断访问终端
var browser={
    versions:function(){
        var u = navigator.userAgent, app = navigator.appVersion;
        return {
            trident: u.indexOf('Trident') > -1, //IE内核
            presto: u.indexOf('Presto') > -1, //opera内核
            webKit: u.indexOf('AppleWebKit') > -1, //苹果、谷歌内核
            gecko: u.indexOf('Gecko') > -1 && u.indexOf('KHTML') == -1,//火狐内核
            mobile: !!u.match(/AppleWebKit.*Mobile.*/), //是否为移动终端
            ios: !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/), //ios终端
            android: u.indexOf('Android') > -1 || u.indexOf('Linux') > -1, //android终端或者uc浏览器
            iPhone: u.indexOf('iPhone') > -1 , //是否为iPhone或者QQHD浏览器
            iPad: u.indexOf('iPad') > -1, //是否iPad
            webApp: u.indexOf('Safari') == -1, //是否web应该程序，没有头部与底部
            weixin: u.indexOf('MicroMessenger') > -1, //是否微信 （2015-01-22新增）
            qq: u.match(/\sQQ/i) == " qq" //是否QQ
        };
    }(),
    language:(navigator.browserLanguage || navigator.language).toLowerCase()
}
使用方法：
//判断是否IE内核
if(browser.versions.trident){ alert("is IE"); }
//判断是否webKit内核
if(browser.versions.webKit){ alert("is webKit"); }
//判断是否移动端
if(browser.versions.mobile||browser.versions.android||browser.versions.ios){ alert("移动端"); }

js 判断安卓或者ios 之正则表达式方式

if (/(iPhone|iPad|iPod|iOS)/i.test(navigator.userAgent)) {
    //alert(navigator.userAgent);  
   //苹果端
} else if (/(Android)/i.test(navigator.userAgent)) {
    //alert(navigator.userAgent); 
    //安卓端
} else {
   //pc端
};

方法一：纯JS判断
使用这方法既简单，又实用，不需要引入jQuery库，把以下代码加入到<head>里即可。
<script type=”text/javascript”>
if( /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent) ) {
window.location = “mobile.html”; //可以换成http地址
}
</script>

方法二：使用 Device.js 库
device.js 是一个用于检查设备用的插件，使用它你可以很方便的判断设备的操作系统，以及设备是纵向还是横向。

首先，我们下载Device.js

下载地址： https://github.com/matthewhudson/device.js

STEP 1: 引入 JS 文件
<script src=”device.min.js”></script>
STEP 2: 加入判断代码
<script type=”text/javascript”>
if(device.mobile()){
window.location = “shouji.html”;  //可以换成http地址
}
</script>

Device.js 方法有很多，若你想实现对某个设备的判断，要以根据以下代码来替换device.mobile()。

JS判断移动设备最佳方法 并实现跳转至手机版网页

以上两种方法判断手机端都是很实用的，由其是电脑版网页和手机版网页分别用不同的网站域名时，使用该方法可以免去用户记2个域名烦恼！
