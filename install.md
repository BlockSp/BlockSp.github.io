---
layout: page
title: Installation
nav_order: 3
---

You can download BlockSp via
    
    git clone https://github.com/BlockSp/BlockSp.git
    
or download the <a href="BlockSp-v1.0.zip">.zip</a>. Visit BlockSp on <a href="https://github.com/BlockSp/BlockSp">GitHub</a>.

BlockSp is a header only C++ library with two external library dependencies.
Place the library folder where your compiler can find it.
Then include it in your code via #include "blocksp_include.hpp".

Additional dependencies:
To run BlockSp, you must first include and link the following libraries:  <br>
<a href="https:www.intel.com/content/www/us/en/developer/tools/oneapi/onemkl-download.html">MKL</a> – Intel’s Math Kernel Library, used for the dense/block linear algebra. <br>
<a href="https:github.com/blitzpp/blitz">blitz++</a> – A high-performance matrix, vector, and multi-dimensional array library. 


A CMakeLists.txt file is provided. Additionally, instructions for setting up BlockSp within the 
<a href= "https://visualstudio.microsoft.com/">Visual Studio</a> IDE are located within the INSTALL file.


