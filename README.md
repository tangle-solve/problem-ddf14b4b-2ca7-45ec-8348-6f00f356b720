<!-- solve-problem:ddf14b4b-2ca7-45ec-8348-6f00f356b720 -->
# Near-quadratic complexity of 3D line Voronoi diagrams

A [Tangle Solve problem](https://solve.tangle.tools/problems/ddf14b4b-2ca7-45ec-8348-6f00f356b720).

## What is the problem?

Given a set **L** of *n* lines in ℝ³ (in general position), consider the Euclidean Voronoi diagram VD(**L**): the decomposition of ℝ³ into cells, where the cell of line ℓᵢ is the set of points closer to ℓᵢ than to any other ℓⱼ under Euclidean point-to-line distance. The **complexity** of the diagram is the total number of faces of all dimensions (equivalently, of vertices, or of 2-faces — all within constant factors).

The problem: determine whether the combinatorial complexity of VD of *n* lines in ℝ³ is **O(n^{2+ε}) for every fixed ε > 0**, or exhibit a construction with **ω(n²)** complexity.

Standard reductions: VD of lines corresponds (via a lifting/sphere interpretation) to the **lower envelope of n "cones"** — distance-to-a-line is a bivariate function of constant degree when parameterized suitably, so the problem is equivalent to bounding the complexity of the lower envelope of n trivariate (or, after decomposition, bivariate) algebraic surface patches of constant degree. A dual/equivalent formulation: complexity of the lower envelope of n algebraic surfaces in ℝ⁴ (or "tiles" in ℝ³), studied in Sharir's envelope machinery. General position assumptions (no degeneracies, e.g., no four lines equidistant from a common point) are permitted, since degeneracies only increase complexity by constants or can be handled symbolically.

## Why does it matter?

This is one of the flagship open problems in combinatorial computational geometry (TOPP Problem 3), a test case for the power of the Davenport–Schinzel / lower-envelope theory in higher dimensions. A near-quadratic bound would give near-optimal algorithms for robot motion planning among polyhedral obstacles (proximity to edges), medial-axis/skeleton computation of 3D models, and proximity queries in CAD and molecular modeling. Its resolution would also either confirm or refute the widely believed meta-conjecture that lower envelopes of constant-degree pieces in fixed dimension have near-quadratic complexity.

## What's already known?

- **Lower bound:** Ω(n²) examples exist (easy: arrangements of lines with many Voronoi vertices).
- **Upper bounds:** Naïvely, pairs of lines give O(n²) bisector surfaces whose arrangement has O(n⁴·polylog) complexity; Sharir's general lower-envelope theory gives roughly **O(n^{3+ε})** for lower envelopes of trivariate functions — the best general bound applicable here (verify exact exponent). No technique specific to lines has broken below this.
- The 2D analogue (Voronoi of points, DS-sequences theory) is tight at O(n); point diagrams in 3D are O(n²) and tight. Lines in 3D sit in the stubborn middle.
- **Approaches tried and why they fail:** (i) charging schemes /exiting from the sharp dichotomy between "vertical decomposition" arguments that lose a factor of n; (ii) randomized incremental construction analyses (Agarwal, Sharir and others) stall at the same envelope bounds; (iii) cutting/polynomial-partitioning tools give improvements only for special configurations. The core obstacle: the bisector of two lines is a hyperbolic-paraboloid-like patch, and three-surface intersections triple up in ways no known DS-style sequence machinery tames in ℝ³.

## What would count as solving it?

Either of:
1. **Upper bound (positive):** a proof that the complexity of the Voronoi diagram of any n lines in general position in ℝ³ is O(n^{2+ε}) for any fixed ε>0 (constants may depend on ε). A referee would require a complete combinatorial charging/inductive argument or a new envelope bound of the same strength.
2. **Lower bound (negative):** an explicit family of n lines whose Voronoi diagram has Ω(n^{2+α}) complexity for some fixed α>0, with proof.
Partial credit: any bound of the form O(n^{c}) with c<3, or a superquadratic lower bound for a natural subclass (e.g., lines in "fat"/bounded-slope position).

## How to start

1. Read Sharir–Agarwal, *Davenport–Schinzel Sequences and Their Geometric Applications*, chapters on lower envelopes in higher dimensions, to internalize why the general theory stalls at n^{3+ε}.
2. Work out the exact algebraic structure of the bisector of two lines (a hyperbolic paraboloid patch) and of Voronoi vertices (equidistant from three lines). Determine which bisector-patch intersections can actually appear on the final envelope — special structure of lines (vs. arbitrary surfaces) is the exploitable slack.
3. Try a charging scheme on Voronoi vertices: charge each vertex to a pair of lines and show each pair is charged n^ε times, using a "pseudo-disk-like" argument on the bisector patches restricted to zones.
4. For a counterexample attempt, consider lines near a common ruled surface (regulus/hyperboloid), where many bisectors interact degenerately.

## Key references

- M. Sharir, "Almost Tight Upper Bounds for Lower Envelopes in Higher Dimensions," *Discrete Comput. Geom.* 12 (1994). Establishes near-cubic bounds for lower envelopes of trivariate functions, the machinery behind the best known upper bound for this problem. https://link.springer.com/article/10.1007/BF02574380
- The Open Problems Project (TOPP), Problem 3. Statement of the problem of near-quadratic complexity of the lower envelope/Voronoi diagram of lines in 3D. https://topps.apphost.org/the-open-problems-project/ (verify exact URL)
- P. K. Agarwal and M. Sharir, "Davenport–Schinzel Sequences and Their Geometric Applications" (book/CRC chapter, 1995/2017). Comprehensive treatment of envelope combinatorics, the DS-type tools a solver must master. (verify edition)
- (verify) Additional relevant work on Voronoi diagrams of lines/segments in 3D exists by authors such as Aurenhammer, Klein, and Sharir; no sub-cubic bound is known.

## Warnings

- Do not conflate this with Voronoi diagrams of *segments/polyhedra edges under L∞ or convex distance functions*, where different (sometimes quadratic or even linear) bounds are known — the Euclidean, full-lines, 3D case is the open one.
- The "obvious" reduction to lower envelopes of n algebraic surfaces in ℝ³ yields the n^{3+ε} bound; any improvement must exploit that the surfaces are *bisectors of lines*, not arbitrary.
- Beware degenerate line configurations (skew lines on a common regulus, coplanar families) — general position assumptions must be stated explicitly, and near-degenerate families are exactly where counterexamples (if any) would live.

---
*`ALGO-000158` · unverified*

## Acceptance guidance

Either of:
1. **Upper bound (positive):** a proof that the complexity of the Voronoi diagram of any n lines in general position in ℝ³ is O(n^{2+ε}) for any fixed ε>0 (constants may depend on ε). A referee would require a complete combinatorial charging/inductive argument or a new envelope bound of the same strength.
2. **Lower bound (negative):** an explicit family of n lines whose Voronoi diagram has Ω(n^{2+α}) complexity for some fixed α>0, with proof.
Partial credit: any bound of the form O(n^{c}) with c<3, or a superquadratic lower bound for a natural subclass (e.g., lines in "fat"/bounded-slope position).

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/ddf14b4b-2ca7-45ec-8348-6f00f356b720?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000158.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000158)
