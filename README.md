# 🖼 Mini Project-23: Resize 100 Images to 50% Using OpenCV

This project uses Python and OpenCV to resize a batch of 100 images to *50% of their original size*. It’s a beginner-friendly image processing task useful for dataset optimization, web use, or mobile app compatibility.

---

## 🚀 Features

- 🔹 Resize all images in bulk
- 🔹 Supports .jpg, .png, .jpeg, .bmp
- 🔹 Saves all resized images in a zip file for easy download
- 🔹 Runs perfectly on Google Colab or locally

---

## 📁 How to Use

### 🧩 Step-by-Step on Google Colab

1. Upload a ZIP file containing 100 images.
2. Extract the ZIP using Python.
3. Use OpenCV to resize each image to 50%.
4. Save the output to a new folder.
5. Zip the folder and download the result.

```python
import cv2, os, zipfile
from google.colab import files

# Upload ZIP
uploaded = files.upload()

# Extract
with zipfile.ZipFile("images.zip", "r") as zip_ref:
    zip_ref.extractall("original_images")

# Resize and Save
os.makedirs("resized_images", exist_ok=True)
for img in os.listdir("original_images"):
    if img.lower().endswith((".jpg", ".png", ".jpeg")):
        path = f"original_images/{img}"
        image = cv2.imread(path)
        resized = cv2.resize(image, (0, 0), fx=0.5, fy=0.5)
        cv2.imwrite(f"resized_images/{img}", resized)

# Zip and Download
shutil.make_archive("resized_images", "zip", "resized_images")
files.download("resized_images.zip")
