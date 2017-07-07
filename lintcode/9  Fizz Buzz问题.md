# 9  [Fizz Buzz](http://www.lintcode.com/en/problem/fizz-buzz/#)问题

### Description:

Given number *n*. Print number from 1 to *n*. But:

- when number is divided by `3`, print `"fizz"`.
- when number is divided by `5`, print `"buzz"`.
- when number is divided by both `3` and `5`, print `"fizz buzz"`.

**Example:**

If *n* = `15`, you should return:

```
[
  "1", "2", "fizz",
  "4", "buzz", "fizz",
  "7", "8", "fizz",
  "buzz", "11", "fizz",
  "13", "14", "fizz buzz"
]
```

**Solution：**

```java
class Solution {
    /**
     * param n: As description.
     * return: A list of strings.
     */
    public ArrayList<String> fizzBuzz(int n) {
       ArrayList<String> list = new ArrayList<String>();
       for(int i=1;i<=n;i++)
       {
            if(i%15==0)
                list.add("fizz buzz");
            else if(i%3==0)
                list.add("fizz");
            else if(i%5==0)
                list.add("buzz");
            else
                list.add(String.valueOf(i));
       }
       return list;
    }  
}
```

