# Real-Time Object Distance Estimator Using OpenCV

This project is a **real-time computer vision system** built with OpenCV to:
- Detect yellow-colored objects in a video stream
- Label them with unique IDs
- Estimate and display the distance between the objects in centimeters
- Provide a visual overlay including bounding boxes, centers, and measured distances

It uses **HSV color filtering**, **contour detection**, and **basic geometric calculations** to determine spatial relationships between detected objects.

---

##  Features :-

-  Real-time video capture with OpenCV  
-  Detection of yellow objects using HSV masking  
-  Calculates center of each object and assigns labels (A, B, C...)  
-  Computes Euclidean distance between detected object centers  
-  Converts pixel distance to real-world centimeters using a fixed threshold  


---

## Technologies Used :-

- Python 3.x
- OpenCV (`cv2`)
- NumPy (`numpy`)
- Basic Math operations (`math`)

---

## Installation :-

### 1. Clone the Repository :-
```bash
git clone https://github.com/your-username/real-time-object-distance-estimator.git
cd real-time-object-distance-estimator
```

### 2. Install Dependencies :-
Ensure you have Python 3 installed. Then install the required libraries:
```bash
pip install opencv-python numpy
```

---

## Camera Setup

> This project uses camera index `10` in `cv2.VideoCapture(10)`.  
>  **Important:** Make sure your desired camera is mapped to index 10, or **change this value** accordingly.

To find your working camera index :-
```python
cv2.VideoCapture(0)  # Try different indexes if 0 doesn't work
```

---

## Usage

Simply run the script :-
```bash
python object_distance_estimator.py
```

### Controls
- Press **`q`** to quit the program safely.

---

## 📌 How It Works

### 1. Color Detection  
The system uses the HSV color space to isolate yellow objects :-
```python
lower_yellow = np.array([20, 100, 100])
upper_yellow = np.array([30, 255, 255])
```

### 2. Object Detection  
Contours are detected from the mask and filtered based on area (`> 500px`) to avoid noise.

### 3. Labeling  
Each detected object is labeled using alphabet characters (A, B, C...).

### 4. Distance Measurement  
- Centers of detected bounding boxes are calculated.
- Distance between consecutive objects is calculated using the Euclidean formula:
  \\( d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2} \\
- This pixel distance is then multiplied by a **distance calibration factor** (`distance_threshold = 0.06912`) to convert to centimeters.

### 5. Display  
- Bounding boxes (green)
- Center points (red circles)
- Blue lines = measured distance between objects
- Red text = real-world distance in centimeters

---

## Output Sample

Here's what you see in the **final output window**:

- Green rectangles = detected objects
- Red dot = center of object
- Blue lines = measured distance between objects
- Red text = real-world distance in centimeters

---

## Calibration Note

> `distance_threshold = 0.06912` is a hardcoded value that maps pixel distance to centimeters.  
To improve accuracy:
- Use a known reference object size in frame
- Calibrate using real-world measurements

---

## Cleanup

On pressing `q`, the script:
- Breaks out of the loop
- Releases the camera feed
- Destroys all OpenCV windows

```python
cv2.destroyAllWindows()
```

---
## Author

**SAMYAK VAIDYA**  
Artificial Intelligence & Data Science Enthusiast  
Connect on [LinkedIn](https://www.linkedin.com/in/samyak-vaidya-4bb9b4282)
