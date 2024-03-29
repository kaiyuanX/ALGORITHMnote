参考

- [matrix67](http://www.matrix67.com/blog/archives/234)
- [DSAA]()

# Miller–Rabin 素性测试

Miller-Rabin 素性测试是不确定算法

“可以通过以 a 为底的 Miller-Rabin 测试的合数” 称作 “以 a 为底的强伪素数” 

( Strong Pseudoprime )

## 原理
1. 如果 $p$ 是素数，$a$ 是小于 $p$ 的正整数，那么 $a^{p-1}\ mod\ p = 1$
   - 费马小定理
   - 逆定理不成立，但大致正确
2. 如果 $p$ 是素数，$x$ 是小于 $p$ 的正整数，且 $x^2\ mod\ p = 1$，那么要么 $x=1$ ，要么 $x=p-1$

( 两条定理的证明见参考 )

两条性质应该是相互独立，在检验性质一时同时检验性质二，提高成功率

## 步骤
前面说过 $341$ 可以通过以 $2$ 为底的 Fermat 测试，因为 $2^{340}\ mod\ 341=1$

如果 $341$ 真是素数的话，那么 $2^{170}\ mod\ 341$ 只可能是 $1$ 或 $340$ 

$\big( a^b \ mod\ p=((a\ mod\ p)^b)\ mod\ p \big)$

当算得 $2^{170}\ mod\ 341$ 确实等于 $1$ 时，我们可以继续查看 $2^{85}$ 除以 $341$ 的结果

$2^{85}\ mod\ 341=32$ 这一结果摘掉了 $341$ 上的素数皇冠

## 代码

“步骤” 中的例子是 p 先通过 `性质1` 的 Fermat 测试再依次降幂进行 `性质 2` 的验证

“代码” 逻辑是在升幂的过程中验证 `性质 2` 直到得到 Fermat 所需的幂次后进行 Fermat 验证

- Start from $2^{0}\ mod\ 341$
- to $2^{1}\ mod\ 341$
- to $(2^{1}\ mod\ 341)^2 mod\ 341$
- ...
- 遇到上一层为奇数幂会额外 $result = (2*result)\  mod\  341$
- to $2^{42} mod\ 341$
- to $result = 2^{84} mod\ 341$，$result = (2*result)\ mod\ 341$
- to $2^{170} mod\ 341$
- to $2^{340} mod\ 341$
- 进行 Fermat 测试


见 `ADAT/MR primality test.c`