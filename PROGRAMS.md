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
        if (root == null) {
            return;
        }
        Node temp = root.left;
        root.left = root.right;
        root.right = temp;

        mirror(root.left);
        mirror(root.right);
    }

    public static void inorder(Node root) {
        if (root == null) return;
        inorder(root.left);
        System.out.print(root.data + " ");
        inorder(root.right);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements in Tree: ");
        int n1 = sc.nextInt();
        Node root = null;
        System.out.println("Enter elements:");
        for (int i = 0; i < n1; i++) {
            root = insert(root, sc.nextInt());
        }

        mirror(root);

        System.out.println("In-order traversal of the mirrored tree:");
        inorder(root);
    }
}

````


### OUTPUT

````java
Enter number of elements in Tree: 3
Enter elements:
1
2
3
In-order traversal of the mirrored tree:
3 2 1
````


### TO FIND THE DIAMETER OF THE TREE

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

    static class Diameter {
        int value = 0;
    }

    public static Node insert(Node root, int data) {
        if (root == null) return new Node(data);
        if (data < root.data)
            root.left = insert(root.left, data);
        else
            root.right = insert(root.right, data);
        return root;
    }

    public static int height(Node root, Diameter d) {
        if (root == null) {
            return 0;
        }
        int lh = height(root.left, d);
        int rh = height(root.right, d);

        int path = lh + rh;
        d.value = Math.max(d.value, path); 
        return 1 + Math.max(lh, rh);
    }

    public static int findDiameter(Node root) {
        Diameter d = new Diameter();
        height(root, d);
        return d.value;
    }


    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements in Tree: ");
        int n1 = sc.nextInt();
        Node root = null;
        System.out.println("Enter elements:");
        for (int i = 0; i < n1; i++) {
            root = insert(root, sc.nextInt());
        }

        int diameter = findDiameter(root);
        System.out.println("Diameter of the tree: " + diameter);

    }
}
````

### OUTPUT

````JAVA
Enter number of elements in Tree: 3
Enter elements:
1
2
3
Diameter of the tree: 2
````

### TO FIND THE LCM AND GCD OF THE TREE

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

    public static int gcd(int a, int b) {
        if (b == 0) return a;
        return gcd(b, a % b);
    }

    public static int lcm(int a, int b) {
        return (a * b) / gcd(a, b);
    }

    public static void lg(Node root) {
        if (root == null) return;

        if (root.left != null && root.right != null) {
            int a = root.left.data;
            int b = root.right.data;

            System.out.println("Siblings: " + a + " & " + b);
            System.out.println("  GCD of siblings: " + gcd(a, b));
            System.out.println("  LCM of siblings: " + lcm(a, b));
        }

        lg(root.left);
        lg(root.right);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements in Tree: ");
        int n1 = sc.nextInt();
        Node root = null;
        System.out.println("Enter elements:");
        for (int i = 0; i < n1; i++) {
            root = insert(root, sc.nextInt());
        }

        System.out.println("\nGCD and LCM of all sibling nodes:");
        lg(root);
    }
}
````

### OUTPUT

````JAVA

Enter number of elements in Tree: 5
Enter elements:
1
6
3
7
3

GCD and LCM of all sibling nodes:
Siblings: 3 & 7
  GCD of siblings: 1
  LCM of siblings: 21
````

###  TO FIND THE DISTANCE OF TWO NODES OF THE TREE
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

    public static Node findLCA(Node root, int n1, int n2) {
        if (root == null) return null;

        if (root.data > n1 && root.data > n2)
            return findLCA(root.left, n1, n2);
        else if (root.data < n1 && root.data < n2)
            return findLCA(root.right, n1, n2);
        else
            return root;
    }

    public static int findDistance(Node root, int target) {
        if (root == null) return -1;

        if (root.data == target)
            return 0;
        else if (target < root.data)
            return 1 + findDistance(root.left, target);
        else
            return 1 + findDistance(root.right, target);
    }

    public static int distanceBetweenNodes(Node root, int n1, int n2) {
        Node lca = findLCA(root, n1, n2);

        int d1 = findDistance(lca, n1);
        int d2 = findDistance(lca, n2);

        return d1 + d2;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of elements in Tree: ");
        int n = sc.nextInt();

        Node root = null;
        System.out.println("Enter elements:");
        for (int i = 0; i < n; i++) {
            root = insert(root, sc.nextInt());
        }

        System.out.print("Enter first node: ");
        int node1 = sc.nextInt();

        System.out.print("Enter second node: ");
        int node2 = sc.nextInt();

        int dist = distanceBetweenNodes(root, node1, node2);
        System.out.println("Distance between " + node1 + " and " + node2 + " is: " + dist);
    }
}
````

