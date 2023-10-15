[Paper](http://arborjs.org/docs/barnes-hut)

The main purpose of this algorithm is to speed the brute force [n-body algorithm](https://en.wikipedia.org/wiki/N-body_simulation) by grouping nearby bodies and approximate them as a single body.

If the group of bodies is far away from a threshold, we can approximate the gravitational forces using the center of mass.

Formally, if two bodies have positions (`x1`, `y1`) and (`x2`, `y2`), and masses `m1` and `m2`, then their total mass and center of mass (`x`, `y`) are given by:

```
m = m1 + m2  
x = (x1*m1 + x2*m2) / m  
y = (y1*m1 + y2*m2) / m
```

## How the algorithm works
It recursively divides the set of bodies into groups by storing them in a _quad-tree_. A quad-tree is similar to a binary tree, except that each node has 4 children (some of which may be empty). Each node represents a region of the two dimensional space.

The space is recursively subdivided into quadrants until each subdivision contains 0 or 1 bodies
![[Barnes-Hut Quadrant.png]]

![[Barnes-Hut Quad Tree.png]]

