+++
title = "Hello JDK 9"
description = ""
date = 2012-10-02
+++


 چند وقتی می شه که از انتشار نسخه پایدار jdk9 می گذره.
 ( ۲۱ سپتامبر ۲۰۱۷)
 
 بعد از ۳ سال و کلی کش و قوس و چندین بار عقب انداختن   نسخه ۹ زبان برنامه نویسی جاوا منتشر شد.
 
  می خایم یه نگاهی به تغییراتی که کرده و ویژگهی های که بهش اضافه شده داشته باشیم.
  
 اول از مهم ها شروع می کنیم
 
### Project Jigsaw
 
 راستش مهم ترین تغییر این نسخه از جاوا متاسفانه مربوط به خود زبان جاوا نیست
 و مربوط به پلتفرم JDK می باشد.
 در واقع پروژه jigsaw اینه که خود پتلفرم جاوا رو به ماژول های مختلفی تقسیم کنند.
 دلیل انجام این کار هم کاهش مصرف حافظه و سریع ترین کردن سرعت بوت رانتایم جاوا بوده.

حالا چطوری ؟ با ماژولار شدن پلتفرم JDK شما می تونید یه Runtime مخصوص واسه برنامه خودتون ایجاد کنید که فقط شامل ماژول های بشه که کد شما برای اجرا بهش نیاز داره.


   زمانی که شما OpenJDK9 رو دانلود کردید با زدن دستور java --list-modules می تونید تمامی ماژول های جاوا رو مشاهده بکنید :
 

 ```
 java.activation@9
 java.base@9
 java.compiler@9
 java.corba@9
 java.datatransfer@9
 java.desktop@9
 java.instrument@9
 java.jnlp@9
 java.logging@9
 java.management@9
 java.management.rmi@9
 java.naming@9
 java.prefs@9
 java.rmi@9
 java.scripting@9
 java.se@9
 java.se.ee@9
 java.security.jgss@9
 java.security.sasl@9
 java.smartcardio@9
 java.sql@9
 java.sql.rowset@9
 java.transaction@9
 java.xml@9
 java.xml.bind@9
 java.xml.crypto@9
 java.xml.ws@9
 java.xml.ws.annotation@9
 javafx.base@9
 javafx.controls@9
 javafx.deploy@9
 javafx.fxml@9
 javafx.graphics@9
 javafx.media@9
 javafx.swing@9
 javafx.web@9
 jdk.accessibility@9
 jdk.attach@9
 jdk.charsets@9
 jdk.compiler@9
 jdk.crypto.cryptoki@9
 jdk.crypto.ec@9
 jdk.deploy@9
 jdk.deploy.controlpanel@9
 jdk.dynalink@9
 jdk.editpad@9
 jdk.hotspot.agent@9
 jdk.httpserver@9
 jdk.incubator.httpclient@9
 jdk.internal.ed@9
 jdk.internal.jvmstat@9
 jdk.internal.le@9
 jdk.internal.opt@9
 jdk.internal.vm.ci@9
 jdk.jartool@9
 jdk.javadoc@9
 jdk.javaws@9
 jdk.jcmd@9
 jdk.jconsole@9
 jdk.jdeps@9
 jdk.jdi@9
 jdk.jdwp.agent@9
 jdk.jfr@9
 jdk.jlink@9
 jdk.jshell@9
 jdk.jsobject@9
 jdk.jstatd@9
 jdk.localedata@9
 jdk.management@9
 jdk.management.agent@9
 jdk.naming.dns@9
 jdk.naming.rmi@9
 jdk.net@9
 jdk.pack@9
 jdk.packager@9
 jdk.packager.services@9
 jdk.plugin@9
 jdk.plugin.dom@9
 jdk.plugin.server@9
 jdk.policytool@9
 jdk.rmic@9
 jdk.scripting.nashorn@9
 jdk.scripting.nashorn.shell@9
 jdk.sctp@9
 jdk.security.auth@9
 jdk.security.jgss@9
 jdk.snmp@9
 jdk.unsupported@9
 jdk.xml.bind@9
 jdk.xml.dom@9
 jdk.xml.ws@9
 jdk.zipfs@9
 oracle.desktop@9
 oracle.net@9
```
  

برای مثال اگه یه REST-API می نویسید دیگه کد شما نیازی به API نوشتن اپلیکیشن دستکتاپ ( مثل Swing , AWT , JavaFX) نداره قاعدتا یا بخش های دیگه جاوا . 
  
  یا یه نرم افزار کامندلاین می خاید بنویسید که سبک باشه و کم حجم و حافظه کمتری مصرف کنه و کار ساده ای می خاد بکنه می یاید به رانتایم می سازید براش از جاوا که فقط شامل ماژول java.core هستش.
  و به جای این که یه JRE ه ۶۰-۷۰ مگاباتی رو هنگام نصب بخاد شما می تونید یه JRE با ۲۴ مگ که فقط شامل java.core هستش کنارش بگذارید.
  
 
 
  
  درسته که jigsaw توی زبان جاوا تغییری ایجاد نمی کنه ولی باعث می شه نرم افزارهای نوشته شده به زبان جاوا از منابع کمتری مصرف کنند و کم حجم تر و سریع تر بارگذاری شوند.

الان خود برنامه نویس ها هم می تونن نرم افزارهاشون رو بر اساس همین سیستم ماژول بندی کنن.

و یه ویژگی که jigsaw داره اینه که هر ماژول می تونه یک سری API خصوصی واسه خودش داشته باشه که از بیرون قابل دسترسی نباشه و فقط داخل همون ماژول بشه ازش استفاده کرد.
و می شه تایین کرد که فقط این package name بیرون از ماژول قابل مشاهده و استفاده باشه (‌توسط ماژول های دیگه).

هر ماژول شامل یه فایل به اسم module-info.java هستش که برای مثال همچین چیزی می تونه باشه :

module com.baeldung.student.service.dbimpl {
    requires transitive com.baeldung.student.service;
    requires java.logging;
    exports com.baeldung.student.service.dbimpl;
}

همچنین هر ماژول می تونه بگه که به کدوم ماژول ها نیاز داره.
البته بحث مدیریت وابستگی ها  که چیز جدیدی نیست و تو اکثر Build System ها مثل Maven و Gradle وجود داشت.
  
   
 یه سری ابزار هم اضافه شدن به JDK9 که می تونید ازشون استفاده کنید :
 
 - jlink
 - jdeps
 - jdeprscan
 - jmod 
 
 