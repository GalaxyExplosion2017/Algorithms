## [445 Cosine Similarity](http://www.lintcode.com/en/problem/cosine-similarity/#)

#####  Description

Cosine similarity is a measure of similarity between two vectors of an inner product space that measures the cosine of the angle between them. The cosine of 0° is 1, and it is less than 1 for any other angle.

See wiki: [Cosine Similarity](https://en.wikipedia.org/wiki/Cosine_similarity)

Here is the formula:![cosine-similarity](C:\Users\ZhangJiachen\Desktop\pic\cosine-similarity.png)

Given two vectors A and B with the same size, calculate the cosine similarity.

Return `2.0000` if cosine similarity is invalid (for example A = [0] and B = [0]).

##### Example

Given A = `[1, 2, 3]`, B = `[2, 3 ,4]`.

Return `0.9926`.

Given A = `[0]`, B = `[0]`.

Return `2.0000`

##### Solution

```java
class Solution {
    /**
     * @param A: An integer array.
     * @param B: An integer array.
     * @return: Cosine similarity.
     */
    public double cosineSimilarity(int[] A, int[] B) {
        // write your code here
        if(A.length == 0 || B.length == 0 || A.length != B.length) return 2;
        int aa = 0, bb = 0, ab = 0;
        for(int i = 0; i < A.length; i++){
            aa += A[i]*A[i];
            bb += B[i]*B[i];
            ab += A[i]*B[i];
        }
        if(aa == 0 || bb == 0) return 2;
        return (double)ab/(Math.sqrt(aa)*Math.sqrt(bb));
    }
}
```

