
https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/

#### Optmized Code

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */

class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        
        //true->right to left, false->left to right
        boolean leftToRight = true;

        List<List<Integer>> result = new ArrayList<>();

        if(root==null)
            return result;

        Queue<TreeNode> queue = new LinkedList<>();

        queue.add(root);

        while(!queue.isEmpty()){

            int size = queue.size();
            List<Integer> levelResult = new LinkedList<>();
            
            for(int i=0;i<size;i++) {

                TreeNode tmp = queue.poll();

                if(leftToRight){
                    levelResult.add(tmp.val);
                } else {
                    levelResult.add(0, tmp.val);
                }
                
                if(tmp.left!=null){
                    queue.add(tmp.left);
                }
                if(tmp.right!=null){
                    queue.add(tmp.right);
                }
            }
            result.add(levelResult);
            leftToRight = !leftToRight;
        }

        return result;
    }
}
```

---



```java

//User function Template for Java

/*class Node
{
    int data;
    Node left,right;
    Node(int d)
    {
        data=d;
        left=right=null;
    }
}*/

class GFG
{
    //Function to store the zig zag order traversal of tree in a list.
	ArrayList<Integer> zigZagTraversal(Node root)
	{
	    //Add your code here.
	    int level=1;
	    LinkedList<Node> queue=new LinkedList<Node>();
	    ArrayList<Integer> result=new ArrayList<Integer>();
	    
	    
	    queue.add(root);
	    int count=1;
	    Node data;
	    while(queue.size()>0)
	    {
	        int tmp=0;
	        
	        if(level%2==0)
	        {
	            //pick values from rear of linkedlist
	            for(int i=1;i<=count;i++)
	            {
	                data=queue.poll();
	                result.add(data.data);
	                if(data.right!=null)
	                {
	                    queue.add(data.right);
	                    tmp+=1;
	                }
	                if(data.left!=null)
	                {
	                    queue.add(data.left);
	                    tmp+=1;
	                }
	                
	            }
	            
	        }
	        else{
	            
	            //pick values from front of linkedlist
	            for(int i=1;i<=count;i++)
	            {
	                data=queue.pollLast();
	                result.add(data.data);
	                if(data.left!=null)
	                {
	                    queue.addFirst(data.left);
	                    tmp+=1;
	                }
	                if(data.right!=null)
	                {
	                    queue.addFirst(data.right);
	                    tmp+=1;
	                }
	   
	            }
	            
	        }
	        count = tmp;
	        level+=1;
	    }
	    return result;
	}
}
```
