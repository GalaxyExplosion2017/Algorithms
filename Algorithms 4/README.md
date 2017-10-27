## 5.3字符串算法

1. ####暴力破解####

   暴力子字符串查找

   ```java
   public static int search(String pat, String txt){
     int M = pat.length();
     int N = txt.length();
     for(int i = 0; i < N; i++){
         int j;
       for(j = 0; j < M; j++){
           if(txt.charAt(i+j)!=pat.charAt(j))
             break;
       }
       if(j == M) return i;
     }
     return N;
   }
   ```

   ​	

2. ####KMP算法

   * 构造DFA数组，**用来保存与txt当前字符匹配成功或失败后的pat当前字符的索引的变化位置 **

     ```java
     dfa[pat.charAt(0)][0] = 1;
     for(int X = 0, j = 1;j < M; j++){
         for(int c = 0; c < R; c++){
             dfa[c][j] = dfa[c][X];
         }
       dfa[pat.charAt(j)][j] = j+1;
       x = dfa[pat.charAt(j)][X];
     }
     ```

   * 子字符串查找算法(DFA模拟)

     ```java
     public int search(String txt){
         int i, j, N = txt.length(), M = pat.length();
       	for(i = 0,j = 0;i < N && j < M; i++){
             j = dfa[txt.charAt(i)][j];
         }
      	if(j == M) return i-M;
       	else return N;
     }
     ```

   * 完整的算法

     ```java
     public class KMP{
         private String pat;
       	private int[][] dfa;
       	public KMP(String pat){
             this.pat = pat;
           	int M = pat.length();
           	int R = 256;
           	dfa = new int[R][M];
           	dfa[pat.charAt(0)][0] = 1;
           	for(int X = 0, j = 1; j < M; j++){
                 for(int c = 0; c < R; c++){
     				dfa[c][j] = dfa[c][X];
                 }
               	dfa[pat.charAt(j)][j] = j+1;
               	X= dfa[pat.charAt(j)][X];
             }
         }
       	public int search(String txt){
             int i, j, N = txt.length(), M = pat.length();
           	for(i = 0; j = 0; i < N && j <M ; i++){
                 j = dfa[pat.charAt(i)][j];
             }
           	if(j == M) return i - N;
           	else return N;
         }
     }
     ```

     ​

3. ####Boyer-Moore算法

   ​	

   ```java
   public class BoyerMoore{
       private int[] right;
     	private String pat;
     	public BoyerMoore(String pat){
           this.pat = pat;
         	int M = pat.length;
         	int R = 256;
         	right = new int[R];
         	for(int c = 0; c < R; c++)
             	right[c] = -1;
         	for(int j = 0; j < M; j++)
             	right[pat.charAt(j)] = j;
       }
     	
     	public int search(String txt){
           int N = pat.length();
         	int M = txt.length();
         	int skip;
         	for(int i = 0; i <= N-M; i+=skip){
               skip = 0;
             	for(int j = M-1; j >= 0; j--){
                   if(pat.charAt(j) != txt.charAt(i+j)){
                     	skip = Math.max(1,j-right[txt.charAt(i+j)]);
                     	//skip = j - right[txt.charAt(i+j)];
                     	//if(skip < 1) 
                         //	skip = 1;
                     	break;
                   }            
               }
              	if(skip == 0) return i;
           }
         return N;
       }
   }
   ```

   ​

   ​