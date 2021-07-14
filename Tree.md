# Trees 

#### We'll be covering Binary Trees , Binary Search Trees and K-ary Trees 


# common Terminology  :
* Node : it's a component which may contain it's own values and references to other nodes
* Root : it's the node at the beginning of the tree .
* K : it's specifies the maximum number of children any node may have in a key- ary tree 
* Left : it's a referance to one child node , in a binary tree .
* Right: it's a referance to the other child node , in a binary tree 
* Edge : the edge in a trees is the link between a parent and child node 
* Leafe : it's the node that does not have any children
* Height : it's the number of edge from the root to the furthest leaf




![BinaryTree1](https://user-images.githubusercontent.com/79080942/125592351-30d28706-19fe-4c38-a66c-2be9025d02d3.png)


## Traversals 

traversing a tree allows us to search for a node print out the content of a tree .
there are two categories :
* Depth First : is where we prioritize going through the depth (height) of the tree first 
and it's have 3 methodes :

##### *pre-order : root >> left >> right
##### *In-order : left >> root >> right
##### *Post-order : left >> right >> root

![tree-example](https://user-images.githubusercontent.com/79080942/125593355-9a40a0a7-fe41-4fb9-a5a1-f47087849416.png)

##### *pre-order : root >> left >> right
##### *pre-order : A , B , D , E , C , F 

##### *In-order : left >> root >> right
##### *In-order : D , B , E , A , F , C

##### *Post-order : left >> right >> root
##### *Post-order : D , E , B , F , C , A 


I just understand this actually , soory about that .



