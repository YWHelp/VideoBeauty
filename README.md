# VideoBeauty
GPUImage原生美颜
步骤一：使用Cocoapods导入GPUImage
步骤二：创建视频源GPUImageVideoCamera
步骤三：创建最终目的源：GPUImageView
步骤四：创建滤镜组(GPUImageFilterGroup)，需要组合亮度(GPUImageBrightnessFilter)和双边滤波(GPUImageBilateralFilter)这两个滤镜达到美颜效果.
步骤五：设置滤镜组链
步骤六：设置GPUImage处理链，从数据源 => 滤镜 => 最终界面效果
步骤七：开始采集视频

注意点：

SessionPreset最好使用AVCaptureSessionPresetHigh，会自动识别，如果用太高分辨率，当前设备不支持会直接报错
GPUImageVideoCamera必须要强引用，否则会被销毁，不能持续采集视频.
必须调用startCameraCapture，底层才会把采集到的视频源，渲染到GPUImageView中，就能显示了。
GPUImageBilateralFilter的distanceNormalizationFactor值越小，磨皮效果越好,distanceNormalizationFactor取值范围: 大于1。
