# Disjoint Sets && Union-Find

- Determine which set an item belongs to
- Test if two items belong to the same set
- Union two disjoint sets into one when needed  

**Usage:**
- Find connected components in an undirected graph
- Kruskal's algorithm for the Minimum Spanning Tree (MST) problem.


**Disjoint Set (tree) -> Disjoint forest (represented by root)**

## Implementation
- p[N] where p[i] is the parent of item i  
    - for root & representative item, p[i] = i
- rank[N] where rank[i] is the upperbound of the height of subtree rooted at vertex i （*height?
    - guiding heuristic for UnionSet(i, j) operation. 
    - after ’path-compression' the rank values no longer reflect the true height of that subtree.

## Operation
### Initialize(N) 
- Create N disjoint sets, all with p[i] = i and rank[i] = 0 
- O(N)

### FindSet(i)
- for vertex i -> go to vertex p[i] until reach the root (p[i] = i)
- O(1) : path-compression heuristic -> directly point to the root node (expect the first run) 
* rank is wrong after path-compression but won’t fix it *

### IsSameSet(i, j) <- FindSet(i) + FindSet(j)
- check FindSet(i) == FindSet(j) ? 
- path-compression heuristic (indirectly).
- O(1)
- -> Kruskal's MST algorithm.

### UnionSet(i, j)  
<-isSameSet(i,j) <- FindSet(i) + FindSet(j)
- if i,j comes from different tree/DS (FindSet(i,j): Link root of the shorter one to the root of the taller tree/DS
- union-by-rank heuristic: get relatively short tree. 
    - if rank(i)==rank(j) (equally tall), rank[result]++
- path-compression heuristic (indirectly): 每次压缩路径，至少会引起一个rank不正确。但是不用fix
- O(1)

## Actual TC: O(α(N)) 
* when both heuristics are implemented *
- inverse Ackermann function α(N)
    - grows extremely slowly. α(1M) ≈ 1.