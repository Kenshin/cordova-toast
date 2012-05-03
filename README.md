Cordova-Toast
=============

PhoneGap Toast for cordova适用于1.5以上的cordova版本。

在[PhoneGap-Toast](https://github.com/m00sey/PhoneGap-Toast)的基础上，修改为对cordova(1.5版本以上)的支持。

使用方法：  
与[PhoneGap-Toast](https://github.com/m00sey/PhoneGap-Toast)一样。

修改地方：  
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

----------------------------------------------
联系方式：
* **博客** [k-zone.cn](http://www.k-zone.cn/zblog)
* **微博** [新浪微博](http://weibo.com/23784148)
