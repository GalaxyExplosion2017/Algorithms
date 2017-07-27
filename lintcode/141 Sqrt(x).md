## [141 Sqrt(x)](http://www.lintcode.com/en/problem/sqrtx/)

**Description**

Implement int `sqrt(int x)`.

Compute and return the square root of *x*.

**Example**

sqrt(3) = 1

sqrt(4) = 2

sqrt(5) = 2

sqrt(10) = 3

**解题思路**

牛顿迭代法：$X=Xi-f(Xi)/f'(Xi)=(Xi+n/Xi)/2$ 

当$r^2$ > x时，不停的迭代，使$r->x$ 直到 $r^2 <=x$ ，返回(int)r

```javascript
class Solution {
    /**
     * @param x: An integer
     * @return: The sqrt of x
     */
    public int sqrt(int x) {
        // write your code here
        long r = x;
        while(r*r > x)
            r = (r+x/r)/2;
        return (int)r;
    }
}
```

