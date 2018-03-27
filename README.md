# Backgroundvideo

##### A simple Cordova/Phonegap plugin to capture MP4 video and then display it onscreen via a transparent overlay without affecting app functionality.
#### On Android can record videos with minimized app or even when screen is off. It can be used for spy cameras or for video surveillance.
#### On iOS you need to provide screen insomnia. Video will be correctly finished on app minimized, screen off or incoming call.

## Supported Platforms
- Android
- iOS
- Windows

# How to use
### Install
```
cordova plugin add https://github.com/pavelety/backgroundvideo.git
```
### Usage
```
cordova.plugins.backgroundvideo.start(filename, cameraOptions, successfn, errorfn);
```

# Getting started
### start recording
```js
var fileName = new Date().getTime() + '';
var videoOptions = {camera: 'back', shouldRecordAudio: true, videoBitrate: 40960, audioBitrate: 10240};
var successFn = function(filePath) {
    console.log('video started:' + filePath);
};
var errorFn = function(error) {
    console.log('video recording error:' + error);
};
cordova.plugins.backgroundvideo.start(successFn, errorFn, fileName, videoOptions);
```
####Or minimalistic
```js
cordova.plugins.backgroundvideo.start(function(filePath) {
    console.log('video started:' + filePath);
});
```

### VideoOptions : <code>Object</code>

| Name              | Type                  | Default               | Description                           |
| ----------------- | --------------------- | --------------------- | ------------------------------------- |
| camera            | <code>string</code>   | <code>back</code>     | 'back' or 'front'                     |
| shouldRecordAudio | <code>boolean</code>  | <code>true</code>     | Record video with audio               |
| videoBitrate      | <code>int</code>      | <code>40960</code>    | Video bitrate in bit per second (bps) |
| audioBitrate      | <code>int</code>      | <code>10240</code>    | Audio bitrate in bit per second (bps) |

---

###### stop recording
```js
var successFn = function(filePath) {
    console.log('video saved:' + filePath);
};
var errorFn = function(error) {
    console.log('video recording error:' + error);
};
cordova.plugins.backgroundvideo.stop(successFn, errorFn);
```
### Other bits
**Camera**
'front' or 'back' to specify camera direction.

**File**
- Outputs as mp4. You do not need to specify file extension.
- Video files are saved to approot on sdcard or internal (cordova.plugins.backgroundvideo.stop() will return the file path).

### Support
Please use the github issue tracker and we will come back to you as soon as we can.

### Contribution
There's lots of Android phones all with their own quirks so we'd love it if you could contribute and help us support all of the devices out there.
