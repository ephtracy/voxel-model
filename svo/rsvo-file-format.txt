.rsvo file format | @ ephtracy | 03/22/2015

version 1
- storage for binary sparse voxel octree (SVO)
- children masks of internal nodes in breadth-first search (BFS) order
- all leaf nodes are at level 0

==============================================================================================
# bytes | description               | value
==============================================================================================
4 bytes | magic number              | "RSVO", 'R' is at byte 0, 'O' is at byte 3
4 bytes | version                   | 1
----------------------------------------------------------------------------------------------
4 bytes | info 0 : reserved         | 0
4 bytes | info 1 : reserved         | 0
----------------------------------------------------------------------------------------------
4 bytes | top level (N)             | e.g. top level 14 == volume size 16384 (2 ^ 14)
----------------------------------------------------------------------------------------------
4 bytes | # nodes at level (N)      | unsigned int | root level, always 1
4 bytes | # nodes at level (N) - 1  | unsigned int
...
4 bytes | # nodes at level 0        | unsigned int | leaf level
----------------------------------------------------------------------------------------------
1 byte  | children mask of internal nodes in bfs order at level (N)
X bytes | children mask of internal nodes in bfs order at level (N) - 1
...
X bytes | children mask of internal nodes in bfs order at level 1
(* no leaf level )
==============================================================================================