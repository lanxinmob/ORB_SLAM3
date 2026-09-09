prob_1:
- hjadmin@ubuntu:~$ ffplay -f v4l2 -input_format mjpeg -video_size 1920x1080 -framerate 60 -i /dev/v4l/by-id/usb-MACROSILICON_Vin_1_20250811-video-index0
[video4linux2,v4l2 @ 0x742970000c80] Dequeued v4l2 buffer contains corrupted data (0 bytes).
    Last message repeated 31 times
[mjpeg @ 0x742970001980] EOI missing, emulating
Input #0, video4linux2,v4l2, from '/dev/v4l/by-id/usb-MACROSILICON_Vin_1_20250811-video-index0':
  Duration: N/A, start: 0.000000, bitrate: N/A
  Stream #0:0: Video: mjpeg (Baseline), yuvj422p(pc, bt470bg/unknown/unknown), 1920x1080, 60 fps, 60 tbr, 1000k tbn
[swscaler @ 0x742960032680] deprecated pixel format used, make sure you did set range correctly
    Last message repeated 3 times
[mjpeg @ 0x742970002640] overread 8   0KB vq=    0KB sq=    0B f=0/0   
[mjpeg @ 0x742970002640] EOI missing, emulating
1313380.02 M-V:  0.000 fd=   0 aq=    0KB vq=    0KB sq=    0B f=0/0   

solution:
- 一通排查，最后开始怀疑采集卡自带的UVC传输线，换了一根线后虽然依然有以上warning，但已经不妨碍正常的图像采集了。
- 这些 warning 是另外两个问题，一个需要打一个补丁，另一个就是设置一下pixel format.

