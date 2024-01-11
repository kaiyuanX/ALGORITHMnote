- [KMP](#kmp)
  - [LSP](#lsp)
      - [快速得到 lsp](#快速得到-lsp)
  - [代码](#代码)
  - [复杂度](#复杂度)

**参考**

- [如何更好地理解和掌握 KMP 算法 - 阮行止](https://www.zhihu.com/question/21923021/answer/1032665486) 
- [字符串匹配的 KMP 算法 - 阮一峰](https://www.ruanyifeng.com/blog/2013/05/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm.html)

---

# KMP

基本思路见这里 : [阮一峰的网络日志](https://www.ruanyifeng.com/blog/2013/05/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm.html)

## LSP

约定从左到右 , 在 `sstr` 中找 `pat`

`lsp[]` : longest proper prefix

eg: S="abcab"

```
lsp[0] = 0 , always 
lsp[1] = 0 
lsp[3] = 1 
lsp[4] = 2 
```

匹配在 `pat[i] == sstr[j]` 处失败，应该跳转到 `pat[lsp[i - 1]]` 继续与 `sstr[j]` 匹配

#### 快速得到 lsp

从 `lsp[x-1]` 到 `lsp[x]`

```c
temp = lsp[x-1]

if pat[x] = pat[lsp[x-1]]   // 1.
    lsp[x] = lsp[x-1] + 1

if pat[x] != pat[temp]
    temp = lps[temp - 1];

if temp = 0                 // 2. 
    lsp[x] = 0

直到 1. 或者 2. 成立
```

[如何更好地理解和掌握 KMP 算法 - 阮行止](https://www.zhihu.com/question/21923021/answer/1032665486) 文章中的图解解释得已经很好
## 代码

```python
def search():
tar =0      # tar:主串中将要匹配的位置
pos = 0     # poS:模式串中将要匹配的位置
while tar < len(s):
    if s[tar] =p[pos]:  # 若两个字符相等，则 tar, pos 各进一步
        tar += 1
        pos += 1
    elif pos:           # 失配了，若 pos != 0，则依据 next 数组移动标尺
        pos = lps[pos-1]
    else:
        tar += 1        # pos[0]失配了，直接把标尺右移一位

    if poslen(p):       # pos 走到了 len(p)，匹配成功
        print(tar - pos)    # 记录一次结果
        pos = lps[pos-1]    # 移动标尺
```

## 复杂度

设 $N$ 为目标 , $M$ 为模式 , 分别长 $n$ 与 $m$

1. 摊还分析，搜索 : $O(n)$
2. 摊还分析，不难证明构建 `lsp[]` 的时间复杂度 : $O(m)$

一共 $O(m+n)$ ( 平均 )

==解释==

`1. `

$j$ 的回溯只会影响搜索主循环次数的上下界 $[n, 2n]$

每个字符**平均**回溯 $2$ 次

在这种情况下，对于 $n$ 中的每个字符，实际上都比较了 $2$ 次，所以一共执行了 $2n$ 次循环

这已经是循环次数的上限 $O(n)$

`2. `

快速求 `next[]` 思路

```c
if (pat[i] != pat[len])
{
    if (len != 0)
    {
        len = lps[len - 1];
    }
    else
    {
        lps[i] = 0;
        i++;
    }
}
```

len 的回溯也没有影响时间复杂度 $O(m)$