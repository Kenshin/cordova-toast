##Cordova-Toast
在[PhoneGap-Toast](https://github.com/m00sey/PhoneGap-Toast)的基础上，修改为对cordova(1.5版本以上)的支持。

### 使用方法：  
与[PhoneGap-Toast](https://github.com/m00sey/PhoneGap-Toast)一样。

### 修改地方：  
phonegap-toast.js改名为cordova-toast.js，其内容为
<pre>
var ToastPlugin = function() {
};

ToastPlugin.prototype.show_long = function(message, win, fail) {
  cordova.exec(win, fail, "ToastPlugin", "show_long", [message]);
};

ToastPlugin.prototype.show_short = function(message, win, fail) {
  cordova.exec(win, fail, "ToastPlugin", "show_short", [message]);
};

cordova.addConstructor(function() { 
  // Register the javascript plugin with cordova
  cordova.addPlugin('ToastPlugin', new ToastPlugin());

  // Register the native class of plugin with cordova
  navigator.app.addService("ToastPlugin", "com.chariotsolutions.toast.plugin.ToastPlugin"); 
});
</pre>

在ToastPlugin.java增加
<pre>
import android.content.Context;
</pre>

修改
<pre>
Toast.makeText(ctx, message, length).show();
</pre>
为
<pre>
Toast.makeText((Context)ctx, message, length).show();
</pre>

## 更新日志：
version 1.0 [2012-05-03]
* 基于[PhoneGap-Toast](https://github.com/m00sey/PhoneGap-Toast)
* 适合cordova 1.5+

## 联系方式：
* 博客：[k-zone.cn](http://www.k-zone.cn/zblog)
* 微博：[新浪微博](http://weibo.com/23784148)
* 联络：kenshin[AT]ksria.com

## 版权和许可：
Copyright 2012 [k-zone.cn](http://www.k-zone.cn/zblog)  
Licensed under MIT or GPL Version 2 licenses