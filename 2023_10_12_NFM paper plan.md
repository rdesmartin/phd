# Introduction

Why do we need a verified proof checker?

* DNNs are complex and vulnerable to adversarial perturbations, so we need DNN verifiers.
* DNN verifiers are complex and can have errors, so we need a way to check their results
	* Errors ex. include implementation bugs, numerical instability
	* Examples motivation: tool disagreement in VNN-comp 
	* Trust/performance balance: these tools are too complex (partly because of optimisations for performance) to formally verify them directly
* Proof checker are common practice in SMT solving; they are smaller, simpler pieces of software compared to full DNNV
* Possible to use verification-oriented, less optimised PLs like functional PLs with integration to automated verification/ITPs.
# Background
* DNNs / DNN verification
* Proof production for DNN verification
* Imandra
* Related works:
	* Proof production for SMT/DNN verification
	* Proof of Farkas lemma in other TP
	* Integration of DNN verification in ITPs, ex DNN in Coq

# Proof checking in Imandra
## Proof Checker Architecture and Specification
* Explain the general proof-checking algorithm
* present its implementation in Imandra and design choices
* Show the 2 parts that we want to formally verify:
	* contradiction checking 
	* bound lemmas checking
## Proof of Correctness: Generalised Farkas Lemma
* Mathematical proof that follows the Imandra proof's structure, e.g. make inductions explicit and give details
* Link to the Imandra code (hyperlinks to annex?)
* Give size of proof and of checker in terms of number of lines
# Discussion
* Evaluation on ACAS Xu?
* We trust some parts of the proof checker
* Numerical instability: compared to the original model, there is some discrepancy
* Example of integration of DNN verifier with verification of a larger system (ex: vehicle controller)