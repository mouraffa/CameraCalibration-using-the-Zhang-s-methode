# CameraCalibration-using-the-Zhang-s-methode

# Camera Calibration

This program implements a camera calibration algorithm based on Zhang's method. It allows you to calibrate your camera, estimate its intrinsic and extrinsic parameters, and correct for lens distortion effects. The calibration parameters obtained can be used for various computer vision tasks, such as 3D reconstruction, camera pose estimation, and image rectification.

## Algorithm Overview

The camera calibration algorithm used in the code is based on the classical Zhang's method, also known as the Zhang's camera calibration algorithm. It is widely used for calibrating cameras and estimating their intrinsic and extrinsic parameters.

### The algorithm follows these main steps:

1. Checkerboard Initialization:
   - Define the dimensions of the checkerboard pattern (number of internal corners).
   - Create a grid of 3D object points corresponding to the corners of the checkerboard in a real-world coordinate system.

2. Image Acquisition:
   - Collect a set of images of the checkerboard pattern from different viewpoints.

3. Corner Detection:
   - Convert each image to grayscale.
   - Apply a corner detection algorithm (e.g., Harris corner detector) to find the corners of the checkerboard pattern in the grayscale image.
   - The detected corners are represented as 2D image points.

4. Corner Refinement:
   - Refine the detected corner coordinates using the `cv2.cornerSubPix` function.
   - This refinement step improves the accuracy of the corner coordinates.

5. Calibration Parameter Estimation:
   - Store the refined 2D image points and the corresponding 3D object points.
   - Use the collected 2D-3D point correspondences to estimate the camera calibration parameters.
   - This estimation is performed using the `cv2.calibrateCamera` function, which employs a nonlinear optimization technique.

6. Distortion Correction:
   - The calibration parameters obtained from the previous step include the camera matrix and distortion coefficients.
   - The camera matrix represents the intrinsic parameters of the camera, including focal length and principal point.
   - The distortion coefficients capture the lens distortion effects.
   - These parameters can be used to correct the distortion in the input images using the `cv2.undistort` function.

7. Results:
   - The calibration parameters, including the camera matrix, distortion coefficients, rotation vectors, and translation vectors, are obtained.
   - These parameters can be used for various computer vision tasks, such as 3D reconstruction, camera pose estimation, and image rectification.
   - The mathematical aspects of the algorithm involve solving a system of equations to estimate the camera matrix, distortion coefficients, and the 3D-2D point correspondences.
   - Zhang's method utilizes a calibration pattern with known dimensions (checkerboard) and relies on geometric transformations to establish the mapping between the real-world points and the image points.

### The algorithm utilizes techniques such as corner detection, corner refinement, and nonlinear optimization to robustly estimate the camera parameters. It minimizes the reprojection error, which measures the discrepancy between the projected 3D points and the observed 2D image points, to achieve accurate calibration results.

The calibration parameters enable the correction of geometric distortions caused by the camera lens, allowing for precise measurements and accurate computer vision tasks.

## Getting Started

### Prerequisites

- Python
- OpenCV library
- glob library
- numpy

### Installation

1. Clone the repository:

```shell
git clone https://github.com/your-username/your-repo.git
```

# Usage:
  1.Place your checkerboard images in the images directory.
  2.Run the program:  python camera_calibration.py
  3.he program will detect the corners of the checkerboard in each image, refine the corner coordinates, and perform camera calibration.
  4.The calibration results, including the camera matrix, distortion coefficients, rotation vectors, and translation vectors, will be         displayed.

  5.The undistorted images will be saved in the undistorted_images directory.
  
  
# Results :
The calibration parameters enable the correction of geometric distortions caused by the camera lens, allowing for precise measurements and accurate computer vision tasks. The mathematical aspects of the algorithm involve solving a system of equations to estimate the camera matrix, distortion coefficients, and the 3D-2D point correspondences.

For more information, refer to the Zhang's camera calibration algorithm and the OpenCV documentation.
