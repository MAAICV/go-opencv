Go OpenCV binding
==================

Fork from https://github.com/lazywei/go-opencv

## Support for gomobile android (arm and x86)

### Install

```
go get github.com/poi5305/go-opencv
```
### Build

- If using gomobild plugin as module in android studio
```
buildscript {
    repositories {
        maven {
            url "https://plugins.gradle.org/m2/"
        }
    }
    dependencies {
        classpath "gradle.plugin.org.golang.mobile.bind:gobindPlugin:0.2.7"
    }
}
apply plugin: "org.golang.mobile.bind"
gobind {
    pkg = "github.com/your_name/your_repo"
    GOPATH = "/your/go/path"
    GOARCH = "arm 386" // important
}
```

- Or using gomobile bind command (generate .aar)
```
gomobile bind -target android/arm,android/386
```

### Runtime dependency

- Don't forget copy opencv/opencv-libs/libs/* to /AndroidStudioProject/app/src/main/jniLibs/

If not, you may get error message that go library can not find the opencv_java.so 

```
opencv/opencv-libs/libs/armeabi/libopencv_java.so
opencv/opencv-libs/libs/armeabi-v7a/libopencv_java.so
opencv/opencv-libs/libs/mips/libopencv_java.so
opencv/opencv-libs/libs/x86/libopencv_java.so
```

- If still not found the opencv library, try this
```
System.loadLibrary("opencv_java");
```
