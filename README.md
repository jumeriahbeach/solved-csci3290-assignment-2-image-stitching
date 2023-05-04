Download Link: https://assignmentchef.com/product/solved-csci3290-assignment-2-image-stitching
<br>
Image stitching is a technique to combine a set of images into a larger image by registering, warping, resampling and blending them together. A popular application for image stitching is creation of panoramas. Generally speaking, there are two classes of methods for image stitching, direct methods and feature-based methods. In this assignment, we will implement a feature-based method. It contains three parts: i) feature detection and matching, ii) homography estimation and iii) blending.

1.1         Feature detection and matching

Given two input images, detect SIFT features from them. And then establish the feature correspondence between SIFT features in the two input images using Brute-Force matcher. In OpenCV, there is a tutorial for SIFT <a href="https://docs.opencv.org/3.4/da/df5/tutorial_py_sift_intro.html">https://docs.opencv.org/3.4/da/df5/tutorial_py_sift_intro.html</a><a href="https://docs.opencv.org/3.4/da/df5/tutorial_py_sift_intro.html">,</a> and a tutorial for Brute-Force matcher <a href="https://docs.opencv.org/3.4/dc/dc3/tutorial_py_matcher.html">https://docs.opencv.org/3.4/dc/dc3/tutorial_py_matcher.html</a><a href="https://docs.opencv.org/3.4/dc/dc3/tutorial_py_matcher.html">.</a>

This part is corresponding to <em>extract and match feature </em>function in the provided skeleton code:

<table width="0">

 <tbody>

  <tr>

   <td width="421">                        <strong>def </strong>extract and match feature (img 1 ,               img 2 ,      ratio<em>”””</em><em>: param img 1 :        input      image 1</em><em>: param img 2 :        input      image 2</em><em>: param     r a t i o t e s t :      ratio      for     the              robustness</em></td>

   <td width="79">test =0.7):<em>test</em></td>

   <td width="23"></td>

   <td width="65"></td>

   <td width="63"></td>

  </tr>

  <tr>

   <td width="421">                         <em>: return             list </em><em>pairs </em><em>matched </em><em>keypoints :           a     l i s t</em><em>[ [ [ p1x , p1y ] ,[ p2x , p2y ] ] ]</em><em>””” </em>list pairs matched keypoints = [ ] <em># to be completed . . . .</em><strong>return </strong>list pairs matched keypoints</td>

   <td width="79"><em>of             pairs</em></td>

   <td width="23"><em>of</em></td>

   <td width="65"><em>matched</em></td>

   <td width="63"><em>points :</em></td>

  </tr>

 </tbody>

</table>

You need to do the following things in this function:

<ul>

 <li>extract SIFT feature from image 1 and image 2,</li>

 <li>use a bruteforce search to find pairs of matched features: for each feature point in img 1, find its best matched feature point in img 2,</li>

 <li>apply ratio test to select the set of robust matched points.</li>

</ul>

<h2>1.2         Homography estimation</h2>

The 2D image transformations (translation, rotation, scale, affine and perspective) can be represented as homography. Therefore, we can estimate the best homography by the matched pairs of features. Also, we employ RANSAC algorithm to eliminate the ”bad” matches. This can make our program more robust. In this section,you need to implement the RANSAC algorithm to find a robust homography between two input images using the feature correspondence.

This part is corresponding to <em>find homography ransac </em>function in the provided skeleton code:

1

<em>5 – Assignment 2: Image Stitching                                                                                                                                                        </em>2

<table width="0">

 <tbody>

  <tr>

   <td width="651"><strong>def </strong>find homography ransac ( list pairs matched keypoints , threshold ratio inliers =0.85, threshold reprojection error =3, max num trial =1000): <em>”””</em><em>: param list </em><em>pairs matched keypoints : a l i s t of pairs of matched points : [ [ [ p1x , p1y ] ,[ p2x , p2y ] ] , . . . ] : param t h r e s h o l dr a t i o i n l i e r s :</em><em>threshold on the ratio of i n l i e r s over the total number of samples , accept the estimated homography i f ratio is higher than the threshold : param threshold </em><em>reprojection </em><em>error :</em><em>threshold of reprojection error (measured as euclidean distance , in pixels ) to determine whether a sample is i n l i e r or outlier : param max num trial :</em><em>the maximum number of t r i a l s to take sample and do testing to find the best homography matrix</em><em>: return      best </em><em>H :     the     best        found homography        matrix</em><em>”””</em>best H = None<em># to     be     completed      . . .</em><strong>return </strong>best H</td>

  </tr>

 </tbody>

</table>

<h2>1.3         Blending</h2>

Having the estimated homography, we can warp the second image to align with the first image and then blend them together to get a a single panorama image. For warping, we employ inverse warping and bilinear resampling.

This part is corresponding to <em>warp </em><em>blend image </em>function in the provided skeleton code:

<table width="0">

 <tbody>

  <tr>

   <td width="651"><strong>def </strong>warp blend image (img 1 , H,                   img 2 ):<em>”””</em><em>: param img 1 :       the       original       f i r s t    image</em><em>: param H:        estimated       homography</em><em>: param img 2 :       the       original       second     image</em><em>: return        img panorama :         resulting            panorama image</em><em>”””</em>img panorama = None<em># to be completed . . . </em><strong>return </strong>img panorama</td>

  </tr>

 </tbody>

</table>

You need to do the following things in this function:

<ul>

 <li>warp image img 2 using the homography H to align it with image img 1 (using inverse warping and bilinear resampling),</li>

 <li>stitch image img 2 to image img 1 and apply average blending to blend the two images into a single panorama image.</li>

</ul>

<em>5 – Assignment 2: Image Stitching</em>