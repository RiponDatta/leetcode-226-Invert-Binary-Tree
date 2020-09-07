# leetcode 226 - Invert Binary Tree
## Approach 1: Recursive
### C#
```C#
public TreeNode InvertTree(TreeNode root)
{
    if (root == null) return root;
    var temp = root.left;
    root.left = root.right;
    root.right = temp;

    root.left = InvertTree(root.left);
    root.right = InvertTree(root.right);

    return root;
}
```
### Java
```Java
public TreeNode InvertTree(TreeNode root) {
	if(root == null) return root;
	TreeNode temp = root.left;
	root.left = root.right;
	root.right = temp;
	
	root.left = InvertTree(root.left);
	root.right = InvertTree(root.right);
	
	return root;
}
```
#### Complexity Analysis
* Time Complexity: O(N), N is the length of the list.
* Space Complexity: O(h), h is the height of the tree.

## Approach 2: Iterative
### C#
```C#
public static TreeNode InvertTree(TreeNode root)
{
    if (root == null) return root;
    Queue<TreeNode> queue = new Queue<TreeNode>();
    queue.Enqueue(root);

    while(queue.Count > 0)
    {
        var current = queue.Dequeue();
        var temp = current.left;
        current.left = current.right;
        current.right = temp;
        if (current.left != null)
            queue.Enqueue(current.left);
        if (current.right != null)
            queue.Enqueue(current.right);
    }

    return root;
}
```

### Java
```Java
public TreeNode InvertTree(TreeNode root) {
	if(root == null) return root;
	Queue<TreeNode> queue = new LinkedList<TreeNode>();
	queue.add(root);
	
	while(!queue.isEmpty()) {
		TreeNode current = queue.poll();
		TreeNode temp = current.left;
		current.left = current.right;
		current.right = temp;
		if(current.left != null) 
			queue.add(current.left);
		if(current.right != null)
			queue.add(current.right);
	}
	
	return root;
}
```
#### Complexity Analysis
* Time Complexity: O(N), N is the length of the list.
* Space Complexity: O(N).

[Youtube Video](https://www.youtube.com/watch?v=peHHTFXPOvs)
