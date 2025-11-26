```matlab
ModifiedEulerMethod[a0_, b0_, n0_, f_, alpha_, actualSolution_] :=
  Module[{a = a0, b = b0, n = n0, h, ti, K1, K2}, h = (b - a)/n;
   ti = Table[a + (j - 1) h, {j, 1, n + 1}];
   wi = Table[0, {n + 1}]; wi[[1]] = alpha;
   actualSol = actualSolution[ti[[1]]];
   difference = Abs[actualSol - wi[[1]]];
   OutputDetails = {{0, ti[[1]], alpha, actualSol, difference}};
   For[i = 1, i <= n, i++,
    K1 = h f[ti[[i]], wi[[i]]];
    K2 = h f[ti[[i]] + h/2, wi[[i]] + K1/2];
    wi[[i + 1]] = wi[[i]] + K2;
    actualSol = actualSolution[ti[[i + 1]]];
    difference = Abs[actualSol - wi[[i + 1]]];
    OutputDetails = 
     Append[OutputDetails, {i, N[ti[[i + 1]]], N[wi[[i + 1]]], 
       N[actualSol], N[difference]}];];
   Print[NumberForm[
     TableForm[OutputDetails, 
      TableHeadings -> {None, {"i", "ti", "wi", "actSol(ti)", 
         "Abs(wi-actSol(ti))"}}], 6]];];
f[t_, x_] := 1 + x/t;
actualSolution[t_] := t (1 + Log[t]);
ModifiedEulerMethod[1, 6, 5, f, 1, actualSolution]
```
