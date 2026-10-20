# name-plate-detection

A small OpenCV script that tries to locate a vehicle number plate in an image and read its text with Tesseract OCR.

## What the script does

`name_plate_detection.py` is a single-file, step-by-step pipeline. Each stage opens an OpenCV window; press a key to continue.

1. Opens a file dialog (Tkinter) to pick an image and resizes it to 500 px wide.
2. Converts to grayscale and applies a bilateral filter.
3. Runs Canny edge detection.
4. Finds contours, keeps the 30 largest, and picks the first one that approximates to a four-sided shape (the plate candidate).
5. Masks the image to that region, thresholds it, and runs `pytesseract` on the result.
6. Prints the recognised text.

## Requirements

- Python 3
- `numpy`, `opencv-python`, `imutils`, `pytesseract`
- [Tesseract OCR](https://github.com/tesseract-ocr/tesseract) installed. The script hard-codes the Windows path `C:\Program Files (x86)\Tesseract-OCR\tesseract.exe`; edit that line if yours differs.

## Run

```bash
pip install numpy opencv-python imutils pytesseract
python name_plate_detection.py
```

## Status

Learning project. The script has some inconsistent variable names (for example `gray`, `img1`, `cnts` and `c` are used but never defined), so it needs those fixed before it will run end to end. There is no error handling for images where no four-sided contour is found.