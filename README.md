# Collision Detection using Quad Trees

Quad Tree is a data structure in which every internal node has exactly 4 children, as is evident from the prefix 'Quad'. Quad trees are used to partition space into 4 quadrants or regions. Partitioning occurs when the number of points in a quadrant exceedes a certian threshold (usually a small number like 1 or 2). Usually, such parititioning is recursive in nature. Every sub quadrant that gets formed due to the parition is a child of the parent quadrant which was partitoned. Every leaf node of a quad tree contains some special spacial information (for example, coordinates of a point in a region). It is also important to note that internal nodes themselves do not hold spatial information. The spaitial information is pushed all the way down the quad tree to the leaf level.

## Use cases:

1. Image Processing
2. Mesh generation
3. Efficient collision detection

## Efficient Collision Detection
This project focuses primarily on the collision detection use case of quad trees. Let's suppose we have n point-sized objects in some space. We can detect collisions easily using the naive O(n^2) implementation (checking every point against the other). Although this might seem feasible for very small n, the algorithm is very inefficient even for small n = 100 (10^4 comparisions). A more efficient (and elegant) solution is to use quad trees. The idea is to insert all the points in a quad tree (keeping in mind the properties mentioned above). Since expected time for insert into a quad tree is O(log n), inserting all of the n points costs O(nlogn) time for the expected case. (Note in theory, height of a quad tree can be unbounded, which can dramatically affect performance. However, this happens only if the distribution of points is very uneven). Once the quad tree is built, we simple traverse the tree using a depth first search and upon hitting a leaf node, use the naive algorithm (since every leaf node can only ever contain a maximum number of points bounded above by the threshold mentioned before). Thus, for n = 100, this algorithm performs much better, as it makes at most 100log(100) = 200 comparisons as opposed to 10^4 comparisons (expected case). 

# Examples:

In these examples, collisions are shown in red. The grids are visual representations of the quad tree that is dynamically built using the data points at runtime. 

## Example 1
![alt text](https://github.com/arp001/Collision-Detection-using-Quad-Trees/blob/cd-qd/80fps200objs.gif)
## Example 2
![alt text](https://github.com/arp001/Collision-Detection-using-Quad-Trees/blob/cd-qd/25fps100objs.gif)
## Example 3
![alt text](https://github.com/arp001/Collision-Detection-using-Quad-Trees/blob/cd-qd/60fps15objs.gif)

## Author

Arpit Hamirwasia, 2017
