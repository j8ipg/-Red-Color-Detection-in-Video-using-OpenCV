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


## 📦 Installation

Make sure Python is installed, then install the dependencies:

```bash
pip install opencv-python numpy imageio
'''
ططط
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

## code i used:
'''import cv2
import numpy as np
import imageio

# تحميل الفيديو
cap = cv2.VideoCapture('7565889-hd_1080_1920_25fps.mp4')

# قائمة لتخزين الفريمات
frames_for_gif = []

while True:
    ret, frame = cap.read()
    if not ret:
        break

    frame = cv2.resize(frame, (640, 480))
    hsv = cv2.cvtColor(frame, cv2.COLOR_BGR2HSV)

    # نطاق الأحمر
    lower_red = np.array([0, 150, 100])
    upper_red = np.array([10, 255, 255])
    mask1 = cv2.inRange(hsv, lower_red, upper_red)

    lower_red2 = np.array([170, 150, 100])
    upper_red2 = np.array([180, 255, 255])
    mask2 = cv2.inRange(hsv, lower_red2, upper_red2)

    mask = mask1 + mask2

    kernel = np.ones((5, 5), np.uint8)
    mask = cv2.morphologyEx(mask, cv2.MORPH_OPEN, kernel)
    mask = cv2.morphologyEx(mask, cv2.MORPH_DILATE, kernel)

    contours, _ = cv2.findContours(mask, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
    for cnt in contours:
        area = cv2.contourArea(cnt)
        if 2000 < area < 30000:
            x, y, w, h = cv2.boundingRect(cnt)
            cv2.rectangle(frame, (x, y), (x + w, y + h), (0, 255, 0), 2)
            cv2.putText(frame, "Red Object", (x, y - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.7, (0, 255, 0), 2)

    # تحويل اللون من BGR إلى RGB وحفظ الفريم
    rgb_frame = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
    frames_for_gif.append(rgb_frame)

    cv2.imshow("Object Tracking", frame)
    if cv2.waitKey(30) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
'''
# حفظ النتيجة كـ gif
imageio.mimsave("output.gif", frames_for_gif, fps=10)
print("✅ Saved as output.gif")

## 📸 Output Preview
The script generates a file called output.gif showing the processed video with red objects labeled like this:
vid:
https:
 //github.com/user-attachments/assets/c3729ae6-1d62-4482-82a3-c801b2f8fde8

pic:

<img width="1366" height="836" alt="red colar" src="https://github.com/user-attachments/assets/957d021d-74b4-415e-8ce5-3a35ccfeb7cc" />


