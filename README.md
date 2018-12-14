# UserAwareVideoView
[![Build Status](https://travis-ci.org/kevalpatel2106/UserAwareVideoView.svg?branch=master)](https://travis-ci.org/kevalpatel2106/UserAwareVideoView) [ ![Download](https://api.bintray.com/packages/kevalpatel2106/maven/user-aware-videoview/images/download.svg) ](https://bintray.com/kevalpatel2106/maven/user-aware-videoview/_latestVersion) [![Hex.pm](https://img.shields.io/hexpm/l/plug.svg)](https://github.com/kevalpatel2106/UserAwareVideoView) [![API](https://img.shields.io/badge/API-15%2B-orange.svg?style=flat)](https://android-arsenal.com/api?level=15) <a href="http://www.methodscount.com/?lib=com.kevalpatel2106%3Auserawarevideoview%3A1.0.2"><img src="https://img.shields.io/badge/Methods count-core: 141 | deps: 23914-e91e63.svg"/></a> <a href="http://www.methodscount.com/?lib=com.kevalpatel2106%3Auserawarevideoview%3A1.0.2"><img src="https://img.shields.io/badge/Size-29 KB-e91e63.svg"/></a>



## Featured in:
- [![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-UserAwareVideoView-green.svg?style=true)](https://android-arsenal.com/details/1/4569)
- [Medium](https://medium.com/@kevalpatel2106/user-aware-video-view-4172c9f722e2#.i068pckyh)
- [![awesome-android](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)]([![awesome-android](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://snowdream.github.io/awesome-android/Other.html#Utility))

## What is this library for?
UserAwareVideoView is a customizable VideoView that smartly play and pause the video based on your user is looking at the video or not. This uses Play Services Mobile Vision APIs to detect user's eyes. If the user is not looking at the screen than this will automatically pause the video, so your user does not miss any part of the video.

## How to use this library???
### Gradle dependency:
Add these lines to your `build.gradle` file to start integration. 

```
dependency{
    compile 'com.kevalpatel2106:userawarevideoview:1.0.2'
}
```

- This library automatically adds `android.permission.CAMERA` permission in your applications `AndroidManifest.xml` file.

### Add to XML layout:
You can use `UserAwareVideoView` just like you user the default VideoView in your layout. 
```
 <com.kevalpatel.userawarevieoview.UserAwareVideoView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/video_view"/>
```

### Initialize in your activity:
- **Step-1:** Check for the Camera permission in runtime.
- **Step-2:** Register `UserAwarenessListener` to get the callbacks from the `UserAwareVideoView` whenever error occurs in eyes detection or eye detection starts stops.
- **Step-3:** Handle errors that may occur while eyes detection. 
```
mVideoView = (UserAwareVideoView) findViewById(R.id.video_view);
mVideoView.setUserAwarenessListener(new UserAwarenessListener() {
            @Override
            public void onErrorOccurred(int errorCode) {
                //Handle errors.
                 switch (errorCode) {
                            case Errors.UNDEFINED:
                                //Unknown error occured. 
                                //This will stop eye tracking, but video will keep playing.
                                break;
                            case Errors.FRONT_CAMERA_NOT_AVAILABLE:
                                //This indicates that device doesnot have the front camera
                                //This will stop eye tracking, but video will keep playing.
                                break;
                            case Errors.CAMERA_PERMISSION_NOT_AVAILABLE:
                                //This indicates that camera permission is not available.
                                //Ask for the runtime camera permission.
                                break;
                            case Errors.LOW_LIGHT:
                                //This indicates that there is dark out side. We cannot detect user's face.
                                //This will stop eye tracking, but video will keep playing.
                                break;
                        }
            }

            @Override
            public void onEyeTrackingStarted() {
                //Eye detection started
            }

            @Override
            public void onEyeTrackingStop() {
                //Eye detection is stopped.
            }
        });
//Atatch your media controller, provide video to play and start the video
//......
//......
```

That's it. UserAwareVideoView is ready to use.

## Demo
- You can download the sample apk from [here](/apk/sample.apk).
- The video in sample apk is streamed online. So, make sure you have active internet connection.

## Contribute:
#### Simple 3 step to contribute into this repo:

1. Fork the project. 
2. Make required changes and commit. 
3. Generate pull request. Mention all the required description regarding changes you made.

## Questions
Hit me on twitter [![Twitter](https://img.shields.io/badge/Twitter-@kevalpatel2106-blue.svg?style=flat)](https://twitter.com/kevalpatel2106)

## License
Copyright 2017 Keval Patel

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.


### Support:

If you want the good work to continue please support us on

* [PAYPAL](https://www.paypal.me/ishandutta2007)
* [BITCOIN ADDRESS: 3LZazKXG18Hxa3LLNAeKYZNtLzCxpv1LyD](https://www.coinbase.com/join/5a8e4a045b02c403bc3a9c0c)
