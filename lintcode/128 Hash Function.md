## [128 Hash Function](http://www.lintcode.com/en/problem/hash-function/)

**Description**

In data structure Hash, hash function is used to convert a string(or any other type) into an integer smaller than hash size and bigger or equal to zero. The objective of designing a hash function is to "hash" the key as unreasonable as possible. A good hash function can avoid collision as less as possible. A widely used hash function algorithm is using a magic number 33, consider any string as a 33 based big integer like follow:

hashcode("abcd") = (ascii(a) * 333 + ascii(b) * 332 + ascii(c) *33 + ascii(d)) % HASH_SIZE 

​                              = (97* 333 + 98 * 332 + 99 * 33 +100) % HASH_SIZE

​                              = 3595978 % HASH_SIZE

here HASH_SIZE is the capacity of the hash table (you can assume a hash table is like an array with index 0 ~ HASH_SIZE-1).

Given a string as a key and the size of hash table, return the hash value of this key.f

**Clarification**

For this problem, you are not necessary to design your own hash algorithm or consider any collision issue, you just need to implement the algorithm as described.

**Example**

For key="abcd" and size=100, return 78

**解题思路**

> 实现hash算法

```java
class Solution {
    /**
     * @param key: A String you should hash
     * @param HASH_SIZE: An integer
     * @return an integer
     */
    public int hashCode(char[] key,int HASH_SIZE) {
        // write your code here
        long result = 0;
        for(int i = 0; i < key.length; i++)
            result = (result*33 + key[i]) % HASH_SIZE;
        return (int)result;
    }
};
```

