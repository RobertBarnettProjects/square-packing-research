# Square packing refinements

Verified improvements for packing identical unit squares into a larger square.

Refinements found by me, Robert Barnett, with the assistance of codex.

## Results

The following saved certificates remain below the strongest relevant public comparisons located on 11 October 2026, including open and closed issues and their comments in [jlevy/squares](https://github.com/jlevy/squares/issues). These are local refinements of existing layouts. Catalogue acceptance and global optimality are unestablished.

| Unit squares | Checked comparison side (approx.) | Certified upper bound (rounded up) | Side reduction (approx.) | Certificate | Diagram |
| ---: | ---: | ---: | ---: | --- | --- |
| 146 | 12.58378227741507688182… | **12.583782203951046204** | 7.346403E-8 | [n146.cert](certificates/n146.cert) | [Packing](images/n146.png) |
| 261 | 16.6787798754 | **16.678779875343207747** | 5.679225E-11 | [n261.cert](certificates/n261.cert) | [Packing](images/n261.png) |
| 2,043 | 45.69642783940993535889… | **45.69569132055726** | 0.0007365189 | [n2043.cert](certificates/n2043.cert) | — |

Each certificate establishes `s(n) <= S`, with the exact rational side `S` in its first data row. [The result metadata](results/review-2026-10-11.json) retains the exact sides, differences, source revisions, hashes and verification receipts. Displayed upper bounds are rounded upward; reduction figures are approximate.

For the smaller precision refinement, the comparison uses the source's original side after removing its stated centre dilation. Its gain therefore extends beyond removal of certificate padding.

The two current results below the submission catalogue's size limit were submitted in [this registration issue](https://github.com/jlevy/squares/issues/505) on 12 October 2026; review and acceptance are pending.

## Historical results

Superseded certificates and their dated comparisons are retained in [the separate archive](superseded/README.md).

## Method

The search refines existing configurations by adjusting square centres, rotations and the enclosing side. Perturbation and relaxation can help find a promising configuration; sparse sequential linear programming provides local refinement. Backtracking and conservative feasibility repair keep retained numerical candidates feasible.

| Unit squares | Method used for the saved result | Hardware used |
| ---: | --- | --- |
| 146 | Minimum-movement sequential linear programming, followed by exact rational contraction and recertification. | CPU |
| 261 | Minimum-movement sequential linear programming, followed by exact rational contraction and recertification. | CPU |
| 2,043 | Sparse sequential linear programming of centres, rotations and the enclosing side. | CPU |

The final coordinates and rotations were converted into exact rational certificates and checked separately from the optimizer. Search code and run logs are currently held outside this repository; the files here are sufficient to check the resulting packings.

## Verification

The current candidates were replayed on 11 October 2026 and passed four exact checks: two checkers developed during this project and the two published checkers from [Evan Daniel's square-packing repository](https://github.com/evand/square-packing/tree/268af529546176a25224ea3b2c7d29cef8d9e911/search/exact). These use separating-axis and polygon-intersection tests with rational arithmetic.

They also passed [David Ellsworth's packing checker](https://github.com/Davidebyzero/packing_squares_in_squares__tools/tree/79f8a378d52e757d70f7cfb2c2f7a24a53da0204), using 140-digit coordinate exports and tolerance `1e-90`. That is supplementary numerical evidence; the exact certificates establish the bounds.

To check the certificates yourself, download these two unchanged reference scripts and save them alongside this README:

- [verify_cert.py](https://raw.githubusercontent.com/evand/square-packing/268af529546176a25224ea3b2c7d29cef8d9e911/search/exact/verify_cert.py)
- [verify_cert2.py](https://raw.githubusercontent.com/evand/square-packing/268af529546176a25224ea3b2c7d29cef8d9e911/search/exact/verify_cert2.py)

Run from the repository root with Python 3, replacing `PATH_TO_CERTIFICATE` with a certificate path from the results table. No third-party packages or optimizer are required.

```sh
python verify_cert.py PATH_TO_CERTIFICATE
python verify_cert2.py PATH_TO_CERTIFICATE
```

Each command should report `VALID`. The checkers account for every pair of squares and establish strictly positive wall clearance and pairwise separation.

## Certificate format

Comments begin with `#`. The first data row contains the square count and rational enclosing side. Each subsequent row contains a square's centre coordinates `x`, `y` and rational half-angle parameter `t`:

```text
n S
x y t
...
```

The rotation is represented by:

```text
c = (1 - t*t) / (1 + t*t)
s = 2*t / (1 + t*t)
```

Since `c*c + s*s = 1` exactly, the four vertices `(x, y) + (a*c - b*s, a*s + b*c)/2`, for `a,b` in `{-1,1}`, describe an exact unit square. All deciding inequalities use exact fractions. Rounded coordinates, diagrams and displayed angles are illustrative; the certificate files are authoritative.

SHA-256 of the certificate files:

| Certificate | SHA-256 |
| --- | --- |
| [n146.cert](certificates/n146.cert) | `77b5524f387472a8e5996e319d05735e2a6a0046c24e7043995549bf3945fa3d` |
| [n261.cert](certificates/n261.cert) | `9141f7eb86ae23388d349efd810992727f16ca09bc9d0d1a5b94cd5e2a3f0019` |
| [n2043.cert](certificates/n2043.cert) | `bfbefba7df7481d409620da9843a51fcaf92c02fdcb733f0c0e24796fb5bd779` |

## Sources and credit

| Unit squares | Original layout and prior refinement | Checked comparison bound | Source | Checked on |
| ---: | --- | --- | --- | --- |
| 146 | **Ryan Xu**, with public regularization by **Evan Daniel**. | `12.583782277415076881822471933138952021758854841075` (reported side; exact source certificate checked) | [Pinned regularized certificate](https://raw.githubusercontent.com/evand/square-packing/7dfca4e474e5822479f3da3fadf537fb2dbd0efc/search/regularize/lists/certs/n-146.cert.gz) | 11 October 2026 |
| 261 | **Ryan Xu**. | `16.6787798754` (original side and undilated coordinate span; exact source certificate side is `16.6787798754166787798754`) | [Pinned source certificate](https://raw.githubusercontent.com/ry-xu/square_packing/8dc415296f697f5140caea27c7a0193d52deb4e6/certificates/n261/n261.cert.json) | 11 October 2026 |
| 2,043 | **David Ellsworth**, subsequently improved by **Grigoriy Dyachkov**. | `45.69642783940993535889741755` | [Pinned starting coordinates](https://raw.githubusercontent.com/evand/square-packing/7cc5af60a60cbe41f3f037839d1c111f11375f64/site/www/data/p/square-2043.json) | 9 October 2026 |

OpenAI Codex assisted the numerical search, verification and preparation of these results. The two project-authored checkers were developed within this assisted research project; they are not separate human audits.
