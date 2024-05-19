Introduction to C++ and Basic Geometry
======================================

The goal of this first assignment is to get familiar with CMake and C++ by implementing two basic algorithms in geometry.
In the exercise, you will implement a function to test whether a point is inside a polygon in 2D.

### Preparing the Environment

Follow instructions the [generale rules](../Rules.md) to setup what you need for the assignment. You can also install [Meshlab](http://www.meshlab.net/) to visualize the datasets (point cloud and polygons) that you will be using in this assignment.


##### File Format

We store point clouds as simple ASCII file in XYZ format. The file format is as follows:

```
3000
222.582 555.88 0
226.411 535.734 0
226.83 529.925 0
269.326 472.13 0
248.178 518.121 0
...
```

The first line indicates the number of points N. The following N lines contains a space-separated list of each point coordinates. Note that our case, we will ignore the 3rd coordinate when reading the data.

Polygons will be stored using a simple [OBJ file format](https://en.wikipedia.org/wiki/Wavefront_.obj_file), which is a list of points, followed (in this case) by a list of edges forming the polygon:

```
v 115.976000 432.047000 0
v 116.430000 529.603000 0
v 123.848000 534.238000 0
...

l 1 2
l 2 3
l 3 4
```

Note that indexing starts with 1 in OBJ files, so remember to shift indices accordingly.



Ex.1: Point In Polygon [7pt]
----------------------

### Description

In this exercise, the goal is to test whether a point is inside a polygon or not. This is called the [Point In Polygon](https://en.wikipedia.org/wiki/Point_in_polygon) test.
The principle is as follows: given a point Q and a polygon P, draw a line from the query point Q to some other point far away in the plane (which should be outside P). Then, count the number of segments in P that this line intersects. This method to compute the inside/outside of a polygon is also called the even-odd rule.

### Code

Compile and run the code as follows:

```
mkdir build; cd build; cmake ..; make
./assignment1
```

### Tasks

1. Complete the function to read .xyz from a file. While it is perfectly fine to use C's `printf()` and `scanf()` functions in C++, the idiomatic way to read/write data is to use `std::iostream<>`, which provides additional type-safety compared to C's equivalent.
2. Write a function to save an XYZ point cloud.
3. Write the function to determine whether two segments intersect.
4. Compute the bounding box of the input polygon, then find a point that is guaranteed to be outside the input polygon.
5. Write the *Point In Polygon* function.

### Result

Here is an image of the dataset provided in this assignment:

![](img/points.png?raw=true)

- The input `points.xyz` are shown in green.
- The polygon in `polygon.obj` is shown in red.
- The points from `points.xyz` which are inside `polygon.obj` are shown in yellow.
