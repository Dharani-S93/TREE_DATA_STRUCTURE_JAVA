### TREE IMPLEMENTATION IN JAVA
```
# 1) Inserting Elements in the tree
# 2) Searching an element
# 3) Deleting the element
# 4) Traversal(Inorder, Preorder, Postorder

```

### CODE

````JAVA
package dharuu;

import java.util.Scanner;

public class Main {

    static class Node {
        int data;
        Node left, right;

        Node(int data) {
            this.data = data;
            left = right = null;
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

    public static Node search(Node root, int data) {
        Node temp = root;
        while (temp != null) {
            if (temp.data == data) {
                System.out.println("Found: " + temp.data);
                return temp;
            }
            if (data < temp.data) {
                temp = temp.left;
            } else {
                temp = temp.right;
            }
        }
        System.out.println("Not Found");
        return null;
    }

    public static Node delete(Node root, int key) {
        if (root == null) {
            return null;
        }

        if (key < root.data) {
            root.left = delete(root.left, key);
        } else if (key > root.data) {
            root.right = delete(root.right, key);
        } else {
            if (root.left == null) {
                return root.right;
            } else if (root.right == null) {
                return root.left;
            }

            Node successor = findMin(root.right);
            root.data = successor.data;
            root.right = delete(root.right, successor.data);
        }

        return root;
    }

    public static Node findMin(Node root) {
        while (root.left != null) {
            root = root.left;
        }
        return root;
    }

    public static void inorder(Node root) {
        if (root != null) {
            inorder(root.left);
            System.out.print(root.data + " ");
            inorder(root.right);
        }
    }
    
    public static void preorder(Node root) {
        if (root != null) {
            System.out.print(root.data + " ");
            preorder(root.left);
            preorder(root.right);
        }
    }
    
    public static void postorder(Node root) {
        if (root != null) {
            postorder(root.left);
            postorder(root.right);
            System.out.print(root.data + " ");
        }
    }
    

    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);

        Node root = null;

        System.out.print("Enter number of elements to insert: ");
        int n = s.nextInt();
        System.out.println("Enter elements: ");
        for (int i = 0; i < n; i++) {
            int val = s.nextInt();
            root = insert(root, val);
        }

        System.out.println("Inorder traversal of BST:");
        inorder(root);
        System.out.println();

        System.out.print("Enter element to search: ");
        int key = s.nextInt();
        search(root, key);

        System.out.print("Enter element to delete: ");
        int del = s.nextInt();
        root = delete(root, del);

        System.out.println("Inorder traversal after deletion:");
        inorder(root);
        System.out.println();
        
        System.out.println("Preorder traversal after deletion:");
        preorder(root);
        System.out.println();
        
        System.out.println("Postorder traversal after deletion:");
        postorder(root);
        System.out.println();
    }
}

````

### OUTPUT

````JAVA
Enter number of elements to insert: 7
Enter elements: 
2
6
4
8
7
3
11
Inorder traversal of BST:
2 3 4 6 7 8 11 
Enter element to search: 4
Found: 4
Enter element to delete: 4
Inorder traversal after deletion:
2 3 6 7 8 11 
Preorder traversal after deletion:
2 6 3 8 7 11 
Postorder traversal after deletion:
3 7 11 8 6 2 
````
