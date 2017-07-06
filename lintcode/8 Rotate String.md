#  8 Rotate String

### Description:

> Given a string and an offset, rotate string by offset. (rotate from left to right)

### Example:

> Given `"abcdefg"`.
>
> offset=0 => `"abcdefg"`
>
> offset=1 => `"gabcdef"`
>
> offset=2 =>` "fgabcde"`
>
> offset=3 =>` "efgabcd"`

#### 解题思路：

> 先将偏移位之前的元素逆置，再将偏移位元素逆置，最后将所有元素逆置

```java
public class Solution {
    /**
     * @param str: an array of char
     * @param offset: an integer
     * @return: nothing
     */
    public void rotateString(char[] str, int offset) {
        // write your code here
        if(str==null||str.length==0) return ;
        offset%=str.length;
        reverse(str,0,str.length-offset-1);
        reverse(str,str.length-offset,str.length-1);
        reverse(str,0,str.length-1);
        
    }
    public void reverse(char[] str,int start,int end)
    {
        for(int i=start,j=end;i<j;i++,j--)
        {
            char temp = str[i];
            str[i] = str[j];
            str[j] = temp;          
        }
    }
}
```

