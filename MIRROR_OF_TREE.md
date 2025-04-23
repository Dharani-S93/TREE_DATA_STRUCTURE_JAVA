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


    public static boolean mirrorTree(Node r1, Node r2){
        if(r1==null && r2==null){
            return true;
        }
        if(r1==null || r2==null){
            return false;
        }
        return ((r1.data==r2.data)&& mirrorTree(r1.left,r2.right)&&
                  mirrorTree(r1.right,r2.left));
    }
    
    
   public static void main(String[] args) {
    // Manually creating Tree 1
    Node root1 = new Node(5);
    root1.left = new Node(3);
    root1.right = new Node(7);
    
    

    // Manually creating Tree 2 (mirror of Tree 1)
    Node root2 = new Node(5);
    root2.left = new Node(7);
    root2.right = new Node(3);

    boolean result = mirrorTree(root1, root2);
    System.out.println("The trees are mirrors of each other: " + result);
}

}

````

### OUTPUT

````JAVA
The trees are mirrors of each other: true
````
