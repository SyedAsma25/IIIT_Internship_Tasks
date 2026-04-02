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

- `images/` → Extracted frames 
- `images_30fps/` → Frames at 30 FPS 
- `output2.mp4` → Reconstructed video
- `audio_1min.mp3` → Trimmed audio
- `final_video.mp4` → Final output video

---

## 📎 References

- YouTube (Video Sources)
- Pixabay (Audio Source)
- FFmpeg Documentation
