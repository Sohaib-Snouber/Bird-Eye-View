# Bird-Eye-View
Transforming the front view to top view according to a homography matrix

The used algorithm is depending on a checkerboard, that will be striaght on floor, and an image of it will be taken as front view of the checker board. it will be noticed that the width of the chekerboard will get reduced along the camera, and the purpose of top view or as it called bird eye view is to get the a view with not distorted dimensions, that mean the result of top view should show, that the lengths of squares' width and height are equal. so to get that result i have some thoghts to do it, before explaining my solution, lets see the fuctions that my solution depends on.

the following function have been used in my code to get the final top view:
**********************
so the function ()_give us the all coodrinates of all corners in the checkerboard, but i have only choose the outer four corners, so i can get the shape of checkerboard.
adn these four corners are the old position of corners, before the transformation, and after transformation, these old points should move according to some specific calculations.
the  calculation that i depends on as a solution for the new positions of the old points is as follows:

first: to get the full sight at the end, i assumed the x(width) value of the top corners to be the same as the old, so we dont change the away line of view.

second: we calculate the difference between the width of top left corner with the width of the bottom left corner and we call it as difference 1, and the same with right side, and we get difference 2
third: now we add the absolute value of difference 1 to the width of bottom left corner as new bottom left corner point, and subtract the absolute value of differecne 2 from the width of bottom right corner
fourth: because i have in last step some changes in the width, we shoud make the same changes to the height, so we get equal length of square sides, By adding the difference 1 abd difference 2 to the height of both top corners.

now we have bothe old and new points, by using the function ()_ get the old and new points as inputs ang give us the output transformation matrix according to the given actual and desired locations points.
then the transformation matrix should be given to the warpPerspective function to apply the laste defined transformation matrix on the image to get the top view from the front view.

