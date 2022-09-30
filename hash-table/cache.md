# Cache

Cache is a in-memory data structure to reuse accessed data from database, disk or some other low-speed sources.

## LRU

Remove the least recently used element when cache is full.

We can combine a hash-map and a linked-list to implement a cache with O(1) time complexity.

## LFU

Remove the least frequently used element when cache is full.

We can combine a hash-map and a heap to implement a cache with O(logN) time complexity.

Or we can combine two doubly linked list to implement a cache with O(1) time complexity.

## Redis