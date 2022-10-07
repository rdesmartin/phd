* The overall contribution of the paper is not clear. It appears the authors are focussed
on their verification system, Imandra, and trying to understand its use in DNN verification.
`RD: the reviewer describes the general context, what we're doing specifically in this paper is in the context of using Imandra for DNN verification, how does the choice of matrix implementation influence the verification possibility`

* The conclusions appear vague - "Imandra's language is sufficiently flexible to give
rise to several versions of the NN library depending on the choice of matrix implementation, and its automated proof heuristics usually adapt rather smoothly".
`RD: reformulate: Imandra's language is sufficiently flexible to give rise to implementatoins of each possible choice of matrix in the CheckINN library. Imandra's proof heuristics adapt smoothly to these different implementations, with very little hints needed to figure out the appropriate proof strategy (induction, SAT/SMT proving or Boyer-Moore waterfall).`

* It is not clear if the observation about modeling matrices as lists or functions and its impact on
proofs by induction or SAT/SMT is limited to Imandra or would carry over to other theorem
proving engines such as PVS.
`RD: I don't know about PVS but we do mention a similar scalability problem in Starchild/Lazuli (which I believe use SMTLib2 as SMT solver)`

* Further, the presented approach appears to fail to even
the class DNN examples such as ACAS Xu. Some of the early DNN verification papers such
as Dutta et. al. Output range analysis for deep feedforward neural networks. NFM'18,
used a simpler set of artificial benchmarks and those might be worth trying out. It
may be also useful to look at https://sites.google.com/view/vnn2021
`RD: As for PPDP, this comment focuses on scalability, which is not our main focus.`
