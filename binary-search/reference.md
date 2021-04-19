# Reference

1. Use int mid = left + \(right - left\) / 2 instead of int mid = \(left+right\)/2 to avoid integer overflow.
2. The binary search will finally fall into the below situation: either a\[mid\] &lt; a\[right\] or &gt; a\[right\] but not equal.

![](../.gitbook/assets/image%20%2810%29.png)

3. When comparing nums\[mid\] with a certain target, \(l &lt;= r\). When comparing with nums\[left/right\] \(l &lt; r\).

