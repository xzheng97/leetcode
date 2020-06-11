---
layout: home
title:  "House Robber III"
number: 337
level: "Medium"
topic: "Tree, DFS"
workDate: "06/10/20"
permalink: /leetcode/:title
---
<a  style="color:#ffe57c;float:top" href="/index.html">Home</a>
<h2>House Robber III</h2>

<h3 style="color:#ffe57c;"><a href="https://leetcode.com/problems/house-robber-iii/">Question</a></h3>


<p>The thief has found himself a new place for his thievery again. There is only one entrance to this area, called the "root." Besides the root, each house has one and only one parent house. After a tour, the smart thief realized that "all houses in this place forms a binary tree". It will automatically contact the police if two directly-linked houses were broken into on the same night.</p>

<p>Determine the maximum amount of money the thief can rob tonight without alerting the police.</p>


<h3>Example 1:</h3>
<pre><code class="plaintext">Input: [3,2,3,null,3,null,1]

     3
    / \
   2   3
    \   \ 
     3   1

Output: 7 
Explanation: Maximum amount of money the thief can rob = 3 + 3 + 1 = 7.
</code></pre>

<h3>Example 2:</h3>
<pre><code class="plaintext">Input: [3,4,5,1,3,null,1]

     3
    / \
   4   5
  / \   \ 
 1   3   1

Output: 9
Explanation: Maximum amount of money the thief can rob = 4 + 5 = 9.
</code></pre>


<h3>Solution:</h3>
<pre><code class="java">class Solution {
    private HashMap<TreeNode, Integer> skip;
    private HashMap<TreeNode, Integer> take;
    public int rob(TreeNode root) {
        if(root == null) return 0;
        skip = new HashMap<>();
        take = new HashMap<>();
        
        help(root);
        
        return Math.max(skip.get(root), take.get(root));
    }
    
    private void help(TreeNode root) {
        if(root == null) return;
        help(root.left);
        help(root.right);
        
        int curSkip = 0, curTake = 0;
        if(root.left != null) {
            curSkip = Math.max(skip.get(root.left), take.get(root.left));
            curTake = skip.get(root.left);
        }
        
        if(root.right != null) {
            curSkip += Math.max(skip.get(root.right), take.get(root.right));
            curTake += skip.get(root.right);
        }
        
        skip.put(root, curSkip);
        take.put(root, curTake + root.val);
    }
}</code></pre>