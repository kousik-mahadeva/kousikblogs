+++
title = 'LLMs, Transpilers, and the Accidental Power of Functional Programming'
date = 2026-01-02T23:39:39+05:30
draft = false
disableMenu = true
+++

Serendipitously, I got into [this](https://juspay.io/blog/revolutionizing-code-intelligence-how-autotranspiler-ensures-flawless-code-conversion) blog from juspay. It was a time when it was running back-of-my-mind about building the testing system. The blog spoke about transpiling with an automatic verification system using LLM. I was hooked on the automatic verification system. I thought that would solve a puzzle in the testing system

**Literatures :**   
\[Must-Read\] Juspay transpiler (haskell to rust) : [link](https://juspay.io/blog/revolutionizing-code-intelligence-how-autotranspiler-ensures-flawless-code-conversion)  
\[Must-Read\] Amazon transpiler (go to rust) : [link](https://assets.amazon.science/0e/ab/c10459dd4013a7c02f09b8c96f3f/scalable-validated-code-translation-of-entire-projects-using-large-language-models.pdf)  
Google migration : [link](https://arxiv.org/pdf/2504.09691)  
LLM transpiler (Functional Programing DSL to other DSLs) : [link](https://arxiv.org/pdf/2406.03003)  
LLM transpiler (java to python) : [link](https://arxiv.org/pdf/2410.24117)  
And a few more…(I missed marking them\!)

**Observations :**   
Couple of things was clear from all their experiences,

* Context windows were small for any decent enterprise repository.  
* They solved the problem by chopping down (few worked at page-level, few worked at function level)  
* Majority of them used a parser. They used ‘tree-sitter’ and LSP (just learned about them both\!). Tree-sitter gives them AST and LSP gives them context about who calls function, where the variable is used,etc  
* No paper claimed they got it all right (as in,100% accuracy)  
* Challenges were mainly for Imperative language like java  
* Java has global variables. Java has side-effects.   
* Java also has huge spring-boot framework that contained lot of context/states

Overall, I got the notion that it is really hard to implement these for complex languages like java, which nearly require the whole codebase to gain context. 

But surprisingly, Functional Programming guys were able to leverage these LLM techniques. Their main advantage is that you segregate code into pure and side-effects (the language itself is designed in such a way\!).   
Since pure functions had no dependency anywhere else, context to the LLM is only the pure function\! This was leveraged in Juspay where Transpiling was happening for each function (ie, each function was given as context to LLM and asked to do all the manipulations).

While lot of larger languages are multi-paradigm. I feel flexibility might creep-in contextual bugs. Thus, only-functional language makes more sense to me.

This should convince you to jump into functional programming.


