# Reference

1. Use int mid = left + \(right - left\) / 2 instead of int mid = \(left+right\)/2 to avoid integer overflow.
2. The binary search will finally fall into the below situation: either a\[mid\] &lt; a\[right\] or &gt; a\[right\] but not equal.

![](../.gitbook/assets/image%20%2811%29.png)

3. When using while\(l &lt; r\), we can't go to the right when right is the correct ans in the above situation, therefore we should use right = mid instead of mid-1 to get the right close interval. When using \(l &lt;=r \), we can set right = mid - 1.

![](../.gitbook/assets/image%20%287%29.png)



