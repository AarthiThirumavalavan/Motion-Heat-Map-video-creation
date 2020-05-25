# Motion-Heat-Map-video-creation
Building Motion Heat Map video using OpenCV

#Explanation to the process
1.	Video is read from the input file “input.mp4”

2.	Gaussian Mixture-based Background/Foreground Segmentation Algorithm is used (cv2.createBackgroundSubtractorMOG2()) 

3.	This is one of the background subtraction methods available in OpenCV (as a part of preprocessing this step is done)

4.	Frame count is calculated

5.	The first frame is read using capture.read() 

6.	Since it is the first frame that is read initially, it is made a reference frame and deep copy of original frame at position 0 happens

7.	This is part of the background initialization that happens

8.	accum_image array is initialized with same size as that of frame

9.	If not first frame, the background subtractor is applied on that frame to remove the background noise and a filter is created

10.	This is then written into the folder location as “frame.jpg”

11.	The frame with filter applied is written into the folder location as “diff-bkgnd-frame.jpg”

12.	cv2.threshold is applied to reduce small amounts of disturbance such as wind, small bird flying etc.

13.	Threshold is applied to the mask along with maxValue

14.	If pixel value is greater than a threshold value, it is assigned one value (may be white), else it is assigned another value (may be black). (cv2.threshold - First argument is the source image, which should be a grayscale image. Second argument is the threshold value which is used to classify the pixel values. Third argument is the maxVal which represents the value to be given if pixel value is more than (sometimes less than) the threshold value. OpenCV provides different styles of thresholding and it is decided by the fourth parameter of the function.)

15.	Result of mask is added to accum.image array

16.	This operation performed for each frame

17.	The result is that accum_image array stores movement in each frame relative to the original initialized frame reference

18.	These operations are done for each frame and colormap is applied to the mask

19.	Mask is merged with the current frame

20.	Video is generated showing the heatmap for every frame. to do this, each frame is exported and merged together using cv2
