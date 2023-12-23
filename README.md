# Bird-Eye-View Transformation using Homography Matrix

## Overview
This project aims to transform a front view of a checkerboard to a top view (bird-eye view) using a homography matrix. The transformation corrects for distortion in the image, ensuring equal dimensions for the squares' width and height in the top view.

This project focuses on transforming a front view of a checkerboard into a top view (bird-eye view) through a homography matrix. The transformation aims to correct distortions in the image caused by the reduction in the width of the checkerboard along the camera axis. The goal is to obtain an undistorted top view where the lengths of squares' width and height are equal.
## Project Details
The transformation algorithm relies on a checkerboard placed flat on the floor, and an image of it serves as the front view for transformation. The key functions involved in this transformation process:
### Functionality Overview
- **findChessboardCorners()**: This function identifies the coordinates of all corners in the checkerboard. However, only the outer four corners are selected to determine the shape of the checkerboard.
### Transformation Logic
The old positions of the selected corners, before transformation, undergo specific calculations to determine their new positions for the top-down view:

1. **Preservation of X-Values**: The X (width) value of the top corners remains unchanged to maintain the line of sight.

2. **Calculating Differences**:
   - Difference 1: Width difference between the top-left and bottom-left corners.
   - Difference 2: Width difference between the top-right and bottom-right corners.

3. **Adjusting Width**:
   - Add the absolute value of Difference 1 to the width of the bottom-left corner.
   - Subtract the absolute value of Difference 2 from the width of the bottom-right corner.

4. **Ensuring Equal Square Sides**:
   - Compensate for width changes by adjusting the height of both top corners.
   - Add Difference 1 and Difference 2 to the height of both top corners.

### Transformation Process
1. Old and new points are determined using the transformation logic.
2. A transformation matrix is derived using the `findHomography()` function based on the given old and new corner coordinates.
3. The `warpPerspective()` function applies the transformation matrix to generate the top-view image from the front view.


## Setup and Usage
1. **Installation**:
   - Ensure Python is installed. If not, download and install Python 3.x from [here](https://www.python.org/).
   - Install required packages:
     ```
     pip install opencv-python numpy
     ```

2. **Execution**:
   - Clone this repository:
     ```
     git clone https://github.com/Sohaib-Snouber/Bird-Eye-View.git
     ```
   - Navigate to the project directory:
     ```
     cd Bird-Eye-View
     ```
   - Place your front view image of the checkerboard in the project directory and rename it as `front_view.png`.
   - Run the Python script:
     ```
     python top_view.py
     ```
   - Follow the on-screen instructions to mark the corners of the checkerboard.

3. **Understanding the Code**:
   - The script uses OpenCV and NumPy to perform the transformation.
   - It identifies the corners of the checkerboard, sorts and extracts the outer corners.
   - Calculations are made to determine the new positions of the corners for the top-down view.
   - Homography matrix is computed using `cv2.findHomography` based on the old and new corner coordinates.
   - The `cv2.warpPerspective` function applies the transformation to generate the top-view image.

## File Structure
- **bird_eye_view.py**: Main Python script for the transformation.
- **front_view.png**: Input image file (front view of the checkerboard).
- **README.md**: Documentation file providing instructions and an overview of the project.

## References
- [OpenCV Documentation](https://docs.opencv.org/)
- [NumPy Documentation](https://numpy.org/doc/)


## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


## Acknowledgments

- **Luca**: Your advice and guidance were instrumental in achieving excellent results for this project.
- **Niklas**: Your assistance with design and optimization for perception-related tasks was incredibly helpful throughout this project.
- **Mika**: Your explained key concepts were crucial to achieving the project results.
- **Ayoub**: Your shared insights were valuable in reaching the outcomes presented in this project.
