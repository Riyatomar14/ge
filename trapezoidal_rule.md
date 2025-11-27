```matlab
a = Input["Enter the left end point"];
b = Input["Enter the right end point"];
n = Input["Enter the number of sub intervals to be formed"];
h = (b - a)/n;
y = Table[a + i*h, {i, 0, n}];
f[x_] := Sin[x];
sum = 0;
For[i = 2, i <= n, i++,
  sum = sum + 2*f[y[[i]]];
];
Tn = (h/2)*( f[a] + sum + f[b] );
Tn = N[Tn];
Print["For n=", n, ",Trapezoidal estimate is:", Tn];
in = N[Integrate[Sin[x], {x, a, b}]];
Print["True value is ", in];
Print["Absolute error is ", N[Abs[Tn - in]]];
```

```matlab
a = Input["Enter the left end point"];
b = Input["Enter the right end point"];
n = Input["Enter the number of sub intervals to be formed"];
h = (b - a)/n;
y = Table[a + i*h, {i, 1, n}];
f[x] := Sin[x];
sumodd = 0;
sumeven = 0;
For[i = 1, i < n, i += 2, sumodd += 2*f[x] /. x -> y[[i]]];
For[i = 2, i < n, i += 2, sumodd += 2*f[x] /. x -> y[[i]]];
Tn = (h/2)*((f[x] /. x -> a) + N[sumodd] + 
     N[sumeven] + (f[x] /. x -> b));
Print["For n=", n, ",Trapezoidal estimate is:", Tn]
in = Integrate[Sin[x], {x, 0, Pi/2}];
Print["True value is ", in]
Print["Absolute error is", Abs[Tn - in]]
```
