# A VR Image using OpenCV and Blender
A program that tracks the location of the head and then displays an image of the 3D model at a certain angle, based on the head’s location so that the image looks 3 dimensional.
<img src="https://img.shields.io/github/issues/Sanscode2911/3D-image-visualizer"> <img src="https://img.shields.io/badge/Dev-InProgress-orange"></br>
This may sound fairly simple. However, simply displaying the rendered image wasn’t sufficient when it’s at an angle. Why? It’s because what we see is actually a perspective view and this should be accounted for in order for the view to seem realistic to the user.</br>
## What We Did
1. We created a simple 3D scene, with a cube with one side open and a vase placed inside the cube.
2. We set the camera to always point at the cube and programmed a python script inside Blender to always position towards it while maintaining a constant distance from the cube.
3. Next We programmed the camera to move in small increments, rendering the camera view at each location. First We tried using fairly large increments but the video output seemed quite jerky. So We decided to go with smaller increments. This is not the most space efficient method as We now have 600 images in a folder. However We had no choice but to do it this way due to the issue with the perspective We previously mentioned.
4. We found a python script online that uses OpenCV to warp any quadrilateral into a square. We altered it such that the images are loop over and the corners of the open face of the cube could be selected and the warped images were saved into a folder.
5. Next came the most tedious and time consuming part. We had to go through 600 images and manually select the points representing the corners of the open faces of the cubes in each image in order for it to be warped. If We understood the Blender rendering system enough, We could probably automate this step. Maybe someday We will 😉.
6. Afterwards We wrote the code for the face detection using OpenCV and the pretrained haarcascade model. For this, We decided to step out of our comfort zone and write the code in C++. Using C++ also meant that We had to install OpenCV for the entire system instead of just pip install for python. We decided to go with building from source. After multiple failed attempts of using Visual Studio Code and Code::Blocks to compile any OpenCV program without a linker error, We decided to give Microsoft Visual Studio a try which was also a program We wanted to familiarize ourselves with. Fortunately, this worked great. So two birds in one stone 😁.
7. Now all We had to do was to determine the correct image out of the warped images (depending on the location of the head) and display it.

And lo and behold, it’s finally working.


It does still seem a little bit jerky. I can think of 2 possible reasons for this.</br>
◾The slight irregularities in face detection.</br>
◾The human error on our part when marking the corners: This could be solved by automating this step as previously mentioned.
