Automated OMR Test Scoring System using Image Processing
This project is an application built with Python and OpenCV to automate the process of grading multiple-choice answer sheets. The system can analyze a scanned image or photograph of an answer sheet, identify the marked bubbles, and extract the results quickly and accurately.

Demo
The system is capable of processing multi-column answer sheets like the one below:

Key Features
Automatic Sheet Detection: Automatically finds and isolates the answer sheet from any background in an image.
Perspective & Skew Correction: Applies a Perspective Transform to "flatten" the answer sheet, removing any skew or distortion from the scanning or capturing process.
Mark Recognition: Segments the answer bubbles, applies binary thresholding, and analyzes pixel density to accurately determine the option selected by the student.
Multi-Column Support: Capable of processing layouts with two columns of questions (e.g., questions 1-10 and 11-20).
Result Extraction: Outputs a final list of the student's answers in character format (A, B, C, D) for easy review and grading.
Technologies Used
Language: Python
Libraries:
OpenCV: Used for core image processing tasks (edge detection, contour finding, image transforms).
NumPy: Used for high-performance array manipulation and numerical calculations.
imutils: Provides convenience functions to simplify image processing tasks.
Jupyter Notebook: The development and presentation environment for this project.
Setup and Usage (with Anaconda)
Clone the repository to your local machine:

Bash

git clone [YOUR_REPOSITORY_URL]
cd [YOUR_PROJECT_DIRECTORY]
Create and activate an Anaconda environment:
Open Anaconda Prompt (or Terminal) and run the following commands. This creates a separate environment to avoid package conflicts.

Bash

# Create a new environment named 'omr_project' with Python 3.9
conda create --name omr_project python=3.9

# Activate the environment
conda activate omr_project
Install the required libraries:
Once the environment is active, run the following command to install all necessary packages.

Bash

pip install opencv-python numpy imutils matplotlib jupyter
Navigate to the project directory:
Use the cd command to navigate to the folder where you saved the project files.

Bash

cd path/to/your/project/folder
Launch Jupyter Notebook:

Bash

jupyter notebook
This command will open a new tab in your web browser. Click on the .ipynb file (e.g., Giuaki.ipynb) to open it and run the code.

Technical Workflow (How It Works)
Preprocessing: The input image is converted to grayscale and a Gaussian Blur is applied to reduce noise.
Sheet Finding: The Canny algorithm detects edges. findContours is then used to find the largest 4-cornered contour, which is identified as the answer sheet.
Rectification: warpPerspective is used to transform the image, creating a flat, top-down view of the sheet.
Segmentation & Recognition:
The sheet is split into columns and then further divided into individual answer bubbles using vsplit and hsplit.
Otsu's Thresholding is applied to binarize the image, separating marked areas from the white paper.
countNonZero counts the marked pixels in each bubble.
np.amax finds the bubble with the maximum number of marked pixels, determining it as the final answer.
Output: The index of the selected answer is mapped to its corresponding character (A, B, C, D).
