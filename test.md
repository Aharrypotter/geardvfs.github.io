<style>

.markdown-bodyh1 {

    border-bottom: none

}

.markdown-bodyh2 {

    border-bottom: 2px solid grey;

}

.markdown-body {

    border-bottom: 2px solid black;

    padding-left: 65px!important;

    padding-right: 65px!important;

    box-shadow: 5px2px2pxgrey;

    background: white;

}

body {

    background: #c1bebe;

}

</style>

<div>

    `<br><br>``<br>`

    [h1style=&#34;text-align:center;&#34;](h1style=%22text-align:center;%22)`<b>`GearDVFS: A Workload-Aware DVFS Robust to Concurrent

Tasks for Mobile Devices`</b></h1>`

</div>


# nnPerf + TFLite Android Image Classifier App

## To Install / Run profile

### Run with apk

1. **Use adb to connect to smartphones or mobile platforms (Android basic system).**
2. **Install the nnPerf_v1.1.apk.**
   ```
   adb install -t '.\nnPerfAPKinstaller\nnPerf_v1.1.apk'
   ```

### Build project

1. **Install Android Studio 3.6.3 (Runtime version: 1.8.0_212-release-1586-b04 amd64)**
2. **Import Project**
   **File -> Open -> Current file directory **
3. **Android Studio Setting**

```
Android Gradle Plugin Version: 3.1.3

Gradle Version:                4.4

NDK Version:                   21.0.6113669

JDK Verison:                   1.8.0_211

Complile Sdk Version:          27

Build Tools Version:           27.0.3

```

4. **Run to profile 【* Update unified output path】**

```
Update Output path: /storage/emulated/0/
```

5. **Note: In the case of GPU reasoning, do not directly switch models.**
6. **Model support list (Support for adding other .tflite models)**

```
mobilenetV3-Large-Float

mobilenetV3-Small-Float

mobilenetV2-Float

mobilenetV1-Float

Squeezenet-Float

EfficientNet-b0-Float

MNasNet-1.0

Densenet-Float

mobilenetV1-Quant
```

7. **Recommended papers and books are in the 'paperList' directory**
