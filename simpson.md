```matlab
SimpsonOneThird[f_, a_, b_, n_] := Module[{h, result},
  
  If[OddQ[n], Return["n must be even"]];
  
  h = (b - a)/n;
  result = (h/3) * (f[a] + 4 f[a + h] + f[b]);
  
  result
]

f[x_] := 1/(1 + x);
SimpsonOneThird[f, 0, 1, 2]
```
```matlab
SimpsonOneThird[f_, a_, b_, n_] := Module[{h, x, sum1 = 0, sum2 = 0},
  
  If[OddQ[n], Return["n must be even"]];
  
  h = (b - a)/n;
  
  sum1 = Sum[f[a + i h], {i, 1, n - 1, 2}];
  sum2 = Sum[f[a + i h], {i, 2, n - 2, 2}];
  
  (h/3) * (f[a] + 4 sum1 + 2 sum2 + f[b])
]

f[x_] := 1/(1 + x);
SimpsonOneThird[f, 0, 1, 3]
```
