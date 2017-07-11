# Algorithms
record some useful algorithms
To realize the traversal of binary tree in preorder, inorder, postorder.

1. recursive
2. stack+iterative
3. morris traversal(only O(1) space complexity, the other two are O(n))
All three methods have time complexity of O(n)

         // Function to traverse binary tree without recursion and without stack
        // Morris Traversal works only when we have write permission
        public void inorderMorrisTraversal(TreeNode root) {
            if (root == null) {
                return;
            }
            TreeNode cur = root;
            TreeNode pre = null;
            while (cur != null) {
                if (cur.left == null) {
                    System.out.println(cur.val);
                    cur = cur.right;
                } else {
                    // Find the inorder predecessor of current
                    pre = cur.left;
                    while (pre.right != null && pre.right != cur) {
                        pre = pre.right;
                    }
                    
                    // Make current as right child of its inorder predecessor
                    if (pre.right == null) {
                        pre.right = cur;
                        cur = cur.left;
                    } else {
                        // Revert the changes made in if part to restore the original tree
                        // i.e., fix the right child of predecessor
                        pre.right = null;
                        System.out.println(cur.val);
                        cur = cur.right;
                    }
                }
            }
       }

Preorder:
        // Function to pre-order traverse binary tree without recursion and without stack
        // Morris Traversal works only when we have write permission
        public void PreorderMorrisTraversal(TreeNode root) {
            if (root == null) {
                return;
            }
            TreeNode cur = root;
            TreeNode pre = null;
            while (cur != null) {
                if (cur.left == null) {
                    System.out.println(cur.val);
                    cur = cur.right;
                } else {
                    // Find the inorder predecessor of current
                    pre = cur.left;
                    while (pre.right != null && pre.right != cur) {
                        pre = pre.right;
                    }
                    
                    // Make current as right child of its inorder predecessor
                    if (pre.right == null) {
                        // The only different line from in-order traversal! Think about it!
                        System.out.println(cur.val);
                        pre.right = cur;
                        cur = cur.left;
                    } else {
                        // Revert the changes made in if part to restore the original tree
                        // i.e., fix the right child of predecessor
                        pre.right = null;
                        cur = cur.right;
                    }
                }
            }
        }
