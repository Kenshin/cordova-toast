Cordova-Toast
=============

PhoneGap Toast for cordova������1.5���ϵ�cordova�汾��

��[PhoneGap-Toast](https://github.com/m00sey/PhoneGap-Toast)�Ļ����ϣ��޸�Ϊ��cordova(1.5�汾����)��֧�֡�

ʹ�÷�����  
��[PhoneGap-Toast](https://github.com/m00sey/PhoneGap-Toast)һ����

�޸ĵط���  
phonegap-toast.js����Ϊcordova-toast.js��������Ϊ
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

��ToastPlugin.java����
<pre>
import android.content.Context;
</pre>

�޸�
<pre>
Toast.makeText(ctx, message, length).show();
</pre>
Ϊ
<pre>
Toast.makeText((Context)ctx, message, length).show();
</pre>

----------------------------------------------
��ϵ��ʽ��
* ���ͣ�[k-zone.cn](http://www.k-zone.cn/zblog)
* ΢����[����΢��](http://weibo.com/23784148)
