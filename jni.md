



# 配置app的 build.gradle

```
Android {
	defaultConfig {
		ndk{
            moduleName "Hello" //so文件: lib+moduleName+.so
            abiFilters "armeabi", "armeabi-v7a","arm64-v8a","x86_64", "x86" //cpu的类型
        }
	}
	//指定要链入的so路径
	sourceSets {
        main {
            //jni.srcDirs = ['libs']
            jniLibs.srcDirs = ['src/libs']
        }
    }
}
# 生成头文件

```
String s = new JniKit().sayHello();
Log.d("dd", s);

public class JniKit {

    static {
        System.loadLibrary("Hello");
    }
    public native String sayHello();
}

javah -classpath ~/AndroidStudioProjects/microtime/app/src/main/java/ -d ./jni -jni microtime.jj.com.microtime.JniKit 

# 在jni 中配置 Android.mk    

一个最基本的配置 

```
LOCAL_PATH := $(call my-dir)
 
include $(CLEAR_VARS)
 
LOCAL_MODULE    := Hello
LOCAL_SRC_FILES := Hello.c

LOCAL_MODULE_PATH := $(my-dir)  
 
include $(BUILD_SHARED_LIBRARY)


# 编译

```
 ~/Library/Android/sdk/ndk-bundle/ndk-build -C app/src/jni -j   

# build gradle

# apktool 反解apk包，查看so文件是否有打包

地址：https://ibotpeaches.github.io/Apktool/install/

apktool d -f app-debug.apk
