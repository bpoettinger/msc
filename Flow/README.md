## Flow

## Session

### Dependencies

- [Isabelle 2020](https://isabelle.in.tum.de/)
- [AFP](https://www.isa-afp.org/) (tested 2020-08-15)

### Usage

Explore/work on session:

```text
isabelle -d <path-to-flow> jedit
```

Check/build session:

```text
isabelle -d <path-to-flow> build Flow
```

### Project Structure

We annotate the theory names with the definitions and lemmas from [1] that are contained in there.
The ordering of theories in this enumeration provides a reasonable order to examine the project.

Preliminary development is contained in theories
- `Auxiliary`: arbitrary/common/auxiliary lemmas on lists/sets/functions
- `Alternating`: alternating list predicates
- `Endomorphism`[def. 9,10,12]: formalization of endomorphisms
- `Chain`[def. 13, lem. 9]: a special kind of function concatenation induced by lists on binary functions
- `Pigeonhole`: the generalized pigeonhole principle and some auxiliary lemmas for the simple pigeonhole principle

The basic abstractions, flow graphs and flow interfaces are defined in theories
- `Flow_Graph`[def. 3,4, lem. 1]
- `Flow_Interface`[def. 5,6]

Their relationship is formalized in theory (for further development,
do not use `Flow_Graph` or `Flow_Interface` directly, use this one)
- `Flow_Base`[lem. 2,3]

Theoretical results on flow graphs and flow interfaces are provided in
- `Flow_Footprint`[def. 7, lem. 4]: a node is in footprint of some operation iff. it is changed
- `Flow_Graph_Separation_Algebra`: valid flow graphs form a separation algebra
- `Flow_Interface_Separation_Algebra`[th. 1]: valid flow interfaces form a separation algebra

Two notions of extensions of flow graphs are provided in:
- `Flow_Extension`[def. 8,13, th. 2]

Approximations of flow terms are developed in:
- `Approximations`[lem. 6]

The development on nilpotent flow graphs is provided in:
- `Nilpotent`[lem. 7]

The development on effectively acyclic flow graphs is provided in:
- `Effectively_Acyclic`[def. 11]: general definitions regarding effective acyclicity
- `Effectively_Acyclic_Approximations`: extends `Approximations` in context of effective acyclicity
- `Effectively_Acyclic_Switch_Worlds`: auxiliary result for `Effectively_Acyclic_Maintain`
- `Effectively_Acyclic_Sourced_Path`: auxiliary result for `Effectively_Acyclic_Maintain`
- `Effectively_Acyclic_Equal_Capacity`: auxiliary result for `Effectively_Acyclic_Maintain`
- `Effectively_Acyclic_Uniqueness`[lem. 8]: proves uniqueness of flows of effectively acyclic flow graphs
- `Effectively_Acyclic_Maintain`[fixed th. 3]: proves existence of flow of effectively acyclic flow graphs
- `Effectively_Acyclic_Maintain_Counter_Example`: provides counter example for [th. 3] from [1]

The PIP example is split into:
- `Pip_Shared`: shared development for acquire and release cases
- `Pip_Acquire`: proof of acquire operation
- `Pip_Release`: proof of release operation
- `Pip_Example`: small example demonstrating the application of the PIP operations

All development is summarized in `Flow.thy`.

## References

* [1] Siddharth Krishna, Alexander J. Summers, and Thomas Wies: Local Reasoning for Global Graph Properties, ESOP 2020, [https://cs.nyu.edu/~siddharth/](https://cs.nyu.edu/~siddharth/)
* [2] Siddharth Krishna: Compositional Abstractions for Verifying Concurrent Data Structures, [https://cs.nyu.edu/~siddharth/](https://cs.nyu.edu/~siddharth/)