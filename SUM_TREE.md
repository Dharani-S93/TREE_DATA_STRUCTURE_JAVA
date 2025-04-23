````java
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


    public static int sumTree(Node root){
        if(root==null){
            return 0;
        }
        if(root.left==null && root.right==null){
            return root.data;
        }
        int left=sumTree(root.left);
        int right=sumTree(root.right);
        
        return left +right+root.data;
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

        int result = sumTree(root);
        System.out.println("The sum tree is: " + result);
        
        
    }
}

````
