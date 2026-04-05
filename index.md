---

layout: page
nav-order: 1
---

# BlockSp: A templated C++ library for block sparse linear algebra

Welcome to BlockSp!
A templated C++ library for block sparse linear algebra. Version 1.0.

You can download BlockSp via
    
    git clone https://github.com/BlockSp/BlockSp.git
    
or download the <a href="BlockSp-v1.0.zip">.zip</a>. Visit BlockSp on <a href="https://github.com/BlockSp/BlockSp">GitHub</a>.

This software package is designed to address linear algebra problems
  where the majority of elements within the linear system are zero (sparse)
	and the non-zero entries are dense matrices (blocks).
	Block sparse linear systems can be found in, e.g., high-order 
  finite element methods (FEM) and discontinuous Galerkin methods (DG), 
  as well as a wide range of other problems. Here is an example:

<table style="width: 100%; text-align: center; border: none;">
  <tr>
    <td>
      \[
      \begin{pmatrix}
          3 & 1 & 6 & 5 & 1 & 1 \\
          8 & 4 & 6 & 5 & 4 & 3 \\
          4 & 9 & 5 & 8 & 7 & 6 \\
          3 & 1 & 0 & 5 & 14 & 7 \\
          8 & 4 & 6 & 5 & 4 & 0 \\
          7 & 8 & 2 & 4 & 9 & 9
      \end{pmatrix}
      \]
    </td>
    <td>
      \[
      \begin{pmatrix}
          -2 & 1 & & & &  \\
          1 & -2 & 1 & & & \\
           & 1 & -2 & 1 &  & \\
           &  & 1 & -2 & 1 &  \\
           &  &  & 1 & -2 & 1 \\
           &  &  &  & 1 & -2
      \end{pmatrix}
      \]
    </td>
    <td>
      \[
      \begin{pmatrix}
      \begin{bmatrix}
          1 & 7 \\
          7 & 2
      \end{bmatrix}
      & &
      \begin{bmatrix}
          2 & 1 \\
          2 & 4
      \end{bmatrix}
      \\
       &
      \begin{bmatrix}
          1 & 1 \\
          1 & 1
      \end{bmatrix}
      & 
      \\
      \begin{bmatrix}
          2 & 2 \\
          1 & 4
      \end{bmatrix}
      & &
      \begin{bmatrix}
          6 & 5 \\
          5 & 2
      \end{bmatrix}
      \end{pmatrix}
      \]
    </td>
  </tr>
  <tr>
    <td><em>A dense matrix.</em></td>
    <td><em>A sparse matrix, blank spaces are zero entries.</em></td>
    <td><em>A block sparse matrix, with 2x2 blocks.</em></td>
  </tr>
</table>
 
This header-only C++ library provides support for both multiplying and solving 
	block sparse linear systems ($Ax = b$). The library includes 
  containers for block sparse matrices and multi-dimension block vectors,
  block sparse matrix-matrix (bsmm) and matrix-vector (bsmv) multiplication,
  preconditioned iterative block sparse system solvers
	including conjugate gradient (pCG) and pGMRES, 
  and several preconditioners including block SOR and ILU0.
 
The data type, block size, and dimension are specified at compile-time
  via templating, allowing for fast optimized stack-based operations.
  Through templating, BlockSp handles both real and complex problems.
	BlockSp requires C++20 or later.

You can find a brief overview of BlockSp <a href="/Overview/">here</a>.

 
Additional dependencies:
To run BlockSp, you must first include and link the following libraries: <br>
<a href="https:www.intel.com/content/www/us/en/developer/tools/oneapi/onemkl-download.html">MKL</a> – Intel’s Math Kernel Library, used for the dense/block linear algebra. <br>
<a href="https:github.com/blitzpp/blitz">blitz++</a> – A high-performance matrix, vector, and multi-dimensional array library. 
 

 BlockSp Copyright © 2026, Luke P. Corcos Ph.D. (lpcorcos@gmail.com)