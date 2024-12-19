# 移动和网页实时直播数字人！

# 数字人方案对比

以下表格展示了不同数字人方案的性能、使用方式、脸部分辨率及适用设备等信息，方便用户根据需求选择合适的方案。

| 方案名称                     | 单帧算力（Mflops） | 使用方式   | 脸部分辨率 | 适用设备                           |
|------------------------------|-------------------|------------|------------|------------------------------------|
| Ultralight-Digital-Human（移动） | 1100              | 单人训练   | 160        | 中高端手机APP                      |
| DH_live_mini                  | 39                | 无须训练   | 128        | 所有设备，网页&APP&小程序          |
| DH_live                       | 55,046            | 无须训练   | 256        | 30系以上显卡                       |
| duix.ai                      | 1,200             | 单人训练   | 168        | 中高端手机APP                      |

### 新闻

## 训练
渲染模型训练的详细信息可以在[这里](https://github.com/kleinlee/DH_live/tree/master/train)找到。
音频模型训练的详细信息可以在[这里](https://github.com/kleinlee/DH_live/tree/master/train_audio)找到。
### 视频示例

[点击这里查看视频示例](https://github.com/user-attachments/assets/7e0b5bc2-067b-4048-9f88-961afed12478)

## 概览
这个项目是一个由少样本学习驱动的实时直播数字人。它被设计为在所有30和40系列显卡上流畅运行，确保无缝和互动的直播体验。

### 核心特性
- **实时性能**：数字人可以与25+ fps的实时互动，适用于常见的NVIDIA 30和40系列GPU
- **少样本学习**：系统能够从几个样本中学习，生成真实的响应。

# 使用方法

### 创建环境并解压模型文件
首先，导航到`checkpoint`目录并解压模型文件：
```bash
conda create -n dh_live python=3.12
conda activate dh_live
pip install torch --index-url https://download.pytorch.org/whl/cu124 
pip install -r requirements.txt
cd checkpoint
```

### 准备您的视频
接下来，使用data_preparation脚本准备您的视频。将YOUR_VIDEO_PATH替换为您的视频路径：
```bash
python data_preparation.py YOUR_VIDEO_PATH
```
结果（video_info）将存储在./video_data目录中。
### 带音频文件运行
使用音频文件运行演示脚本。确保音频文件是16kHz采样率和16位单通道的.wav格式。将video_data/test替换为您的视频_info文件路径，video_data/audio0.wav替换为您的音频文件路径，1.mp4替换为您希望的输出视频路径：
```bash
python demo.py video_data/test video_data/audio0.wav 1.mp4
```
### 使用麦克风实时运行
对于使用麦克风的实时操作，只需运行以下命令：
命令传参为DH_live\video_data下模型文件夹名，
如需使用其他模型，可以修改此脚本的参数
```bash
python demo_avatar.py test
```

## 致谢
我们要感谢[Wav2Lip](https://github.com/Rudrabha/Wav2Lip)、[DINet](https://github.com/MRzzm/DINet)、[LiveSpeechPortrait](https://github.com/YuanxunLu/LiveSpeechPortraits) 仓库的贡献者，感谢他们的开放研究和贡献。

## 许可证
DH_live在MIT许可证下授权。

DH_live_mini在Apache 2.0许可证下授权。
