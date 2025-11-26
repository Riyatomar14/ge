```matlab
EulerMethod[a0_, b0_, n0_, f_, alpha_] := 
  Module[{a = a0, b = b0, n = n0, h, ti}, h = (b - a)/n;
   ti = Table[a + (j - 1) h, {j, 1, n + 1}];
   ui = Table[0, {n + 1}];
   ui[[1]] = alpha;
   OutputDetails = {{0, ti[[1]], alpha}};
   For[i = 1, i <= n, i++, 
    ui[[i + 1]] = ui[[i]] + h*f[ti[[i]], ui[[i]]];
    OutputDetails = 
     Append[OutputDetails, {i, N[ti[[i + 1]]], N[ui[[i + 1]]]}];];
   Print[NumberForm[
     TableForm[OutputDetails, 
      TableHeadings -> {None, {"i", "ti", "ui"}}], 6]];
   Print["Subinterval size h used= ", h];];
f[t_, w_] := 1 + w/t;
a = 1;
b = 6;
n = 10;
alpha = 1;
EulerMethod[a, b, 10, f, alpha];
```
```matlab
EulerMethodwithH[a0_, b0_, h0_, f_, alpha_] :=
  Module[{a = a0, b = b0, h = h0, n, ti},
   n = (b - a)/h;
   ti = Table[a + (j - 1) h, {j, 1, n + 1}];
   ui = Table[0, {n + 1}];
   ui[[1]] = alpha;
   OutputDetails = {{0, ti[[1]], alpha}};
   For[i = 1, i <= n, i++,
    ui[[i + 1]] = ui[[i]] + h*f[ti[[i]], ui[[i]]];
    OutputDetails = Append[OutputDetails,
      {i, N[ti[[i + 1]]], N[ui[[i + 1]]]}];];
   Print[NumberForm[
     TableForm[OutputDetails, 
      TableHeadings -> {None, {"i", "ti", "ui"}}], 6]];
   Print["Subinterval size h used= ", h];];
g[t_, w_] := 1 + w/t;
a = 1;
b = 6;
h = .2;
alpha = 1;
EulerMethodwithH[a, b, h, g, alpha];
```
