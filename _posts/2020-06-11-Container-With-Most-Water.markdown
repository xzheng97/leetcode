---
layout: home
title:  "Container With Most Water"
number: 11
level: "Medium"
topic: "Array, Two Pointers"
workDate: "06/11/20"
permalink: /:title
---
<a  style="color:#ffe57c;float:top" href="{{site.baseurl}}/index.html">Home</a>
<h2>Container With Most Water</h2>

<h3 style="color:#ffe57c;"><a href="https://leetcode.com/problems/container-with-most-water/">Question</a></h3>


<p>TGiven n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.</p>

<p>Note: You may not slant the container and n is at least 2.</p>

<img src="{{site.baseurl}}/images/question_11.jpg" style='width:100%;'>

<h3>Example:</h3>
<pre><code class="plaintext">Input: [1,8,6,2,5,4,8,3,7]
Output: 49
</code></pre>


<h3>Solution:</h3>
<p style="color: #ffc0cb">Note: one at the start and one at the end. One moves closer if it has smaller height as moving the other one will not expand the area since the height is determined by the lower one.</p>
<pre><code class="java"> class Solution {
    public int maxArea(int[] height) {
        int max = 0;
        int area = 0;
        int pt1 = 0;
        int pt2 = height.length-1;
        while (pt1 < pt2) {
            if(height[pt1]< height[pt2]){
                area = height[pt1] * (pt2-pt1);
                pt1++;
            }
            else {
                area = height[pt2] * (pt2-pt1);
                
                pt2--;
            }   
            max = max > area? max: area;
        }
        return max;
    }
}</code></pre>