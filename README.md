# webrtc-android-demo-apprtc

WebRTC is a free, open project.The source code of this demo is based on official samples(src/samples/androidapp). I have compiled webrtc source to get required .so and .jar files, so you can just build it by android studio.

![demo](https://github.com/duqian291902259/webrtc-android-demo-apprtc/blob/master/screenshot/webrtc-android-demo-as-project.png)

## How to start
This demo is based on WebRTC.the official website: [https://webrtc.org/](https://webrtc.org/)

### How to build and run?
Please clone this project,build it with android stuido,install the target apk files to your devices.

### Overview 
1，go to website : [https://appr.tc/](https://appr.tc/).input your room id(any number).

![webrtc-server](https://github.com/duqian291902259/webrtc-android-demo-apprtc/blob/master/screenshot/appr.tc-webrtc-server.png)

2，open the apprtc app,input the same room id.

![webrtc-android-app](https://github.com/duqian291902259/webrtc-android-demo-apprtc/blob/master/screenshot/AppRTC-android-demo-p2p.png)

3，Experience p2p connectivity with webrtc.

![webrtc p2p connectivity ](https://github.com/duqian291902259/webrtc-android-demo-apprtc/blob/master/screenshot/AppRTC-connectivity.png)


### Development
if you try to compile the source of webrtc,you'll depressed 
at its large size,the total checkout size will be about 16 GB. and more than 30G after compiled.
for more details about getting source code: [https://webrtc.org/native-code/android/](https://webrtc.org/native-code/android/)


if you have installed all required softwares in linux.
let's excute cmds like the follow tips:

```
#!/bin/bash
#duqian2010@gmail.com

export PATH=$PATH:~/webrtc/depot_tools

cd ~/webrtc/android/

fetch --nohooks webrtc_android
gclient sync
gclient runhooks

ls
cd src

git new-branch webrtc_compile
git checkout webrtc_compile

echo "--------------compile config：android，arm-----------------"

gn gen out/arm --args='target_os="android" target_cpu="arm"'

echo "-----------------start compiling webrtc---------------------"

ninja -C out/arm

echo "-----------------compile webrtc done---------------------"

#ninja -C out/arm AppRTCMobile
#build/android/gradle/generate_gradle.py --output-directory $PWD/out/arm --target "//webrtc/examples:AppRTCMobile" --use-gradle-process-resources --split-projects --canary

echo "start copying jar files"
mkdir ../libs/armeabi-v7a/

cp out/arm/lib.java/sdk/android/libjingle_peerconnection_java.jar ../libs/libjingle_peerconnection_java.jar 
cp out/arm/lib.java/rtc_base/base_java.jar ../libs/base_java.jar 
cp out/arm/gen/modules/audio_device/audio_device_java__compile_java.javac.jar ../libs/audio_device_java__compile_java.javac.jar
cp out/arm/lib.java/examples/androidapp/third_party/autobanh/autobanh.jar ../libs/autobanh.jar

echo "start copying so files"

cp out/arm/libjingle_peerconnection_so.so ../libs/armeabi-v7a/libjingle_peerconnection_so.so

echo "task has finished"
exit 0

# scp /Users/duqian/Downloads/webrtc_arm.sh nonolive@192.168.0.18:/home/nonolive/webrtc/android/
```



### Future 
Maybe I will share more articles about webrtc in the future.

### Thanks to WebRTC team！
Dusan's E-mail: duqian2010@gmail.com

WebRTC Demos:[webrtc-android-demo-apprtc](https://github.com/duqian291902259/webrtc-android-demo-apprtc)

