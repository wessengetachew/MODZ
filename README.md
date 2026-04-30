# Modular Lifting Rings

**Live:** [wessengetachew.github.io/MODZ/](https://wessengetachew.github.io/MODZ/)

An interactive exploration of coprime residue geometry, lift survival, and prime spiral structure in modular arithmetic.

---

## What It Shows

For each modulus M ≥ 1, the coprime residue group

```
R(M) = { r ∈ {0, …, M−1} : gcd(r, M) = 1 }
```

is placed on a circle at angles θ = 2πr/M. A residue r **lifts** from ring M to ring M+1 when gcd(r, M+1) = 1 as well. The long-run fraction of residues that lift converges to

```
C = ∏_p (p²−2)/(p²−1) ≈ 0.530711806246…
```

This constant is OEIS A065469. The **lift survival** framing — residues surviving the transition between consecutive rings — is the original contribution of this work.

---

## Features

### Canvas

- **Four arrangements** — Concentric (ring M at radius M), Fermat spiral (radius √M), Farey half-plane (point at r/M, 1/M), Strip (column M, row θ)
- **Pan and zoom** — click-drag to move, scroll to zoom toward cursor, pinch-to-zoom on mobile, double-click to reset
- **Inspect mode** — toggle to click individual points and see r, M, gcd(r,M+1), sector, lift status, mirror, appearances across rings
- **M=1 origin point** — the primitive seed at angle 0°, always rendered as a white dot with glow halo

### Color Modes

| Mode | Colors by |
|------|-----------|
| **New r** (default) | Each residue value r gets a stable hue — same r is always the same color across all rings |
| **Sector 1/n** | Which Farey sector r/M falls in (1/(n+1), 1/n] |
| Angle θ | Rainbow by position on circle |
| r is prime | Teal if r is prime |
| r/M parity | Four colors for odd/even combinations |
| Quadratic residue | r is a QR mod M |
| φ(M)/M density | Coprime density of ring M |
| Divisor count Ω(M) | Total prime factors of M |
| Prime gap class | Gap class of M |
| Lift ✓/✗ | Teal = lifts, red = blocked |

### Overlays

- **Prime spiral** — for a fixed prime p, traces its path across rings; highlights the equator gap at M=2p (Lemma 8.1), mirrors (Lemma 8.2), bottom sector (Lemma 8.3)
- **Lift lines** — connect consecutive appearances of each residue; green = lifts, red = blocked
- **N-gon polygons** — connect coprime points on each ring (gcd=1 polygon), or all integer points (full M-gon), or both. M=3 gives a triangle, M=4 gives a square (coprime) or full square (all), M=6 gives a triangle (coprime) or hexagon (all)
- **n-paths** — the (M±n)/2 upper/lower paths; n=1 gives the permanently blocked upper path (Lemma 8.4) and the Z[i]-linked lower path (Lemma 8.5)
- **Gap chords** — connect residues r and r+k on the same ring; gap k=2 gives twin-prime pairs, k=6 gives sexy pairs
- **Non-coprime points** — gcd(r,M)>1 residues rendered in dim colors by their gcd value

### Theorem Presets

One-tap presets in the header strip load configurations illustrating each lemma:

| Preset | Shows |
|--------|-------|
| §2 Euler | C_k Euler product conditioned on k |
| §6 ζ·d_FT | C = ζ(2)·d_FT Feller–Tornier identity |
| §7 Primorial | T(p#)=φ(p#) ⟺ p#+1 prime |
| 8.1 Equator | gcd(p,2p)=p — forced gap at M=2p |
| 8.2 Mirror | Mirror lift identity |
| 8.3 Sector | Bottom sector count p−2 |
| 8.4 Upper | (M+1)/2 never lifts |
| 8.5 Lower | (M−1)/2 lifts iff M≡3(mod 4) / q inert in Z[i] |
| C(1)–C(4) | Conditioned survival rates — "density leakage" |

### Export

- **Canvas only** — 3840×2400 PNG with title, auto-subtitle (M range, prime, arrangement, paths), footer watermark
- **Canvas + Legend** — same with 880px legend panel: active layers, parameters, point counts, empirical C(N), C identity
- **Portrait share** — 2160×3840 PNG optimised for mobile sharing

### Tools

Five companion visualizations accessible via the Tools overlay:

- **MLR Viz** — Modular Lifting Rings full visualization
- **Farey & Unit Circle** — rational unit circle, Ford circles, Farey sequence
- **Gap ζ(2)** — gap-class decomposition of ζ(2) = π²/6
- **Farey Summatory** — Farey summatory function and Franel–Landau connection to RH
- **Mod Reduction** — modular reduction projection research portal

### Paper

The in-app paper (tap "Paper") documents:

- **Definition** of lift survival and C
- **Proposition 1** — Euler product for C_k
- **Remark** — C = ζ(2)·d_FT (Feller–Tornier, known)
- **Proposition 2** — T(p#) = φ(p#) ⟺ p#+1 is prime, with full proof
- **Lemmas 8.1–8.5** — prime spiral geometry, each with short proofs
- **§6** — interactive C_k density leakage via chain slider
- **References** — Erdős 1951, Feller–Tornier 1932, Tóth–Sándor 1989, Tóth 2010

---

## The Mathematics

### Lift Survival Constant

```
C  =  lim_{N→∞}  [Σ_{M=2}^{N} T(M)]  /  [Σ_{M=2}^{N} φ(M)]
   =  ∏_p (p²−2)/(p²−1)
   =  ζ(2) · d_FT
   ≈  0.530711806246…
```

Verified to 8 significant figures for N = 2,000,000. OEIS A065469 (Tóth–Sándor 1989). The lift survival framing is original.

### Conditioned Rate C_k

```
C_k  =  ∏_{p ∤ k} (p²−2)/(p²−1)  ·  ∏_{p | k} (p−1)(p²+p−1)/p³
```

C_k < C for all k ≥ 2. C_k = C_{rad(k)} — depends only on which primes divide k, not multiplicities. The chain slider shows this density leakage live:

```
C(1) ≈ 0.530711    C(2) ≈ 0.413061
C(3) ≈ 0.373969    C(4) ≈ 0.337595
```

### N-gon Connection

The coprime residues of R(M) are exactly the vertices of the regular M-gon that are **primitive** — they generate the full cycle under repeated addition mod M. For prime M, every non-zero residue is coprime, giving a complete (M−1)-gon. For composite M, the coprime polygon has φ(M) vertices — the multiplicative group (Z/MZ)×.

---

## Status

| Result | Status |
|--------|--------|
| C as lift survival fraction | Original geometric interpretation |
| C = ζ(2)·d_FT | Known identity — Feller–Tornier 1932 |
| Euler product for C_k | Elementary, likely not in literature in this form |
| Monotonicity C_j > C_k | Immediate from product formula |
| T(p#) = φ(p#) ⟺ primorial prime | Correct, proof provided |
| Lemmas 8.1–8.5 | Elementary gcd observations, proofs provided |

---

## References

- Erdős, P. (1951). On the density of some sequences of integers.
- Feller, W., Tornier, E. (1932). Mengentheoretische Untersuchung von Eigenschaften der Zahlenreihe.
- Tóth, L., Sándor, J. (1989). On some arithmetical products. — OEIS A065469.
- Tóth, L. (2010). On the probability that two randomly chosen integers are k-free.

---

## Author

Wessen Getachew · 2026 · [@7dview](https://twitter.com/7dview)
