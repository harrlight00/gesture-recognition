Goal

The goal is to use openCV to differentiate 3 gestures, including a peace sign and an open hand as static gestures, and a finger-wave as a motion.

Method

After creating a skeleton that could input and parse video, we processed the video using various openCV implentations.  
First, we used cv2.cvtColor to transform the data to grayscale, then used Gaussian Blur and Image Thresholding to implement 
a version of background differencing.  After performing the same process on our template data, this allowed us to easily use 
template matching to match static gestures with our target gestures: a peace sign, an open hand, and a single finger for the 
motion detection.  We first checked for motion data by matching the finger template to a background reduced mask and tracked the
motion of that finger wave.  If we did not find motion data, we used template matching to check for the peace sign or the open 
hand gesture.  We also made sure to add a template picture for both the right and left hand for each gesture, so that our function 
would properly mark either hand.  Our system can only recognize one thing at a time, so unfortunately if someone put up 
double peace signs, it would only recognize one.  After using template matching on our live video feed, if a match was found 
for any gesture, we would draw a rectangle around it in an assigned color, and affix a label of the same color to it (as 
seen in section (#1).
