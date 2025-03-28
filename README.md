# realtime-line-detection

A real-time video processing tool for detecting and drawing lane-like lines in video streams.  
Supports video file input or webcam, optional frame rotation, white color filtering, edge detection, line averaging, and output saving.

---

## 📦 Features

- Process video from webcam or file
- Rotate frames by a specified angle
- Filter for white features (e.g., road lanes)
- Apply Canny edge detection
- Region of interest masking
- Detect and average Hough lines
- Draw extended lines for visualization
- Interactive keyboard controls (start, pause, quit)
- Optional real-time FPS display
- Save output to processed video file

---

## 🛠 Requirements

- Python 3.6+
- OpenCV (`cv2`)
- NumPy

Install with:

```bash
pip install opencv-python numpy
```

---

## 🚀 How to Run

```bash
python video_line_detection.py
```

With optional arguments:

```bash
python video_line_detection.py -f input_video.mp4 -o result.avi -r 10
```

### CLI Arguments:

| Argument | Description |
|----------|-------------|
| `-f` / `--file` | (Optional) Input video file. Defaults to webcam if not provided. |
| `-o` / `--out`  | Output video file name (default: `output.avi`) |
| `-r` / `--rotate` | Rotation angle in degrees (default: `10`) |

---

## 🎮 Controls (During Runtime)

| Key | Action              |
|-----|---------------------|
| `s` | Start detection     |
| `p` | Pause/Resume        |
| `q` | Quit and exit       |

---

## 🔍 Pipeline Overview

1. **Optional Rotation**: Rotate frame to correct camera angle.
2. **White Filtering**: Mask white-ish pixels (based on brightness + saturation).
3. **Edge Detection**: Use Canny to highlight contours.
4. **Region of Interest**: Focus on trapezoid area (e.g., road area).
5. **Hough Transform**: Detect lines.
6. **Line Filtering**: Classify left/right based on slope.
7. **Averaging**: Extend and stabilize visual lines.
8. **Rotation Reversal**: If rotated, convert lines back to match original frame.
9. **Draw + Save**: Output annotated video frames.

---

## 🧠 Possible Use Cases

- Road lane detection (basic prototype)
- General purpose line detection
- Frame preprocessing demo
- Real-time visual debugging tool

---

## 🗂 Project Structure

```
.
├── Cam.py    # Main script
├── output.avi                 # Processed output video
├── README.md
```

---

## 💡 Future Ideas

- Add debug overlays for edges and masks
- Use Kalman Filter for smoothing line tracking
- Add logging or stats per frame
- Add GUI (Tkinter or PyQt) for easier control
