# I7 Video Manager

## Description
A small-scale, fully functional desktop video track manager that allows us to manage and modify tracks when a video is selected.  
This tool is primarily designed for small-scale editors who may be uncertain about certain tracks.  
The entire tool is built with **Python + PyQt5 + FFmpeg**.

## Useful Scenarios
1. If a video is available in 4K quality in English and in 144p in Telugu, we can extract the audio track from the Telugu video and insert it into the English video.  
   We also have the option to replace the video in the English track.  
2. If a video contains multiple tracks, we can delete any unnecessary ones.  
3. We can clear the metadata associated with the video.  

<img width="1202" height="813" alt="image" src="https://github.com/user-attachments/assets/e3f6dfad-a079-4a86-b2ec-3b6489523805" />

---

## Technologies Used
- **Language**: Python 3.11+  
- **GUI Framework**: PyQt5  
- **Backend Tool**: FFmpeg / FFprobe  
- **Packaging**: PyInstaller (for `.exe` builds)

---

## Features
- **Track Inspection**
  - View all video, audio, and subtitle tracks
  - See codec, duration, language, and size (in MB)

- **Track Management**
  - Delete tracks (staged with red highlight before saving)
  - Insert new tracks (audio or subtitle files)
  - Replace the main video track
  - Extract tracks with a single click (auto-saves to file)

- **Metadata Handling**
  - View complete file metadata (size, duration, format, streams)
  - Clear metadata option

- **User-Friendly Interface**
  - Undo / Redo support
  - Operations log (shows performed actions with timestamps)
  - Progress bar for large video file loading & size extraction
  - Splash screen with animation

---

## Installation
1. Install Python 3.11+  
2. Install dependencies:
   ```bash
   pip install pyqt5
   ```
3. Extract the zip folder. Your folder should look like this:
    ```
    I7VideoManager/
    |- ffmpeg.exe
    |- ffprobe.exe
    |- I7VideoManager.exe
    ```
4. If you don’t have standalone ffmpeg.exe and ffprobe.exe:
    - Download them from the official build: [FFmpeg Builds](https://www.gyan.dev/ffmpeg/builds/)
    - Get the **release full build (zip)**.
    - Inside `bin/` you’ll find `ffmpeg.exe` and `ffprobe.exe`.
    - Copy those two files into the folder above.
5. Run your `I7VideoManager.exe`.

---

## Turning `.py` into Standalone Application

### 1: Install PyInstaller
```bash
pip install pyinstaller
```

### 2: Build the exe
Navigate to your project folder where `I7VideoManager.py` is saved:


Run PyInstaller:
```bash
pyinstaller --onefile --windowed --icon=icon.ico I7VideoManager.py
```

Options explained:
- `--onefile` → bundles everything into a single `.exe`.
- `--windowed` → hides the console window (good for GUI apps).
- `--icon=icon.ico` → optional, sets a custom app icon.

### 3: Find the exe
After building, you’ll see two folders created:
```
build/
dist/
```

Your executable will be in:
```
dist/I7VideoManager.exe
```

### Note:
- Since the app relies on **ffmpeg.exe** and **ffprobe.exe**, make sure:
  - Either add them to PATH,  
  - Or bundle them inside the same folder as your `.exe`.  
- The first build may take time since PyInstaller analyzes all dependencies.  
- The exe may be large (~50–70MB), which is normal because it bundles Python + Qt.

---

## License
MIT License — free to use, modify, and share.
