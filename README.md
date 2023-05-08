Download Link: https://assignmentchef.com/product/solved-tdt4195-assignment-3
<br>
In this assignment, we will explore how we can segment an image into foreground and background by using basic segmentation algorithms, such as thresholding and region region growing. Then, you will explore how we can use binary morphological operations to manipulate the contents of a binary image.

<h1>Task 1: Theory</h1>

<ul>

 <li>Define <em>opening </em>and <em>closing </em>in terms of <em>erosion </em>and <em>dilation</em>. What happens when open and closing are applied multiple times on the same image?</li>

 <li>Smoothing of an image is often done before performing edge detection. What is the purpose of smoothing the image before edge detection?</li>

 <li>The Canny edge detector uses a method called <em>hysteresis thresholding</em>. Shortly explain how hysteresis thresholding work.</li>

 <li>Why do we use hysteresis thresholding instead of a single treshold?</li>

 <li>Determine the dilation <em>A </em>⊕ <em>B </em>of the binary image in Figure 1a. Use the structuring element in Figure 1b.</li>

</ul>

<table width="166">

 <tbody>

  <tr>

   <td width="28">0</td>

   <td width="27">1</td>

   <td width="28">0</td>

   <td width="27">1</td>

   <td width="28">0</td>

   <td width="28">0</td>

  </tr>

  <tr>

   <td width="28">0</td>

   <td width="27">1</td>

   <td width="28">0</td>

   <td width="27">1</td>

   <td width="28">1</td>

   <td width="28">0</td>

  </tr>

  <tr>

   <td width="28">0</td>

   <td width="27">1</td>

   <td width="28">1</td>

   <td width="27">1</td>

   <td width="28">0</td>

   <td width="28">0</td>

  </tr>

  <tr>

   <td width="28">0</td>

   <td width="27">0</td>

   <td width="28">0</td>

   <td width="27">0</td>

   <td width="28">0</td>

   <td width="28">0</td>

  </tr>

  <tr>

   <td width="28">0</td>

   <td width="27">0</td>

   <td width="28">1</td>

   <td width="27">0</td>

   <td width="28">0</td>

   <td width="28">0</td>

  </tr>

  <tr>

   <td width="28">0</td>

   <td width="27">0</td>

   <td width="28">0</td>

   <td width="27">0</td>

   <td width="28">0</td>

   <td width="28">1</td>

  </tr>

 </tbody>

</table>

<table width="69">

 <tbody>

  <tr>

   <td width="23">1</td>

   <td width="23">•</td>

   <td width="23">1</td>

  </tr>

 </tbody>

</table>

(b) A 1×3 structuring element

(a) A 6 × 6 binary image.

Figure 1: A binary image and a structuring element. The foreground is colored white and given the symbol 1. The background has the symbol 0 and is colored black. The reference pixel in the structuring element (b) is indicated by a black circle.

<h1>Programming</h1>

<h2>Task 2: Segmentation</h2>

Segmentation by thresholding on pixel intensity is a intuitive, computational efficient, and simple way of implementing image segmentation. Selecting a good value for thresholding is a cumbersome process that is best left up to a threshold detection algorithm. One automatic algorithm for selecting a good threshold in a grayscale image is Otsu’s method. The algorithm finds a single threshold value that separates pixels into two classes, foreground and background. The basic idea is that a threshold giving the best separation between classes in terms of their intensity values would be the optimum threshold. In the assignment files we have included the file otsu-thresholding.pdf, scanned from the curriculum book [1], which describes the algorithm in detail.

(a)Implement a function in task2a.py/task2a.ipynb that implements Otsu’s algorithm for thresholding, and returns a single threshold value.

Segment the images thumbprint.png and polymercell.png, and include the results in your report.

<ul>

 <li>X-ray image of a defective (b) Segmented using <em>Otsu’s </em>(c) Segmented using <em>region grow</em>weld <em>thresholding algorithm</em>. <em>ing </em>with four manually selected</li>

</ul>

seed points.

Figure 2: Two different ways to segment the image in (a). Image source: [1]

Region growing is a region-based segmentation algorithm that uses a set of seed points and a homogeneity criteria <em>H</em>(<em>R<sub>i</sub></em>) to perform segmentation. For each seed point, a region is grown by inspecting neighboring pixels and evaluating whether or not to include them in region <em>R<sub>i </sub></em>using <em>H</em>(<em>R<sub>i</sub></em>). The neighboring pixels that are currently being evaluated are typically called <em>candidate pixels</em>. The growing of a region stops when there are no more candidate pixels to inspect. The simplest homogeneity criteria is a threshold, where the threshold defines the maximum absolute difference in intensity between the seed point and the current candidate pixel.

