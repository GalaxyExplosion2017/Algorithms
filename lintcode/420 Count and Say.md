## [420 Count and Say](http://www.lintcode.com/en/problem/count-and-say/)

##### Description

The count-and-say sequence is the sequence of integers beginning as follows:

`1, 11, 21, 1211, 111221, ...`

`1` is read off as `"one 1"` or `11`.

`11` is read off as `"two 1s"` or `21`.

`21` is read off as `"one 2, then one 1"` or `1211`.

Given an integer `n`, generate the `n`th sequence.

#####  Notice

The sequence of integers will be represented as a string.

**Example**

Given n = `5`, return `"111221"`.

##### Solution

初始化一个stringBuilder类型的对象curr，值为1，定义一个同类型的对象prev，定义计数变量count初始为1和当前数字索引say，当n大于1时，将curr赋给prev，然后将第一个数赋给say，从第二个数开始，与前面的数不相同时，将前面数的计数count和当前数say追加到curr中，若等于say则count+1，遍历完当前数字则将count和say追加到curr中，只到遍历完n。

```java
public class Solution {
    /**
     * @param n the nth
     * @return the nth sequence
     */
    public String countAndSay(int n) {
        // Write your code here
        StringBuilder curr=new StringBuilder("1");
	    	StringBuilder prev;
	    	int count;
	    	char say;
	        for (int i=1;i<n;i++){
	        	prev=curr;
	 	        curr=new StringBuilder();       
	 	        count=1;
	 	        say=prev.charAt(0);
	 	        
	 	        for (int j=1,len=prev.length();j<len;j++){
	 	        	if (prev.charAt(j)!=say){
	 	        		curr.append(count).append(say);
	 	        		count=1;
	 	        		say=prev.charAt(j);
	 	        	}
	 	        	else count++;
	 	        }
	 	        curr.append(count).append(say);
	        }	       	        
	        return curr.toString();
    }
}
```

