# 🔴 Red Color Detection in Video using OpenCV

This project uses **OpenCV** and **NumPy** to detect red-colored objects in a video, highlight them with bounding boxes, and save the result as an animated GIF. It's a simple yet effective demonstration of color recognition using the HSV color space.

---

## 🎯 Project Goal

To detect and highlight red objects in a video file by applying color masking and contour detection using OpenCV.

---

## 🧰 Technologies Used

- Python
- OpenCV
- NumPy
- imageio (to save GIF)

---

## 
---

## 📦 Installation

Make sure Python is installed, then install the dependencies:

```bash
pip install opencv-python numpy imageio

## ▶️ How to Run
1.Clone or download this repository.

2.Download the video used from Pexels or replace it with your own.

3.Place the video file in the same folder as the script.

4.Run the Python script:
تحرير
python red_color_detection.py

5.A window will open showing the processed video with detected red objects highlighted.

6.Press q to exit early if needed.

7.The result will be saved as output.gif in the same folder.


## 🔍 How It Works
.The script reads video frames one by one.

.Each frame is resized and converted to HSV color space.

.A red color range is applied using cv2.inRange for two HSV zones (lower and upper red).

.Morphological operations are used to clean the mask.

.Contours are detected and drawn around red areas with bounding rectangles and labels.

.Each processed frame is stored and then saved as a GIF using imageio.

## 📸 Output Preview
The script generates a file called output.gif showing the processed video with red objects labeled like this:
vid:
https://github.com/user-attachments/assets/c3729ae6-1d62-4482-82a3-c801b2f8fde8

pic:<img width="1366" height="836" alt="red colar" src="https://github.com/user-attachments/assets/957d021d-74b4-415e-8ce5-3a35ccfeb7cc" />


