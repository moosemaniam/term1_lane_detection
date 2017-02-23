#**Finding Lane Lines on the Road**
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1.Pipeline description

1) Convert image to greyscale and add blurring
2) Get the edges in the image
3) Define a region on interest to remove information that we are not interested
in. Basically remove anything other than the road
4) Apply hough transform to identify a set of lines
5) I then changed the draw_lines function like below
   a) Calculate the slope and intercept of each line and classify them as left
   lane or right lane
   b) Once classified, take a average of these lines one for each lane
   c) Now that we have a slope and intercept for each lane, fit such a line
   within the ROI that we defined in step 3
   d) draw these lines on the image



###2. Shortcomings of current pipeline
1) If the road curves, the line detection picks the points on the other lane
   and the lane markings may flicker a bit
2) In the list of lines for each lane, there may be outliers. ie lines which
   are not essentially part of the lane.

###3. Possible improvements to your pipeline

1) Possibly fit a curve instead of a line
2) Have a outlier detector and remove lines which have slopes and intercepts which are
   far removed from the average slope and intercept. This might reduce the
   flickering that sometimes occurs
