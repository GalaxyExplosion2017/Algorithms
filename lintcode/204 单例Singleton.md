# 204 单例 Singleton

> 恶汉模式，线程安全的

```java
class Solution {
    /**
     * @return: The same instance of this class every time
     */
    public static Solution getInstance() {
        // write your code here
        return solution;
    }
    private static Solution solution = new Solution();
};
```

> 懒汉模式，方法同步之后线程才安全

```java
class Solution {
    /**
     * @return: The same instance of this class every time
     */
    public static synchronized Solution getInstance() {
        // write your code here
        if(solution==null)
            solution =  new Solution();
        return solution;
    }
    private static Solution solution = null;
};
```

