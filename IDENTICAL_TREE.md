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


    public static boolean identicalTree(Node r1, Node r2){
        if(r1==null && r2==null){
            return true;
        }
        if(r1==null || r2==null){
            return false;
        }
        return ((r1.data==r2.data)&& identicalTree(r1.left,r2.left)&&
                  identicalTree(r1.right,r2.right));
    }
    
    
    
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        Node root1 = null;
        Node root2 = null;
        

        System.out.print("Enter number of elements: ");
        int n = s.nextInt();
        System.out.println("Enter elements: ");
        for (int i = 0; i < n; i++) {
            int val = s.nextInt();
            root1 = insert(root1, val);
        }
        System.out.print("Enter number of elements: ");
        int n1 = s.nextInt();
        System.out.println("Enter elements: ");
        for (int i = 0; i < n1; i++) {
            int val = s.nextInt();
            root2 = insert(root2, val);
        }
        

        boolean result = identicalTree(root1, root2);
        System.out.println("The tree is identical: " + result);
        
        
    }
}

````

### OUTPUT
````JAVA
Enter number of elements: 2
Enter elements: 
1
2
Enter number of elements: 2
Enter elements: 
1
3
The tree is identical: false

````
