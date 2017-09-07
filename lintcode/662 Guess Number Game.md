## [662 Guess Number Game](http://www.lintcode.com/en/problem/#)

##### Description

We are playing the Guess Game. The game is as follows:

I pick a number from **1** to **n**. You have to guess which number I picked.

Every time you guess wrong, I'll tell you whether the number is higher or lower.

You call a pre-defined API `guess(int num)` which returns 3 possible results (-1, 1, or 0):

#####Example

n = 10, I pick 4 (but you don't know)

Return 4. Correct !

##### Solution

二分查找

```java
/* The guess API is defined in the parent class GuessGame.
   @param num, your guess
   @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
      int guess(int num); */

public class Solution extends GuessGame {
    /**
     * @param n an integer
     * @return the number you guess
     */
    public int guessNumber(int n) {
        // Write your code here
        int i = 1;
        int j = n;
        while(i <= j){
            int mid = i+(j-i)/2;
            if(guess(mid) == 0){
                return mid;
            }else if(guess(mid) == 1){
                i = mid +1;
            }else{
                j = mid -1;
            }
        }
        return -1;
    }
}
```

