# A + B Problem
## 描述
- 给出两个整数a和b, 求他们的和, 但不能使用 `+`  等数学运算符。
## 算法
- `^` 异或, `A^B`表示不带进位的加法。而`A&B`则指出了产生进位的位置。所以`A^B`与`A&B<<1`之和表示了完整的加法。
## 代码
```
public class Solution {
    /**
     * @param a: An integer
     * @param b: An integer
     * @return: The sum of a and b 
     */
    public int aplusb(int a, int b) {
        // write your code here
        while(b != 0){
            int sum1 = a ^ b;
            b = (a & b) << 1;
            a = sum1;
        }
        return a;
    }
}
```
## 总结
- 这里求`A`与`B`之和与求`A^B`与`A&B<<1`之和是一样的方法明确这一点才能确定循环体。