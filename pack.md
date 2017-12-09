# AndroidStudio多渠道打包

基于友盟统计实施

* 在AndroidManifest.xml里设置动态渠道变量
```
	<meta-data
    android:name="UMENG_CHANNEL"
    android:value="${UMENG_CHANNEL_VALUE}" />
```

* 在build.gradle设置productFlavors

```    
android {  
    productFlavors {
        huawei {
            manifestPlaceholders = [UMENG_CHANNEL_VALUE: "huawei"]
        }
        tencent {
            manifestPlaceholders = [UMENG_CHANNEL_VALUE: "tencent"]
        }
        xiaomi {
            manifestPlaceholders = [UMENG_CHANNEL_VALUE: "xiaomi"]
        }
        360 {
            manifestPlaceholders = [UMENG_CHANNEL_VALUE: "360"]
        }
        baidu {
            manifestPlaceholders = [UMENG_CHANNEL_VALUE: "baidu"]
        }
        wandoujia {
            manifestPlaceholders = [UMENG_CHANNEL_VALUE: "wandoujia"]
        }
    }  
}
```
* 打包操作

AndroidStudio>Build>Generate signed APK

or

AndroidStudio/Terminal/gradlew assembleRelease


* 签名

在build.gradle文件中配置签名信息


```
signingConfigs {
        release{
            storeFile file("../app_keystore") //签名文件路径
            storePassword "abcdefg"
            keyAlias "abcdefg"
            keyPassword "abcdefg"  //签名密码
        }
    }

```
重新执行gradlew assembleRelease命令，得到加签的包


(学习的网站)[http://stormzhang.com/devtools/2015/01/15/android-studio-tutorial6/]
