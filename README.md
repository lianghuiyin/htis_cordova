—jdk版本号为1.7

java version "1.7.0_79"

Java(TM) SE Runtime Environment (build 1.7.0_79-b15)

Java HotSpot(TM) 64-Bit Server VM (build 24.79-b02, mixed mode)

-常用指令
新建项目:
cordova create htis com.horizon.htis 加油
添加平台:
cordova platform add android
添加插件:
cordova plugin add cordova-plugin-splashscreen
cordova plugin add cordova-plugin-whitelist
生成项目:
cordova build android
运行项目:
cordova run android
打开九宫图制作工具:
draw9patch


—生成密钥

YinLiangHuideMacBook-Air:keystore yinlianghui$ keytool -genkey -v -keyalg DSA -keysize 1024 -sigalg SHA1withDSA  -validity 20000  -keystore horizon.keystore -alias horizon   -keypass pwd -storepass pwd

您的名字与姓氏是什么?

  [Unknown]:  xxx

您的组织单位名称是什么?

  [Unknown]:  xxx

您的组织名称是什么?

  [Unknown]:  xxx

您所在的城市或区域名称是什么?

  [Unknown]:  xx

您所在的省/市/自治区名称是什么?

  [Unknown]:  xx

该单位的双字母国家/地区代码是什么?

  [Unknown]:  zh

CN=xx, OU=xx, O=xx, L=xx, ST=xx, C=xx是否正确?

  [否]:  Y



正在为以下对象生成 1,024 位DSA密钥对和自签名证书 (SHA1withDSA) (有效期为 20,000 天):

CN=xx, OU=xx, O=xx, L=xx, ST=xx, C=xx

[正在存储horizon.keystore]

YinLiangHuideMacBook-Air:keystore yinlianghui$ 

-build
YinLiangHuideMacBook-Air:~ yinlianghui$ cd documents/phonegap-apps/htis
YinLiangHuideMacBook-Air:htis yinlianghui$ cordova build android --release

-copy to dist
YinLiangHuideMacBook-Air:htis yinlianghui$ cp platforms/android/build/outputs/apk/android-release-unsigned.apk dist/htis.apk

—签名
YinLiangHuideMacBook-Air:htis yinlianghui$ jarsigner  -verbose -sigalg SHA1withDSA -digestalg SHA1  -keystore dist/horizon.keystore -storepass pwd dist/htis.apk horizon

—验证签名
YinLiangHuideMacBook-Air:htis yinlianghui$ jarsigner -verbose -verify  dist/htis.apk

-优化
YinLiangHuideMacBook-Air:htis yinlianghui$ /Users/yinlianghui/Library/Android/sdk/build-tools/22.0.1/zipalign -v 4 dist/htis.apk dist/htis_v1.2.8.apk;


