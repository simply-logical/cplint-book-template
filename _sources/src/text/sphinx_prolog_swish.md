(sec:sphinxprolog:swish)=
# Diabetes Mellitus #

:::{note}
This page is based on the [*Diabetes Mellitus* cplint example].
Launch the {ref}`final code block <swish:cplint6>` on this page to execute
the entire programme.
:::

From
 - Steffen Michels, Arjen Hommersom, Peter J. F. Lucas, Marina Velikova:
   A new probabilistic constraint logic programming language based on a
   generalised distribution semantics. Artif. Intell. 228: 1-44 (2015)

We want to compute the probability of insurgence of diabetes mellitus type 2
given the level of glycated hemoglobin (HbA1c).

Various genetic factors play a role on the onset of type 2 diabetes:

```{swish} swish:cplint1
---
---
:- use_module(library(mcintyre)).

:- if(current_predicate(use_rendering/1)).
:- use_rendering(c3).
:- use_rendering(graphviz).
:- endif.

:- mc.
:- begin_lpad.

predisposition(average):0.698;predisposition(moderate):0.227;predisposition(high):0.075.
```

Type2 diabetes has different probability of insurgence given the
predisposition:

```{swish} swish:cplint2
---
inherit-id: swish:cplint1
---
dm:0.054:-
  predisposition(average).
dm:0.131:-
  predisposition(moderate).
dm:0.266:-
  predisposition(high).
```

The level of glucose is represented by two normal distributions:

```{swish} swish:cplint3
---
inherit-id: swish:cplint1 swish:cplint2
---
gluc_if_dm(G):gaussian(G,7.5,3.8).
gluc_if_not_dm(G):gaussian(G,5.79,0.98).
```

The level of HbAc1 depends linearly from the level of glucose plus some noise:

```{swish} swish:cplint4
---
inherit-id: swish:cplint1 swish:cplint2 swish:cplint3
---
noise_if_dm(N):gaussian(N,0.0,3.3).
noise_if_not_dm(N):gaussian(N,0.0,0.3).

hba1c(H):-
    dm,
    gluc_if_dm(G),
    noise_if_dm(N),
    {H=:=1.4+0.92*G+N}.

hba1c(H):-
    \+ dm,
    gluc_if_not_dm(G),
    noise_if_not_dm(N),
    {H=:=0.6+0.9*G+N}.
```

We observe that the level of HbA1c is larger than 7.2:

```{swish} swish:cplint5
---
inherit-id: swish:cplint1 swish:cplint2 swish:cplint3 swish:cplint4
---
e:- hba1c(H),{H>7.2}.
:- end_lpad.
```

We want to compute the probability of diabetes type 2 a priori and given the
evidence:

```{swish} swish:cplint6
---
inherit-id: swish:cplint1 swish:cplint2 swish:cplint3 swish:cplint4 swish:cplint5
---
/** <examples>
?- mc_sample(dm,1000,Prob).
?- mc_mh_sample(dm,e,10000,Prob).
*/
```

[*Diabetes Mellitus* cplint example]: http://cplint.ml.unife.it/example/inference/diabetes.swinb