### OUTPUT

````JAVA
Enter number of elements in Tree: 5
Enter elements:
2
5
7
4
8
Enter first node: 2
Enter second node: 8
Distance between 2 and 8 is: 3
````

### ZIGZAG TREE TRAVERSAL

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

    public static int height(Node root) {
        if (root == null) return 0;
        int lh = height(root.left);
        int rh = height(root.right);
        return 1 + Math.max(lh, rh);
    }

    public static void printlevel(Node root, int level, boolean leftToRight) {
        if (root == null) return;

        if (level == 1) {
            System.out.print(root.data + " ");
        } else if (level > 1) {
            if (leftToRight) {
                printlevel(root.left, level - 1, leftToRight);
                printlevel(root.right, level - 1, leftToRight);
            } else {
                printlevel(root.right, level - 1, leftToRight);
                printlevel(root.left, level - 1, leftToRight);
            }
        }
    }

    public static void zigzag(Node root) {
        int h = height(root);
        boolean leftToRight = true;

        for (int i = 1; i <= h; i++) {
            printlevel(root, i, leftToRight);
            leftToRight = !leftToRight; 
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Node root = null;

        System.out.print("Enter number of nodes: ");
        int n = sc.nextInt();

        System.out.println("Enter node values:");
        for (int i = 0; i < n; i++) {
            int val = sc.nextInt();
            root = insert(root, val);
        }

        System.out.println("Zigzag Traversal:");
        zigzag(root);
    }
}
````


### OUTPUT
````
Enter number of nodes: 7
Enter node values:
50
30
70
20
40
80
60
Zigzag Traversal:
50 70 30 20 40 60 80
````

###  TO FIND THE MAXIMUM ELEMENT IN A PATH TO TARGET

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

    public static int maxEle(Node root, int target, int max) {
        if (root == null) return -1;

        if (root.data == target)
            return Math.max(max, root.data);

        max = Math.max(max, root.data);

        if (target < root.data)
            return maxEle(root.left, target, max);
        else
            return maxEle(root.right, target, max);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        Node root = null;
        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();
        System.out.println("Enter elements:");
        for (int i = 0; i < n; i++) {
            root = insert(root, sc.nextInt());
        }

        System.out.print("Enter target node: ");
        int target = sc.nextInt();

        int res = maxEle(root, target, Integer.MIN_VALUE);

        if (res == -1)
            System.out.println("Target not found in tree.");
        else
            System.out.println("Maximum element in path to " + target + " is: " + res);
    }
}
````

### OUTPUT

````JAVA
Enter number of elements: 5
Enter elements:
1
3
7
4
9
Enter target node: 4
Maximum element in path to 4 is: 7
````

### TO CONVERT ARRAY TO TREE

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
    public static Node arraytotree(int[] arr, int start, int end) {
        if (start > end) return null;

        int mid = (start + end) / 2;
        Node root = new Node(arr[mid]);

        root.left = arraytotree(arr, start, mid - 1);
        root.right = arraytotree(arr, mid + 1, end);

        return root;
    }

    public static void inorder(Node root) {
        if (root == null) return;
        inorder(root.left);
        System.out.print(root.data + " ");
        inorder(root.right);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter size of array: ");
        int n = sc.nextInt();
        int[] arr = new int[n];

        System.out.println("Enter array elements:");
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        Node root = arraytotree(arr, 0, n - 1);

        System.out.println("Inorder traversal:");
        inorder(root);
    }
}
````

### OUTPUT

````JAVA
Enter size of array: 5
Enter array elements:
1
3
6
7
8
Inorder traversal:
1 3 6 7 8

````


### MEDIAN OF BST

````JAVA

package dharuuu;

import java.util.ArrayList;
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

    public static void inorder(Node root, ArrayList<Integer> l) {
        if (root != null) {
            inorder(root.left, l);
            l.add(root.data);
            inorder(root.right, l);
        }
    }

    public static int median(Node root) {
        ArrayList<Integer> res = new ArrayList<>();
        inorder(root, res);
        int n = res.size();

        if (n % 2 != 0) {
            return res.get(n / 2);
        } else {
            return (int) ((res.get(n / 2 - 1) + res.get(n / 2)) / 2.0);
        }
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

        int med = median(root);
        System.out.println("Median of BST: " + med);
    }
}
````

## OUTPUT
````JAVA
Enter number of elements: 7
Enter elements: 
12
4
76
5
88
45
3
Median of BST: 12
````




