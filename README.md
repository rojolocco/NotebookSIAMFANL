# Solving Nonlinear Equations with Iterative Methods: <br> Solvers and Examples in Julia

# Notebook version 0.2.1

# This is the dev branch for v0.2.1. Use v0.2.1 with this version of the notebook.

## [C. T. Kelley](https://ctk.math.ncsu.edu)

## Contents

- [Quick start guide](#If-you-know-what-to-do): Fast starting for those who have done this before.

- [Mission](#What-is-this-thing): What is this thing and why do you care?

- [Getting Started](#Getting-Started): Things you need to do before anything works.

- [How much Julia do you need to know?](#Julia-Prerequisites): You need to know something about Julia. You do not need to be an expert.

- [The Algorithms](#The-Algorithms): Pointers to the literature for theory

- [Other Nonlinear Solvers in Julia](#Other-Nonlinear-Solvers-in-Julia): Three other packages with very different missions.

- [Notebook Problems?](#Notebook-Problems) What? You're having trouble starting the notebook?

- [Support](#Support): Thanks!

## If you know what to do
- Install the package with **Pkg.add("https://github.com/ctkelley/SIAMFANLEquations.jl")**
- Clone this repository. Put the directory in your Julia load path.
- Fire up an IJulia notebook and open SIAMFANL.ipynb.
- Follow the directions in the preface and the "How to get the software" sections.


## What is this thing?

These are the notebooks that come with the print book and the solvers. The solver
package is independent of the books, but you would be well advised to 
play with the notebooks. The purpose of all of these things is to enable
the reader to learn about algorithms for nonlinear solvers. Please read the preface in 
the first notebook (Part1) for a more detailed mission statement.

The book is a sequal to my 2003 book in SIAM Fundamentals of Algorithms (FA) series.

(Kel03) [***Solving Nonlinear Equations with Newton's Method***](https://my.siam.org/Store/Product/viewproduct/?ProductId=841) , Fundamentals of Algorithms 1, SIAM 2003


The provisional title is

**Solving Nonlinear Equations with Iterative Methods: Solvers and Examples in Julia**

Hence the repositories have SIAMFANL in their names.

## Getting started

If you are reading this you have found the notebooks. The optimal way to use this is
to clone this repository and put it in your Julia **LOAD_PATH**. Then install the packages with the solvers using **pkg**.

One way to do that is to type

**import Pkg; Pkg.add("https://github.com/ctkelley/SIAMFANLEquations.jl")**

in the REPL.

The next step is to open the notebooks. An efficient way to do this (after installing IJulia) is to type **using IJulia** and  **notebook()** in the REPL. Then navigate to the directory where the notebooks are and click on SIAMFANL.ipynb.

In the first code window in each of the notebooks you will find

**using SIAMFANLEquations**<br>
**using SIAMFANLEquations.TestProblems**


To get everything to work, you will need a few packages. LinearAlgebra, SuiteSparse, SparseArrays, AbstractFFTs, FFTW, IJjulia, JLD2, and PyPlot. I put 

```Julia
using LinearAlgebra
using SuiteSparse
using SparseArrays
using AbstractFFTs
using FFTW
using IJulia
using JLD
```

in my startup.jl file and do **using PyPlot** when I need it. PyPlot takes a while to get going.

All this is also in the first code window in the notebooks. If Julia complains about a missing package, it is your job to add it.

If you want to play with the solvers, clone the repository for the package and put that in your Julia **LOAD_PATH**.

## Julia Prerequisites

Since this is an education project, I do not expect the reader to be an expert
in Julia, but do expect her/him to be able to understand the codes, 
play with the algorithms, and wreak havoc. To that end I have tuned the 
codes for readability by a Julia novice who knows some numerical analysis. I made the algorithmic parameters very easy to find. As part of this I have sacrificed a lot of abstraction, some generality, and a bit of performance.

The reader should know Julia well enough to use the package manager, install packages, use modules, and to do basic tasks in 
numerical methods (LU, SVD, QR) in Julia. You should also know how to use github to clone repositories (like this one) and put them where they need to go.

## The algorithms.

My two books on nonlinear equations

(Kel95) [***Iterative Methods for Linear and Nonlinear Equations***](https://my.siam.org/Store/Product/viewproduct/?ProductId=862) , Frontiers in Applied Mathematics 16,  SIAM 1995

and

(Kel03) [***Solving Nonlinear Equations with Newton's Method***](https://my.siam.org/Store/Product/viewproduct/?ProductId=841) , Fundamentals of Algorithms 1, SIAM 2003

describe the Newton and Broyden algoirthms. CTK95 has the theory. This project is a sequal to CTK03. CTK03 is Matlab-centric
and will remain in print.

A recent Acta Numerica paper has everything

(Kel18) C. T. Kelley, ***Numerical Methods for Nonlinear Equations***, Acta Numerica 27 (2018), pp 207--287. https://doi.org/10.1017/S0962492917000113

The references I use for theory of pseudo-transient continuation and Anderson acceleration are

(KK98) C. T. Kelley and D. E. Keyes, ***Convergence Analysis of Pseudo-Transient Continuation***, SIAM Journal on Numerical Analysis 35 (1998), pp 508-523. https://doi.org/10.1137/S0036142996304796

(TK15) A. Toth and C. T. Kelley, ***Convergence Analysis for Anderson Acceleration***, SIAM Journal on Numerical Analysis 53, (2015), pp 805-819. https://doi.org/10.1137/130919398

These references have extensive bibliographies as does the print book. The notebooks have smaller bibliographies because a lengthy list of citations is hard to parse and looks ugly in a notebook.

## The examples

The codes for every plot and table in the book are either in the src directory in this repository or in the notebooks. You'll get the chance to run them, change them, and make them better/worse/shinier as you work through the notebooks. 

## Other Nonlinear Solvers in Julia

We have a very different mission from that of the other nonlinear solver
packages in Julia. Three of the most complete packages are NLsolve.jl, Sundials.jl and BifurcationKit.jl.

Solvers like NLsolve.jl

https://github.com/JuliaNLSolvers/NLsolve.jl

are highly abstracted and very general. The Julia ecosystem has many 
codes like this for all kinds of things. They are very useful but hard to learn from. This seems to be based on Dennis and Schnabel's 1983 book. T

At the high end, KINSOL is part of the Julia port of Sundials

https://github.com/SciML/Sundials.jl

Sundials is a suite of solvers from Lawrence Livermore National 
Laboratory that is designed for scalable performance on high-end
supercomputers. This is a well-done (by the very best people) and important project, but not one designed
for a novice to understand.

The pathfollowing and bifurcation analysis package BifurcationKit.jl

https://github.com/rveltz/BifurcationKit.jl

has speical-purpose nonlinear solvers that communicate well with continuation algorithms. 

## Notebook Problems
 
It is very important that PyPlot and IJulia use the same version of conda. If the notebook is complaining about the kernel, that is likely the issue. You have a good chance of fixing this with the __update__ command within pkg. If you did the update when you installed this application and are still having problems. Try typing __update IJulia__ from pkg. If that fails ...

The worst case, which has happened to me more than once, is that you'll have to 

   1. Move .julia/config to a safe place.
      1. Your startup.jl lives in config. Don't lose it.
        
   2. Delete or move .julia
   
   3. Run Julia (which will create a new .julia in your home directory)
      1. Put your config diectory back in there. 
        
   4. Reinstall ALL YOUR PACKAGES! That is a real pain, but has never failed to fix the problem for me.

## Support

This project was partially supported by
1. Army Research Office grant W911NF-16-1-0504 and
2. National Science Foundation Grants
   1. OAC-1740309
   2. DMS-1745654
   3. DMS-1906446
   
Any opinions, findings, and conclusions or
recommendations expressed in this material are those of the author and
do not necessarily reflect the views of the National
Science Foundation
or the Army Research Office.
