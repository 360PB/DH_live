# Mobile and Web Real-time Live Streaming Digital Human! 

# 数字人方案对比

以下表格展示了不同数字人方案的性能、使用方式、脸部分辨率及适用设备等信息，方便用户根据需求选择合适的方案。

| 方案名称                     | 单帧算力（Mflops） | 使用方式   | 脸部分辨率 | 适用设备                           |
|------------------------------|-------------------|------------|------------|------------------------------------|
| Ultralight-Digital-Human（mobile） | 1100              | 单人训练   | 160        | 中高端手机APP                      |
| DH_live_mini                  | 39                | 无须训练   | 128        | 所有设备，网页&APP&小程序          |
| DH_live                       | 55,046            | 无须训练   | 256        | 30系以上显卡                       |
| duix.ai                      | 1,200             | 单人训练   | 168        | 中高端手机APP                      |

### News

## Training
Details on the render model training can be found [here](https://github.com/kleinlee/DH_live/tree/master/train).
Audio Model training Details can be found [here](https://github.com/kleinlee/DH_live/tree/master/train_audio).
### Video Example


https://github.com/user-attachments/assets/7e0b5bc2-067b-4048-9f88-961afed12478


## Overview
This project is a real-time live streaming digital human powered by few-shot learning. It is designed to run smoothly on all 30 and 40 series graphics cards, ensuring a seamless and interactive live streaming experience.

### Key Features
- **Real-time Performance**: The digital human can interact in real-time with 25+ fps for common NVIDIA 30 and 40 series GPUs
- **Few-shot Learning**: The system is capable of learning from a few examples to generate realistic responses.
## Usage

### Create Environment and Unzip the Model File 
First, navigate to the `checkpoint` directory and unzip the model file:
```bash
conda create -n dh_live python=3.12
conda activate dh_live
pip install torch --index-url https://download.pytorch.org/whl/cu124
pip install -r requirements.txt
cd checkpoint
```

### Prepare Your Video
Next, prepare your video using the data_preparation script. Replace YOUR_VIDEO_PATH with the path to your video:
```bash
python data_preparation.py YOUR_VIDEO_PATH
```
The result (video_info) will be stored in the ./video_data directory.
### Run with Audio File
Run the demo script with an audio file. Make sure the audio file is in .wav format with a sample rate of 16kHz and 16-bit single channel. Replace video_data/test with the path to your video_info file, video_data/audio0.wav with the path to your audio file, and 1.mp4 with the desired output video path:
```bash
python demo.py video_data/test video_data/audio0.wav 1.mp4
```
### Real-Time Run with Microphone
For real-time operation using a microphone, simply run the following command:
```bash
python demo_avatar.py
```

## Acknowledgements 
We would like to thank the contributors of [Wav2Lip](https://github.com/Rudrabha/Wav2Lip), [DINet](https://github.com/MRzzm/DINet), [LiveSpeechPortrait](https://github.com/YuanxunLu/LiveSpeechPortraits) repositories, for their open research and contributions.

## License
DH_live is licensed under the MIT License.

DH_live_mini is licensed under the Apache 2.0.