<ul>

 <li>Implement a function in task2b.py/task2b.ipynb that segments a grayscale image using the region growing method outlined above. Use a Moore neighborhood (8-connectedness) to expand your set of candidate pixels around each seed point.</li>

</ul>

Apply it on the image defective-weld.png and show the result in your report. Use the 4 seed points given in the starter code and use a pixel intensity threshold of 50.

<em>Hint: </em>To make sure you implement the code correct, you should test your algorithm with a pixel intensity threshold of 90.

<h2>Task 3: Morphology</h2>

For the following tasks, you are allowed to use already implemented functions for opening, closing, erosion, and dilation. Skimage has several useful functions for this:

<ul>

 <li><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_dilation">skimage</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_dilation">.</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_dilation">morphology</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_dilation">.</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_dilation">binary_dilation</a></li>

 <li><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_erosion">skimage</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_erosion">.</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_erosion">morphology</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_erosion">.</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_erosion">binary_erosion</a></li>

 <li><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_closing">skimage</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_closing">.</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_closing">morphology</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_closing">.</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_closing">binary_closing</a></li>

 <li><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_opening">skimage</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_opening">.</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_opening">morphology</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_opening">.</a><a href="https://scikit-image.org/docs/dev/api/skimage.morphology.html#skimage.morphology.binary_opening">binary_opening</a></li>

</ul>

(a) A noisy binary image                   (b) An almost noise free version    (c) A distance transform of the of (a) after morphological opera-   binary image in (b) using chesstions.          board distance.

Figure 3: Morphology operations on a binary image (a). Image source: [1]

<ul>

 <li>Use what you know about erosion, dilation, opening, and closing to remove the noisy elements from the image in Figure 3. Implement this in the file py/task3a.ipynb. Your result should look something like the one in Figure 3b.</li>

</ul>

Include the resulting image in your report and shortly explain how you removed the noise.

The distance transform is an operation typically applied on a binary image and creates a grayscale image where each foreground pixel shows the distance to the closest boundary pixel. An example of this using chessboard distance can be seen in Figure 3c. The chessboard distance is the minimum number of moves a king has to perform to move from one square (or pixel in our case) to another square in the game of chess.

One inefficient way of calculating the distance transform is to use erosion. Intuitively, by using erosion the distance transform for a pixel is simply the number of erosion operations it took to remove it from the foreground of the original image.

<ul>

 <li>Implement the distance transform using the erosion method explained above, in the file py/task3b.ipynb.ipynb. You can use a 3 × 3 structuring element of all ones to get chessboard distance.</li>

</ul>

Test the function on the noise free binary image you got from task (a) and show the result in your report.

Mathematical operations can be used for extracting boundary information from images. The operation for extracting the inner boundary extraction can be seen in Equation 1, where        is erosion.

)                                                    (1)

<ul>

 <li>Implement a function that extracts the boundary from a binary image, as defined in Equation 1, in the file py/task3c.ipynb. You can use a 3 × 3 structuring element of all ones.</li>

</ul>

Show the boundary on the image lincoln.png and include the result in your report.

Hole filling is a method to fill in holes in a segmentation, and is very useful for post-processing imperfect segmentations. Algorithm 1 outlines a basic algorithm that takes a binary image and fills all known holes indicated by a set of starting points.

<strong>Algorithm 1 </strong>A algorithm to fill holes in a binary image <em>I</em>. ⊕ is the dilation operation, <em>I<sup>c </sup></em>is the complement of <em>I</em>, and ∪ is the union.

1: <strong>Input: </strong>Image <em>I</em>, number of iterations <em>K</em>, starting points <em>S</em>, and structuring element <em>B</em>.

2: Form an array, <em>X</em><sub>0</sub>, of 0’s (the same size as the Image <em>I</em>)

3: <strong>for </strong>row, column in <em>S </em><strong>do </strong>4: <em>X</em><sub>0</sub>[<em>row,column</em>] ← 1

5: <strong>for </strong><em>k </em>← 1 to <em>K </em><strong>do</strong>

6:                   <em>X<sub>k </sub></em>← (<em>X<sub>k</sub></em><sub>−1</sub>⊕ <em>B</em>) ∩ <em>I<sup>c</sup></em>

7: <strong>return </strong><em>X<sub>k </sub></em>∪ <em>I</em>

(d) Implement a function that takes in a binary image and a set of starting points indicating position of holes, and applies the hole filling algorithm outlined in Algorithm 1. Implement this in the file task3d.py/task3d.ipynb.

Apply the function on the image balls-with-reflection.png and include the resulting image in your report. The position of the holes are given in the starter code. Use 30 iterations (<em>K </em>= 30), and a 3 × 3 structuring element (<em>B</em>) of all 1’s.