---
layout: page
title: Overview
nav_order: 4
---
# Overview 
A typical BlockSp code structure to solve $Ax = b$ is
```
int n;           //Vector length/matrix size 
int constexpr B; //solArray blocksize, defined at compile time
int constexpr D; //solArray dimension, defined at compile time
BlockSp::BlockSp<double, B*D> A(n);    //Block sparse matrix A
    //Assemble A 
BlockSp::solArray<double, B, D> b(n);  //Right-hand-side b
    //Assemble b
auto x { BlockSp::ez::sor_pGMRES(A, B) }; //solve Ax = b
```


Here is a brief overview of the key files, containers, and functions
  of the BlockSp library:
<pre>
blocksp_containers.hpp
    BlockSp   --  A block sparse matrix in condensed row storage (CSR) format. 
    solArray  --  A multi-dimensioned block vector. 
The file also includes the dot product, infinity norm, and two norm of solArrays. 

</pre>  
    
    The containers use the following template parameters, specified at compile time: 
        Data type T  --  float, double, std::complex<float>, and std::complex<double>. 
	    int       B  --  block size of the solArray.	
	    int       D  --  dimension of the solArray. D = 1 is the default. 
	Note: the block size of a BlockSp matrix it typically B or B*D.		
	Setting B = D = 1 reduces the problem to regular sparse linear algebra. 
	Testing indicates that the code often runs fastest when B = 2 and D = 1, use when applicable.		     
<pre>

blocksp_multiply.hpp
    bsmm        --  Block sparse matrix-matrix multiplication. 
    bsmv        --  Block sparse matrix-vector multiplication. 
    transpose   --  Block sparse matrix transpose.

blocksp_solvers.hpp 
    BlockSp provides the following iterative linear system solvers.
    pCG           --  Preconditioned block conjugate gradient.
    pGMRES        --  Preconditioned block GMRES, with deflated restarting (see blocksp_deflated_restart.hpp).
    arnoldi_eigenvalues  --  Arnoldi eigenvalue solver.
 
blocksp_preconditioners
    The following functions precondition the block linear system for the iterative solvers: 
    Diag          --  Block diagonal preconditioner.
    SOR           --  Successive over-relaxation.
    ILU0          --  Incomplete LU factorization with zero fill.	
    IChol0        --  Incomplete Cholesky factorization with zero fill.
 
Additional files in the library include:
    blocksp_dense_multiply.hpp  --  Dense matrix-matrix and matrix-vector multiplication.
    blocksp_dense_solvers.hpp   --  Dense linear system solvers.
    blocksp_include.hpp         --  All of the include files for running BlockSp.
    blocksp_lapack.hpp          --  Templated access to the Lapack routines used by BlockSp.
    blocksp_utility.hpp         --  Useful utility functions.

    
