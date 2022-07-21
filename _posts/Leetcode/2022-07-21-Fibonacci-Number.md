---
title: Leetcode 509. Fibonacci Number
categories: ["Leetcode"]
---

<https://leetcode.cn/problems/fibonacci-number/>

### Question

写一个函数，输入 n ，求斐波那契（Fibonacci）数列的第 n 项（即 F(N)）。斐波那契数列的定义如下：

```
F(0) = 0, F(1) = 1
F(n) = F(n - 1) + F(n - 2), for n > 1.
```

斐波那契数列由 0 和 1 开始，之后的斐波那契数就是由之前的两数相加而得出。

答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。

0 <= n <= 100

### Answer 1 dynamic programming

```go
func fib(n int) int {
    if n < 2 {
        return n
    }
    const mod int = 1e9+7
    x, y, z := 0, 1, 1
    for i := 2; i < n; i++ {
        x = y
        y = z
        z = x + y
        if z > mod {
            z %= mod
        }
    }
    return z
}
```

Time:  O(n)
Space: O(1)

### Answer 2 fast matrix exponentiation

```go
const mod int = 1e9+7

func fib(n int) int {
    if n < 2 {
        return n
    }
    ans := [][]int{{1}, {0}}
    a := [][]int{{1, 1}, {1, 0}}
    n -= 1
    for ; n > 0; n >>= 1 {
        if n & 1 == 1 {
            ans = multiply(a, ans)
        }
        a = multiply(a, a)
    }
    return ans[0][0]
}

func multiply(a, b [][]int) (res [][]int) {
    r, z, c := len(a), len(a[0]), len(b[0])
    res = make([][]int, r)
    for i := 0; i < r; i++ {
        res[i] = make([]int, c)
    }
    for i := 0; i < r; i++ {
        for j := 0; j < c; j++ {
            for k := 0; k < z; k++ {
                res[i][j] += (a[i][k] * b[k][j])
                if res[i][j] > mod {
                    res[i][j] %= mod
                }
            }
        }
    }
    return res
}
```

Time:  O(log n)
Space: O(1)