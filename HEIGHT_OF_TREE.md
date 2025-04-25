
### CODE 

````JAVA

import java.util.*;
public class Main
{
    static class Node {
        int data;
        Node left, right;

        Node(int data) {
            this.data = data;
            left = right = null;
        }
    }

    public static Node insert(Node root, int data) {
        if (root == null) return new Node(data);
        if (data < root.data) root.left = insert(root.left, data);
        else if (data > root.data) root.right = insert(root.right, data);
        return root;
    }

    public static int heightofTree(Node root){
        if(root==null){
            return 0;
        }
        
        int left=heightofTree(root.left);
        int right=heightofTree(root.right);
        
    
      return Math.max(left,right)+1;
        
    }
    
    

    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        Node root = null;

        System.out.print("Enter number of elements: ");
        int n = s.nextInt();
        System.out.println("Enter elements: ");
        for (int i = 0; i < n; i++) {
            int val = s.nextInt();
            root = insert(root, val);
        }

        int result = heightofTree(root);
        System.out.println("The Height of the tree is: " + result);
    }
}


````

### OUTPUT

````JAVA
Enter number of elements: 5
Enter elements: 
2
4
7
6
5
The Height of the tree is: 5

````
