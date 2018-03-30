<a href="art/logo.jpg"><img src="art/logo.jpg" width="100%"/></a>

<p align="center">
<a href="http://developer.android.com/index.html"><img src="https://img.shields.io/badge/platform-android-green.svg"></a>
<a href="https://jitpack.io/#lizixian18/MusicLibrary"><img src="https://jitpack.io/v/lizixian18/MusicLibrary.svg"></a>
<a href="http://choosealicense.com/licenses/mit/"><img src="https://img.shields.io/badge/license-MIT-green.svg"></a>
</p>

# MusicLibrary

一个比较完善的音乐播放封装库，针对快速集成音频播放功能。  

- 基于 IPC 实现音频服务，减少app的内存峰值，避免OOM。
- 集成和调用 API 非常简单，几乎一句话就可以把音频功能集成好了。
- 提供了丰富的 API 方法，轻松实现各种功能。
- 一句话集成自定义通知栏和系统通知栏，可以自定义对通知栏的控制。
- 集成 MediaPlayer 和 ExoPlayer 两个播放器，可自由切换
- 支持多种音频格式，支持音频直播。

### WorkPlan




    

#### Demo
具体应用 Demo 请参考 [NiceMusic](https://github.com/lizixian18/NiceMusic)

#### 导入
```java
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}

dependencies {
     compile 'com.github.lizixian18:MusicLibrary:v1.2.5'
}
```
[![](https://jitpack.io/v/lizixian18/MusicLibrary.svg)](https://jitpack.io/#lizixian18/MusicLibrary)

#### 文档
1. 集成方法：
  ```java
    
    
    在 Application 中完成初始化，会自动开启音乐服务和初始化：
    
    if (!BaseUtil.getCurProcessName(this).contains(":musicLibrary")) {
        MusicManager.get().setContext(this).init();
    }
    
    其中，一定要调用 setContext 设置上下文，否则会报错。 
    因为音乐服务是运行在 musicLibrary 进程里面的，多进程的情况下，Application 会创建多次， 
    所以需要加上以上判断，在非 musicLibrary 进程里面初始化。
      
    初始化的时候还有一些参数可以配置：  
    
    setAutoPlayNext(boolean autoPlayNext) 是否在播放完当前歌曲后自动播放下一首
    setUseMediaPlayer(boolean isUseMediaPlayer) 是否使用 MediaPlayer
    setNotificationCreater(NotificationCreater creater) 通知栏配置
    
    （通过 MusicManager 去调用 lib 中所有的 api ，静态方法可以直接调用，
      非静态方法需要通过 MusicManager.get() 去调用。）
  ```
  
2. Model字典
 
   详细见 [Model字典说明](https://github.com/lizixian18/MusicLibrary/blob/master/readme/model.md)
   
3. 播放器API
   
   详细见 [API说明](https://github.com/lizixian18/MusicLibrary/blob/master/readme/api.md)
 
4. 通知栏集成

   详细见 [通知栏集成](https://github.com/lizixian18/MusicLibrary/blob/master/readme/notification.md)

5. 代码实现以及原理
  
   详细见 [代码实现以及原理](https://github.com/lizixian18/MusicLibrary/blob/master/readme/principle.md)




<br><br><br>

PS：
- 如果你有想法或者意见和建议，欢迎提issue，喜欢点个star。欢迎各位大佬指点指点。

#### About me
An android developer in GuangZhou  
简书：[http://www.jianshu.com/users/286f9ad9c417/latest_articles](http://www.jianshu.com/users/286f9ad9c417/latest_articles)   
Email:386707112@qq.com  
If you want to make friends with me, You can give me a Email and follow me。


#### License
```
Copyright 2018 L_Xian   

Licensed under the Apache License, Version 2.0 (the "License");  
you may not use this file except in compliance with the License.  
You may obtain a copy of the License at  

http://www.apache.org/licenses/LICENSE-2.0  

Unless required by applicable law or agreed to in writing, software  
distributed under the License is distributed on an "AS IS" BASIS,  
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.  
See the License for the specific language governing permissions and  
limitations under the License.
```