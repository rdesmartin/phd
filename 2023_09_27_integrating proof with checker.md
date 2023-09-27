At the moment, we have basically two different code bases for verifying certificates of unsatisfiability  (e.g. they use different data structures and data types): (a) the Imandra proof for Farkas lemmas; (b) the proof checker implementation, that comprises additional checks on top of certificate checking.
For instance, the system of linear constraints in (a) is represented as a list of constraints with a single type `expr` for equality and inequality constraints: 
```ocaml
(* A polynomial is a list of coefficients, one for each variable
X_1, ..., X_n as well as a final constant term.
So, e.g., `3X_1 + 4X_3 + 1` is represented as
[3.0; 0.0; 4.0; 1.0].
*)
type poly = Real.t list

(* An expression is a constraint of the form `Eq p` or `Geq p`,
with `p` a polynomial, interpreted as `p = 0` or `p >= 0`
(resp.). *)

type expr =
| Eq of poly (* = 0 *)
| Geq of poly (* >= 0 *)
```

Whereas in (b), the equality constraints and the inequality constraints (i.e. the bounds of each variables) are kept in two separate lists, which gives us a quicker access to corresponding elements for instance in the function `check_contradiction`:

```ocaml
let check_contradiction (contradiction: real list) (tableau: real list list) (upper_bounds: real list) (real list): bool =
let linear_combination = LinArith.compute_combination contradiction tableau in
LinArith.compute_row_upper_bound linear_combination upper_bounds lower_bounds <. 0.
```


Now we want to use the proof in (a) to prove that the implementation (b) is correct. The possible ways of doing that are:
* changing the checker to use only (a) implementation: 
	* pro: 100% correspondence between proof and implementation; 
	* con: all the checker would have to be re-implemented, probably loss of performance
* convert the (b)-style data to (a)-style data and use the (a)-implementation of certificate checking in the overall proof checker: 
	* pros: we don't have to re-implement the whole checker
	* con: loss of performance because we essentially maintain 2 different copies of the same data, not elegant
* prove equivalence of (a) to (b) to prove the correctness of (b): 
	* pros: no need to re-implement anything
	* con: ?

At the moment the last option seems the best