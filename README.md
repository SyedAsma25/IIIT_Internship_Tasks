# 🎬 FFmpeg Internship Tasks 

This repository contains the implementation of video and audio processing tasks using FFmpeg as part of the internship assignment.

---

## 📌 Task 1: Extract Images from Video

### 🎥 Video Source:
https://youtu.be/T1cgoNp_xJ0

### 🔧 Process:
- Downloaded the YouTube video using yt-dlp
- Extracted frames using FFmpeg at 1 frame per second

### 💻 Command Used:
```bash
ffmpeg -i video.mp4 -vf fps=1 images/output_%03d.jpg
```

### 📊 Output:
- Extracted approximately 150 images from the video
- Images stored in `images/` folder

---

## 📌 Task 2: Generate Video from Frames

### 🎥 Video Source:
https://youtu.be/qByEvIimSa4

### 🔧 Process:
- Extracted a 1-minute segment from the video
- Generated frames at 30 FPS (~1800 images)
- Reconstructed video from image sequence

### 💻 Commands Used:
```bash
ffmpeg -ss 0 -t 60 -i video2.mp4.webm -vf fps=30 images_30fps/frame_%04d.jpg
ffmpeg -framerate 30 -i images_30fps/frame_%04d.jpg -c:v libx264 -pix_fmt yuv420p output2.mp4
```

### 📊 Output:
- `output2.mp4` (1-minute video reconstructed from frames)

---

## 📌 Task 3: Add Audio to Video

### 🎵 Audio Source:
https://pixabay.com/music/search/1%20minute/

*(Example: Kaazoom - Under the Forest or similar royalty-free track)*

### 🔧 Process:
- Downloaded royalty-free audio from Pixabay
- Trimmed audio to 1 minute
- Merged audio with video created in Task 2

### 💻 Commands Used:
```bash
ffmpeg -i "music.mp3.mp3" -t 60 -acodec copy audio_1min.mp3
ffmpeg -i output2.mp4 -i audio_1min.mp3 -c:v copy -c:a aac -shortest final_video.mp4
```

### 📊 Output:
- `final_video.mp4` (video with background audio)

---

## 🛠️ Tools Used

- FFmpeg
- yt-dlp
- Windows Command Prompt

---

## 🎯 Conclusion

This project demonstrates:
- Video frame extraction
- Frame-to-video reconstruction
- Audio trimming and merging

All tasks were successfully completed using FFmpeg.

---

## 📂 Repository Contents

- `Task-01/` → Extracted frames and Video input  [Task-01]
- `video2.mp4.mp4` → Input Video of task-2  [Task-02]
- `output2.mp4` → Reconstructed video  [Task-02]
- `music.mp3.mp3` → Input audio  [Task-03]
- `final_video (1).mp4` → Final output video  [Task-03]
- `Week-02` → Terminal screenshot, input and output images  [Week-02, Tasks-1,2,3]

---

## 📎 References

- YouTube (Video Sources)
- Pixabay (Audio Source)
- FFmpeg Documentation

---

## 📌 Week 2 - Object Detection using YOLO

### 🔧 Task Overview:
- Created Python virtual environment using venv
- Installed Ultralytics package
- Ran object detection using pretrained YOLO model

### 💻 Commands Used:
```bash
python -m venv venv
venv\Scripts\activate
pip install -U ultralytics
yolo predict model=yolov8n.pt source='https://ultralytics.com/images/bus.jpg
```


### 📊 Output:
- Detected objects: persons, bus, stop sign
- Output saved in:
  runs/detect/predict/

### 🖼️ Sample Output:
![Detection](runs/detect/predict/bus.jpg)
