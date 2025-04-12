### TREE DATA STRUCTURE

### TO FIND THE MAXIMUM ELEMENT IN TREE

````java

package dharuu;

import java.util.Scanner;

public class Main {

    static class Node {
        int data;
        Node left, right;

        Node(int data) {
            this.data = data;
            this.left = this.right = null;
        }
    }
    public static Node insert(Node root, int data) {
        if (root == null) {
            return new Node(data);
        }
        if (data < root.data) {
            root.left = insert(root.left, data);
        } else {
            root.right = insert(root.right, data);
        }
        return root;
    }
    public static int Max(Node root) {
        if (root == null) {
            return -1; 
        }
        Node node = root;
        while (node.right != null) {
            node = node.right;
        }
        return node.data;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();
        Node root = null;
        System.out.println("Enter elements:");
        for (int i = 0; i < n; i++) {
            int data = sc.nextInt();
            root = insert(root, data);
        }
        System.out.println("Maximum value in BST: " + Max(root));
    }
}

````

### OUTPUT

````java
Enter number of elements: 5
Enter elements:
2
4
8
5
10
Maximum value in BST: 10
````
