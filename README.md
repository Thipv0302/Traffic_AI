
# 🚗 Vehicle Detection, Tracking, and Speed Estimation using YOLOv8

This project uses **YOLOv8** and **OpenCV** to detect vehicles in a video, assign unique IDs to each vehicle using a simple tracking algorithm, and calculate their **speed** as they pass through two predefined lines.

---

## 📌 Features

- ✅ Real-time vehicle detection using **YOLOv8**
- ✅ Simple object tracking to assign consistent IDs
- ✅ Calculates vehicle speed based on time between two lines
- ✅ Logs results to a CSV file
- ✅ Saves annotated output video with bounding boxes, IDs, and speed

---

## 🧠 Model Used

- **YOLOv8s** (You Only Look Once - v8, small version)
- From [Ultralytics](https://github.com/ultralytics/ultralytics)

---

## 📁 Project Structure

```

.
├── main.py           # Visualize detection + tracking only
├── speed.py          # Main file: detection + speed estimation + CSV logging
├── tracker.py        # Custom object tracker (ID assignment)
├── coco.txt          # Class labels for YOLOv8
├── veh2.mp4          # Sample input video (you need to provide)
├── output\_tracking.mp4 # Output video with annotations
├── car\_details.csv   # Output CSV with car ID, speed, direction, timestamp

````

---

## ⚙️ Requirements

- Python 3.8+
- Packages:

```bash
pip install ultralytics opencv-python pandas numpy
````

---

## ▶️ How to Run

### 1. Vehicle Detection + Speed Estimation (Main functionality):

```bash
python speed.py
```

* Outputs annotated video as `output_tracking.mp4`
* Saves speed logs to `car_details.csv`

### 2. Just Visualize Detection + Tracking (No speed):

```bash
python main.py
```

* Useful for testing detection and ID tracking.

---

## 📊 Output Example

**CSV Output (`car_details.csv`):**

| Car ID | Direction | Speed (Km/h) | Timestamp           |
| ------ | --------- | ------------ | ------------------- |
| 1      | Down      | 43           | 2025-06-05 08:15:32 |
| 2      | Up        | 38           | 2025-06-05 08:16:01 |

**Video Output:**
Displays bounding boxes, ID, speed (if calculated), and direction indicators.

---

## ✏️ How Speed is Calculated

1. Two horizontal lines (`L1` and `L2`) are defined in the frame.
2. When a car crosses `L1`, a timestamp is saved.
3. When it crosses `L2`, the elapsed time is used to compute speed:

   ```
   Speed (m/s) = Distance / Time
   Speed (Km/h) = Speed (m/s) * 3.6
   ```

> ⚠️ Default distance between L1 and L2 is `10 meters`. Adjust it in `speed.py` if needed.

---

## 📌 Notes

* The file `veh2.mp4` is expected to be a top-view or side-view traffic video.
* You can replace it with your own traffic video, but adjust resolution and line positions if needed.
* `coco.txt` should contain COCO class labels (car = class\_id 2).

---

## 📜 License

This project is released under the MIT License.

---

## 🙋‍♂️ Author

Created by \[Thipv0302]
If you find this project useful, feel free to ⭐ the repo!
---

Bạn chỉ cần thay thế dòng `"Your Name"` thành tên thật hoặc nickname của bạn. Nếu bạn dùng `veh2.mp4` không muốn đưa public, hãy thêm `.gitignore` để loại bỏ nó. Nếu cần, mình có thể giúp bạn tạo luôn file `.gitignore`.
```
