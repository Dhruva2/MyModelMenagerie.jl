# MyModelMenagerie

This is just a store for a couple of input-output differential equation models I can test stuff on.

## How to use:

1. Make an input function 
```   
t -> input(t)
```
2. In julia, call 
```
 od, ic, tspan, ps = ModelName(input)
  ```

So eg 
```
od, ic, tspan, ps = NFKBModel(sin)
od, ic, tspan, ps = CircadianOscillator(t -> 0.)
```

Now you can use the DifferentialEquations.jl ecosystem to solve the equation. e.g.

```
using OrdinaryDiffEq
prob = ODEProblem(od,ic,tspan,ps)
sol = solve(prob, Tsit5())
```

Of course, you can alter the parameter values and initial conditions, accessed as 
```
vals = last.(ps)
vals[1] += 1
ps = first.(ps) .=> vals
```
(same for initial conditions)

## Notes

Most of the models here are buit using ModelingToolkit.jl.

