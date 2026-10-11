# Superseded results

These certificates remain valid improvements over their dated starting sources. Smaller packings are now available from the public comparisons or from a later refinement above. They are retained as superseded and excluded from the current registration request.

| Unit squares | Historical certified upper bound (rounded up) | Certificate | Current standing |
| ---: | ---: | --- | --- |
| 70 | 8.880960371556215075 | [n070.cert](certificates/refinements-2026-10-10/n070.cert) | Superseded |
| 103 | 10.679232047362129301 | [n103.cert](certificates/refinements-2026-10-10/n103.cert) | Superseded |
| 123 | 11.591378145498503553 | [n123.cert](certificates/refinements-2026-10-10/n123.cert) | Superseded |
| 129 | 11.872029849081310953 | [n129.cert](certificates/refinements-2026-10-10/n129.cert) | Superseded |
| 146 | 12.583782204439681157 | [n146.cert](certificates/refinements-2026-10-10/n146.cert) | Superseded by later refinement |
| 237 | 15.903670905778137000 | [n237.cert](certificates/n237.cert) | Superseded |
| 295 | 17.704232790737265264 | [n295.cert](certificates/refinements-2026-10-10/n295.cert) | Superseded |

The newer [comparison certificate](https://raw.githubusercontent.com/franciscouzo/square-packing/f311f08901c24b2a6c5f720710a45adec23e926a/certificates/n237.cert) for the earlier large-layout refinement has side `15.90294960767783168971278840528` and passed both project exact checkers. Earlier versions and dated comparisons are retained in [the first result file](results/quiet-2026-10-10.json) and [the subsequent refinement file](results/threshold-2026-10-10.json).

These files are historical feasible packings, rather than current best claims. The current results are listed in [the main README](../README.md). Certificate bytes and their hashes are preserved; metadata paths are relative to the repository root.

## Method and credit

| Unit squares | Method used for the saved result | Hardware used |
| ---: | --- | --- |
| 237 | Shear/angle perturbation, L-BFGS relaxation under a box-size and overlap penalty, then sparse sequential linear programming. | CPU |

| Unit squares | Original layout and prior refinement | Checked starting bound | Source | Checked on |
| ---: | --- | --- | --- | --- |
| 237 | **Nate Chaoweeraprasit / SQUISH**, with an exact precision refinement by **Siddharth Gupta**. | `3180735247037827607980371558401 / 200000000000000000000000000000` | [Pinned comparison certificate](https://raw.githubusercontent.com/SidG2k1/square-packing-refinements/9643cb5a78c1d4dcfc867c80a6920c3a6219d05a/witnesses/packing-237.cert) | 9 October 2026 |

| Certificate | SHA-256 |
| --- | --- |
| [n237.cert](certificates/n237.cert) | `76253edce982bae58907c8c39a18433a053eb2a89adccd2dcea58737e09966b6` |
