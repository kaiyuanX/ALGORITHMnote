# Miller–Rabin 素性测试
Miller-Rabin 素性测试同样是不确定算法

我们把可以通过以 a 为底的 Miller-Rabin 测试的合数称作以 a 为底的强伪素数 ( strong pseudoprime )

## 原理
1. 如果 $p$ 是素数，$a$ 是小于 $p$ 的正整数，那么 $a^{p-1}\ mod\ p = 1$( 费马小定理 ) ( 逆定理不成立，但大致正确 )
2. 如果 $p$ 是素数，$x$ 是小于 $p$ 的正整数，且 $x^2\ mod\ p = 1$，那么要么 $x=1$ ，要么 $x=p-1$

( 两条定理的证明见参考 )

## 步骤
前面说过 $341$ 可以通过以 $2$ 为底的 Fermat 测试，因为 $2^340\ mod\ 341=1$

如果 $341$ 真是素数的话，那么 $2^{170}\ mod\ 341$ 只可能是 $1$ 或 $340$ 

$\big( a^b \ mod\ p=((a\ mod\ p)^b)\ mod\ p \big)$

当算得 $2^{170}\ mod\ 341$ 确实等于 $1$ 时，我们可以继续查看 $2^{85}$ 除以 $341$ 的结果

$2^{85}\ mod\ 341=32$ 这一结果摘掉了 $341$ 上的素数皇冠

[reference](http://www.matrix67.com/blog/archives/234)

## 代码
参考 `DSAA`

见 `Randomized/MR primality test.c`

与 `步骤` 有些不一样

`步骤` 是 N 先通过 Fermat 测试再依次降幂进行性质 2 的验证

而 `代码` 是在升幂的过程中验证性质 2 直到得到 Fermat 所需的幂次最后进行 Fermat 验证