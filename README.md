# GroupSlices.jl

[![Build Status](https://travis-ci.org/mcabbott/GroupSlices.jl.svg?branch=master)](https://travis-ci.org/mcabbott/GroupSlices.jl)

The function `groupslices` is related to `unique`, but instead of returning the unique elements, 
it returns a list of indices showing where an equivalent entry first appeared. Like this:

```julia
(v1.2) pkg> add GroupSlices

julia> using GroupSlices

julia> V = rand('α':'γ', 5)
5-element Array{Char,1}:
 'β'
 'β'
 'γ'
 'α'
 'β'

julia> groupslices(V)
5-element Array{Int64,1}:
 1
 1
 3
 4
 1

julia> unique(V)
3-element Array{Char,1}:
 'β'
 'γ'
 'α'

julia> M = rand(2:4, 2,13)
2×13 Array{Int64,2}:
 2  2  3  3  3  4  2  2  2  4  3  2  4
 4  4  4  4  4  4  3  4  3  2  3  4  2

julia> groupslices(M, dims=2) |> transpose
1×13 LinearAlgebra.Transpose{Int64,Array{Int64,1}}:
 1  1  3  3  3  6  7  1  7  10  11  1  10

julia> unique(M, dims=2)
2×6 Array{Int64,2}:
 2  3  4  2  4  3
 4  4  4  3  2  3
```

This package was written by [AndyGreenwell](https://github.com/AndyGreenwell/GroupSlices.jl) 
in 2015, originally for Julia PRs [#14142](https://github.com/JuliaLang/julia/pull/14142) and [#15503](https://github.com/JuliaLang/julia/pull/15503).

My fork is now the registered version. It has minimal changes to make it work on Julia 1.0,
and to accept keywords like `dims=2` (although `groupslices(M,2)` will also still work).

See [JuliaLang/julia#1845](https://github.com/JuliaLang/julia/issues/1845) for discussion of possible replacements. 
