## PERMUTE-BY-SORTING(A)
```
1  n = A. length
2  let P[l. . n] be a new array
3  for i = 1 to n
4       P[i] = RANDOM(l, n^3)
5  sort A , using P as sort keys
```

## RANDOMIZE-IN-PLACE(A)
```
1  n = A.Length
2  for i = 1 to n
3       swap A[i] with A[RANDOM(i, m)]
```