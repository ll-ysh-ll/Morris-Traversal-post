# Morris Traversal
### Quick Introduction :
##### Tree :
- > Tree is a hierarchical data structure which stores the information naturally in the form of hierarchy unlike linear data structures like, Linked List, Stack, etc. A tree contains nodes(data) and connections(edges) which should not form a cycle.
##### Tree Traversal :
- > “In computer science, tree traversal (also known as tree search) is a form of graph traversal and refers to the process of visiting (checking and/or updating) each node in a tree data structure, exactly once. Such traversals are classified by the order in which the nodes are visited.” — Wikipedia

##### Tree Traversal Algorithms :

- Depth-First Search (DFS) Algorithm
- Breadth-First Search (BFS) Algorithm


### Complexity analysis

Both recursive and iterative traversal takes O(n) space in worst case, while Morris traversal will take O(1) space.
- T.C: O(n)
- S.C: O(n)

> Note: Only `Inorder traversal` has been discussed in this article.

### Threaded Binary Tree 
> The idea of threaded binary trees is to make inorder traversal faster and do it without stack and without recursion. A binary tree is made threaded by making all right child pointers that would normally be NULL point to the inorder successor of the node (if it exists).

<p align="center">
<img src="https://github.com/ll-ysh-ll/Morris-Traversal-post/blob/master/Threaded%20Binary%20Tree.jpg"  width="575">
</p>

### Algorithm 

```sh
1. initialize current as root 
2. while current exists
   if current has a left child
      if a) get the rightmost child of leftsubtree and add current to its right
      if b) rightmost child of leftsubtree is pointing to current:
            print current’s data and destroy the link
            go to the right
      go to this left child
   else
      a) print current’s data
      b) go to the right
```

### Visual Representation 
<p align="center">
<img src="https://github.com/ll-ysh-ll/Morris-Traversal-post/blob/master/Morris_Traversal_gif.gif" width="575"/>
</p>

### Python Code 

```python 
def inorderMorrisTraversal(self, root: TreeNode) -> List[int]:
    curr = root
    res = []
    while curr:
        if curr.left:
            pre = curr.left
            while pre.right and pre.right!=curr:
                pre = pre.right
            if pre.right == curr:
                pre.right = None
                res.append(curr.val)
                curr = curr.right
            else:
                pre.right = curr
                curr = curr.left
        else:
            res.append(curr.val)
            curr = curr.right
    return res
```

#### References :

[c why you should be aware of morris traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/discuss/2153281/c-why-you-should-be-aware-of-morris-traversal)

[CPP Morris Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/discuss/148939/CPP-Morris-Traversal)

[4 types of tree traversal algorithms](https://towardsdatascience.com/4-types-of-tree-traversal-algorithms-d56328450846)

[threaded binary tree](https://www.geeksforgeeks.org/threaded-binary-tree/)

[Morris traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/discuss/706892/Python%3A-Morris-traversal)
