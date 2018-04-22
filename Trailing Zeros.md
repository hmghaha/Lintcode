# Trailing Zeros
## 描述
- 设计一个算法，计算出n阶乘中尾部零的个数。
## 样例
- `11! = 39916800`，因此应该返回 2。
## 算法
1. 首先想到对n!因式分解，0来源于`2*5`，而2比5多，所以转换成能分解出多少个5。
刚开始是这样做的loop(n->1), 每层循环里计算 n能分解出多少个5，详见代码1。不过
这样会导致运行时间超时。
2. 这题数比较有规律，1，2，3...n中每五个有一个5的倍数共有`n/5`个，此外，25，
125...等有多个5，可以全体除以5得到一个子问题1，2，3...n/5,再以同样的方法处理

## 代码
1. 
```
public class Solution {
      /*
     * @param n: An integer
     * @return: An integer, denote the number of trailing zeros in n!
     */
    public long trailingZeros(long n) {
        // write your code here, try to do it without arithmetic operators.
        long num = 0;
        while(n!=0){
            num +=zeros(n);
            n--;
        }
        return num;
    }   
    long zeros(long n){
       int count = 0;
       while(n % 5 == 0){
           n /=5;
           count++;
       }
       return count;
    }
} 
```

2. 
```
public class Solution {
      /*
     * @param n: An integer
     * @return: An integer, denote the number of trailing zeros in n!
     */
    public long trailingZeros(long n) {
        // write your code here, try to do it without arithmetic operators.
        long num = 0;
        while(n/5 !=0){
            num +=n/5;
            n /=5;
        }
        return num;
    }
 
}
```

