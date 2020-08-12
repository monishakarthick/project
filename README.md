# CLOSEST PAIR OF POINTS:

## Question Statement:

* Generate a random pair of 100 values. Apply the closest pair algorithm to find the closest pair(distance). A C++ implementation from scratch implementation is with neat documentation is expected.The time complexity of the algorithm should be O(N log N).

# ALGORITHM:

## STEP 1:

* The input array is sorted according to x coordinates.
* Find the middle point in the sorted array, we can take P[n/2] as middle point.
* Divide the given array in two halves. The first subarray contains points from P[0] to P[n/2]. The second subarray contains points from P[n/2+1] to P[n-1].

## STEP 2:

* Recursively find the smallest distances in both subarrays. Let the distances be dl and dr. Find the minimum of D_Left and D_Right. Let the minimum be min_dist.

![mindis](https://user-images.githubusercontent.com/69573313/90012430-faeeb180-dcc0-11ea-97ec-5dc8ff0180a4.png)

## STEP 3:

* From the above steps, we have an upper bound min_dist of minimum distance. Now we need to consider the pairs such that one point in pair is from the left half and the other is from the right half. Consider the vertical line passing through P[n/2] and find all points whose x coordinate is closer than d to the middle vertical line. Build an array stp[] of all such points.

![closepair](https://user-images.githubusercontent.com/69573313/90012559-3ab59900-dcc1-11ea-8331-5449e4fa26b5.png)


## STEP 4:

* Sort the array stp[] according to y coordinates. This step is O(nLogn). It can be optimized to O(n) by recursively sorting and merging.
* Find the smallest distance in stp[]. This is tricky. From the first look, it seems to be a O(n^2) step, but it is actually O(n). It can be proved geometrically that for every point in the strip, we only need to check at most 7 points after it (note that strip is sorted according to Y coordinate). See this for more analysis.

## STEP 5:

* Finally return the minimum of d and distance calculated in the above step (step 4).

# Time Complexity:

* Let Time complexity of above algorithm be T(n). Let us assume that we use a O(nLogn) sorting algorithm. The above algorithm divides all points in two sets and recursively calls for two sets. After dividing, it finds the strip in O(n) time, sorts the strip in O(nLogn) time and finally finds the closest points in strip in O(n) time. So T(n) can expressed as follows
T(n) = 2T(n/2) + O(n) + O(nLogn) + O(n)
T(n) = 2T(n/2) + O(nLogn)
T(n) = T(n x Logn x Logn)
