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


#### TO CHECK IF THE TREE IS BST OR NOT

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

    public static boolean validateBST(Node root, Integer min, Integer max) {
        if (root == null) {
            return true;
        }

        if ((min != null && root.data <= min) || (max != null && root.data >= max)) {
            return false;
        }

        return validateBST(root.left, min, root.data) &&
               validateBST(root.right, root.data, max);
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

        if (validateBST(root, null, null)) {
            System.out.println("The given tree is a valid BST.");
        } else {
            System.out.println("The given tree is NOT a valid BST.");
        }

    }
}
````

### OUTPUT
```JAVA
Enter number of elements: 7
Enter elements:
5
2
8
4
6
7
9
The given tree is a valid BST.
````

### TO CHECK IF TWO TREES ARE IDENTICAL TO EACH OTHER

````JAVA
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
        if (root == null) return new Node(data);
        if (data < root.data)
            root.left = insert(root.left, data);
        else
            root.right = insert(root.right, data);
        return root;
    }

    public static boolean areIdentical(Node root1, Node root2) {
        if (root1 == null && root2 == null)
            return true; 
        if (root1 == null || root2 == null)
            return false; 

        return (root1.data == root2.data) &&
               areIdentical(root1.left, root2.left) &&
               areIdentical(root1.right, root2.right);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements in Tree 1: ");
        int n1 = sc.nextInt();
        Node root1 = null;
        System.out.println("Enter elements for Tree 1:");
        for (int i = 0; i < n1; i++) {
            root1 = insert(root1, sc.nextInt());
        }

        System.out.print("Enter number of elements in Tree 2: ");
        int n2 = sc.nextInt();
        Node root2 = null;
        System.out.println("Enter elements for Tree 2:");
        for (int i = 0; i < n2; i++) {
            root2 = insert(root2, sc.nextInt());
        }

        if (areIdentical(root1, root2))
            System.out.println("Both trees are IDENTICAL.");
        else
            System.out.println(" Trees are NOT identical.");

    }
}
````

### OUTPUT
````JAVA
Enter number of elements in Tree 1: 3
Enter elements for Tree 1:
1
2
3
Enter number of elements in Tree 2: 3
Enter elements for Tree 2:
1
2
3
Both trees are IDENTICAL.
````


### TO MIRROR A TREE 

````JAVA
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
        if (root == null) return new Node(data);
        if (data < root.data)
            root.left = insert(root.left, data);
        else
            root.right = insert(root.right, data);
        return root;
    }

    public static void mirror(Node root) {
    	if(root==null) {
    		return;
    	}
    	Node temp=root.left;
    	root.left=root.right;
    	root.right=temp;
    	
    	mirror(root.left);
    	mirror(root.right);
    }


    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements in Tree 1: ");
        int n1 = sc.nextInt();
        Node root = null;
        System.out.println("Enter elements:");
        for (int i = 0; i < n1; i++) {
            root = insert(root, sc.nextInt());
        }

          System.out.println("The mirror of the given tree is" + mirror(root));
      
    }
}
````

### OUTPUT
