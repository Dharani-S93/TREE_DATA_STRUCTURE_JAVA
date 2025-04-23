
## CODE

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

    public static int maxOfTree(Node root){
        if(root==null){
            return 0;
        }
        
        int res=root.data;
        int left=maxOfTree(root.left);
        int right=maxOfTree(root.right);
        
        if(left> res){
            res=left;
        }
        if(right> res){
            res=right;
        }
        //return 1+ Math.max(left,right);
        return res;
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

        int result = maxOfTree(root);
        System.out.println("The Maximum is: " + result);
    }
}

````

### OUTPUT
````JAVA

Enter number of elements: 5
Enter elements: 
2
5
6
3
4444   
The Maximum is: 6

````
