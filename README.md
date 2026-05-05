# Modular Lifting Rings

**[→ Live Tool](https://wessengetachew.github.io/MODZ/)**

An interactive visualization of coprime residue geometry and lift survival in modular arithmetic. For each modulus M, the integers coprime to M are placed on a circle at angles proportional to their value. The question — which of these points also survive to ring M+1 — converges to a classical constant woven from π and prime numbers.

---

## What it shows

Place every integer r coprime to M on a unit circle at angle θ = 2πr/M. This is **ring M**. A point r **lifts** to ring M+1 when gcd(r, M+1) = 1. The fraction of points that lift, averaged across all rings up to N, converges to

```
C = ζ(2) · ∏_p (1 − 2/p²) ≈ 0.530711806246…
```

the product of ζ(2) = π²/6 with the Feller–Tornier constant d_FT (OEIS A065469). The live status bar tracks this convergence as you adjust the M range.

---

## Features

### Canvas
- **4 arrangements** — Concentric (radius ∝ M), Fermat (radius ∝ √M), Farey (x = r/M, y = 1/M), Strip (linearized columns)
- **16 color modes** — residue hue, Farey sector, angle, lift ✓/✗, parity, quadratic residue, φ(M)/M density, prime gap class, entropy, and more
- **Lift lines** — green segments where gcd(r, M+1) = 1; red half-lines with ✗ where blocked
- **Chain slider** — require n consecutive lifts; empirical survival rate shown live
- **Prime spiral** — trace any prime p across all rings; equator gap at M=2p, upper/lower path geometry
- **N-gon polygons** — connect coprime points to see (ℤ/Mℤ)× as a geometric object
- **Gap chords** — connect residues r and r+k on the same ring for any gap k
- **Mirror path** — M−p residues in the top half of the spiral; φ(p+1) of them lift by the mirror bijection
- **Primorial rings** — highlighted in amber; 100% lift rate when p#+1 is prime
- **Inspect** — click any point for full arithmetic details (gcd, angle, Farey sector, lift status, mirror)
- **Global rotation** — set as a/b × 360° fraction; default 90° (1/4 turn)
- **Snap to circle** — project all points to exact ring radius; affects lift lines and all overlays

### Live counters (status bar, scrollable)
| Counter | Converges to |
|---------|-------------|
| φ/total | 6/π² ≈ 60.79% |
| lift/φ = C(N) | C ≈ 0.530712 |
| M range | current ring count |

### Export
- **Canvas only** — 3840×2400 or 7680×4800 PNG
- **Canvas + Legend** — ring view with full parameter legend panel
- **Portrait** — 2160×3840 for mobile sharing

---

## Tool Tabs

Five companion visualizations accessible via the Tools button:

| Tab | What it shows |
|-----|--------------|
| **MLR Viz** | Standalone coprime residue geometry with rational fraction layer |
| **Farey & Circle** | Farey sequence F_N on the unit circle; Ford circles; mediant structure |
| **Gap ζ(2)** | Decomposition of π²/6 by prime gap class; convergence charts |
| **Farey Summatory** | Summatory function F(N) and its deviation — connected to the Riemann Hypothesis via the Franel–Landau theorem |
| **Mod Reduction** | Modular reduction projection; chandelier visualization of reduction chains |

Each tab has its own ↓ PNG export.

---

## The Mathematics

All results are classical. The contribution is the geometric arrangement and the interactive tool.

**Lift survival constant:**
```
C = ∏_p (p²−2)/(p²−1) = ζ(2) · d_FT ≈ 0.530711806246
```

**Coprime density:**
```
lim_{N→∞} Σφ(M) / Σ(M−1) = 6/π² ≈ 0.607927
```

**Primorial lift** (Euclid): T(p#) = φ(p#) iff p#+1 is prime.

**Mirror bijection**: For p < M < 2p, gcd(M−p, M+1) = gcd(M−p, p+1). Exactly φ(p+1) of the p−1 mirror residues lift — a bijection with units of ℤ/(p+1)ℤ.
# Modular Lifting Rings — Full Mathematical Reference

**Live tool:** [wessengetachew.github.io/MODZ/](https://wessengetachew.github.io/MODZ/)  
*Wessen Getachew · 2026*

---

## Table of Contents

1. [Main Canvas — MLR](#1-main-canvas--modular-lifting-rings)
2. [Tab 1 — MLR Viz](#2-tab-1--mlr-viz)
3. [Tab 2 — Farey & Circle](#3-tab-2--farey--circle)
4. [Tab 3 — Gap ζ(2)](#4-tab-3--gap-ζ2)
5. [Tab 4 — Farey Summatory](#5-tab-4--farey-summatory)
6. [Tab 5 — Mod Reduction](#6-tab-5--mod-reduction)

---

## 1. Main Canvas — Modular Lifting Rings

### The Geometry

For each modulus M ≥ 1, the **coprime residues** are:

```
R(M) = { r ∈ {1, …, M−1} : gcd(r, M) = 1 }     |R(M)| = φ(M)
```

Each r is placed at angle **θ = 2πr/M** on a circle. Ring M sits at radius proportional to M (or √M, log M, M², or on a single unit circle depending on the ring scale setting). Together the rings form a nested field of dots — the **modular ring system**.

**How it draws:** For each M in [M_min, M_max], for each r with gcd(r,M)=1, compute:

```
x = cx + ρ(M) · cos(2πr/M + α + (M−1)·δ)
y = cy − ρ(M) · sin(2πr/M + α + (M−1)·δ)
```

where α is the global rotation, δ is the per-ring rotation increment, and ρ(M) is the radius function (linear/sqrt/log/quadratic/unit).

### The Lift Condition

A residue r on ring M **lifts** to ring M+1 when:

```
gcd(r, M+1) = 1
```

Green line segments connect (M, r) to (M+1, r) when this holds. Red half-lines with × marks when blocked.

### The Lift Survival Constant

```
C = lim_{N→∞} [ Σ_{M=2}^{N} T(M) ] / [ Σ_{M=2}^{N} φ(M) ]

  = ∏_p (p²−2)/(p²−1)

  = ζ(2) · ∏_p(1−2/p²)

  = ζ(2) · d_FT  ≈  0.530711806246…
```

where T(M) = |{r ∈ R(M) : gcd(r,M+1)=1}| and d_FT ≈ 0.3226 is the Feller–Tornier constant (OEIS A065469). The status bar shows C(N) converging live as M_max grows.

**Coprime density:**

```
Σφ(M) / Σ(M−1)  →  6/π²  ≈  0.6079
```

### Chain-n Survival

```
gcd(r, M+j) = 1   for j = 1, 2, …, n
```

The chain slider requires n consecutive lifts. The live rate T_n(M)/φ(M) is shown in the status bar.

### Ring Scale Options

| Scale | Radius ρ(M) | Effect |
|---|---|---|
| Linear | M · s | Default; outer rings visually sparser |
| Square root | √M · s | Equalizes arc density |
| Logarithmic | log(M)/log(M_max) · R | Inner rings get more space |
| Quadratic | (M/M_max)² · R | Inner rings compressed |
| Unit circle | R (constant) | All rings on one circle — pure angle geometry |

### Color Modes (18 total)

| Mode | Formula |
|---|---|
| New r | h = (r × 137.508°) mod 360 — golden ratio hash |
| Sector 1/n | k = min k s.t. r/M ≤ 1/k; hue by sector k |
| Angle θ | hue = (r/M) × 300° |
| Lift ✓/✗ | teal if gcd(r,M+1)=1, red otherwise |
| Lift survival rate | ring colored by T(M)/φ(M); teal above C, orange below |
| Parity | 4-way split by (r mod 2, M mod 2) |
| Quadratic residue | teal if ∃x: x²≡r (mod M) |
| r mod 6 | 6 colors; primes >3 always in slots 1 or 5 |
| r is prime | prime r = teal |
| Prime ring M | prime M = teal |
| φ(M)/M density | brightness proportional to φ(M)/M |
| Divisor count Ω(M) | hue by Ω(M) = Σ v_p(M) |
| Modular entropy | ΔS_M = −Σ (e_i/Ω) ln(e_i/Ω) for M = ∏p_i^{e_i} |
| Primorial rings | amber if M ∈ {2,6,30,210,2310,…} |
| Mersenne rings | violet if M = 2^n − 1 |
| Prime gap class | for prime M: hue by (next_prime(M) − M) |
| Top / Bottom ½ | teal if r/M > ½, orange if r/M < ½ |
| Monochrome | neutral gray — publication-ready |

### Prime Spiral Overlays

For prime p, traces r=p across rings where gcd(p,M)=1:

```
θ(p, M) = 2πp/M    (sweeps as M grows)
```

**Three canonical theorems drawn:**

> **Equator gap at M = 2p**  
> gcd(p, 2p) = p ≠ 1. The spiral always skips ring 2p. Visible as a break in the path.

> **Upper path r = (M+1)/2 — always blocked**  
> gcd((M+1)/2, M+1) = (M+1)/2 ≥ 2. Never lifts. Permanent red barrier.

> **Lower path r = (M−1)/2 — alternating**  
> gcd((M−1)/2, M+1) = gcd((M−1)/2, 2) = 1 iff M ≡ 3 (mod 4).  
> For prime q: this is the condition for q being inert in ℤ[i] — not expressible as a sum of two squares.

**Mirror path:** For p < M < 2p, the mirror residue is M−p. Since gcd(M−p, M+1) = gcd(M−p, p+1), exactly **φ(p+1)** of the p−1 top-half mirrors lift — a bijection with units of ℤ/(p+1)ℤ.

### Path Systems

**Paths (M±n)/2:** For rings M where M and n share parity:

```
r_upper = (M+n)/2    lifts iff gcd((M+n)/2, M+1) = 1  [NEVER when n=1]
r_lower = (M−n)/2    lifts iff gcd((M−n)/2, M+1) = 1  [iff M≡3 mod 4 when n=1]
```

**Ray path a/b:** A ray at angle 2π·(a/b) hits ring M at:

```
r_ray = round(M × a/b)
```

Cyan trace. Neighbors r_ray ± n in violet (lower) and orange (upper).

### Export

All exports use `canvas.toBlob()` → `URL.createObjectURL()` for Android compatibility.

| Mode | Resolution | Contents |
|---|---|---|
| Canvas only | 3840×2400 or 7680×4800 | Title + ring view + footer |
| Canvas + Legend | 3840×2400 or 7680×4800 | Ring view + 960px parameter legend |
| Portrait share | 2160×3840 | Vertical layout |

Labels export at 3× font scale. Export dialog shows live preview before download.

---

## 2. Tab 1 — MLR Viz

**Full title:** Modular Lifting Rings — Coprime Residue Geometry  
**What it shows:** A standalone ring visualization with deeper mathematical exposition, trajectory analysis, and derivation of the constant C.

### The Geometry (same ring system, different framing)

Each coprime residue r on ring M encodes a reduced fraction r/M ∈ (0,1). The angular position θ = 2πr/M places it on the circle. In polar coordinates with ρ = M:

```
ρ · θ = M · (2πr/M) = 2πr = constant
```

This means **the arc length swept by residue r is constant across all rings** — the trajectory forms a hyperbolic spiral satisfying ρθ = 2πr.

### Lift Condition (geometric form)

```
lift r : M → M+1  ⟺  gcd(r,M) = 1  AND  gcd(r,M+1) = 1
```

Equivalently: the fraction r/M persists to ring M+1 iff r remains coprime to both denominators.

### Derivation of C

```
C = lim_{N→∞} (1/N) Σ_{M=2}^{N} T(M)/φ(M)

  = ∏_p (1 − 2/p²) · ζ(2)

  = ∏_p (p²−2)/(p²−1)
```

**Closed form via Euler product:** Expanding the lift probability for each prime p independently (they are asymptotically independent by the Chinese Remainder Theorem), the probability that r survives both gcd(r,M)=1 and gcd(r,M+1)=1 for a random prime p is (p²−2)/(p²−1).

### Color Modes in MLR Viz

| Mode | Mathematical meaning |
|---|---|
| Rainbow (angle) | hue = θ/(2π) — pure angular position |
| Survival rate | T(M)/φ(M) per ring — teal = high, orange = low |
| Modular entropy ΔS_m | ΔS = −ln(φ(m)/m) — information content of ring m |
| Prime ring | highlight prime moduli |
| Residue class mod 6 | since all primes > 3 are ≡ 1 or 5 (mod 6) |
| Mersenne rings | M = 2^n − 1 — related to perfect numbers |
| Primorial rings | M = p# — maximum-entropy rings |
| Gap class | gap to next prime for prime M |

### Theorems Displayed

**Prime-Crossing Theorem:** For any prime p and ring M with gcd(p,M)=1, the residue r=p appears on ring M and traces the hyperbolic spiral ρθ = 2πp.

**Mersenne Halving Theorem:** If M = 2^n − 1 (Mersenne), then every odd r coprime to M satisfies r/M ≈ r/(2^n) — residues cluster near dyadic rationals on the circle.

**Lift Count Formula:**
```
T(M) = Σ_{r=1}^{M-1} [gcd(r,M)=1] · [gcd(r,M+1)=1]
     = φ(M) - |{r ∈ R(M) : gcd(r,M+1) > 1}|
```

**ζ(2) Gap Class Decomposition:**
```
ζ(2) = ∏_g P_g    where P_g = ∏_{p: gap(p)=g} p²/(p²−1)
```

Each prime gap class g contributes a multiplicative factor P_g to ζ(2).

**Modular Entropy:**
```
ΔS_m = −ln(φ(m)/m) = Σ_{p|m} ln(p/(p−1))
```

Primorials maximize entropy at each prime level. The entropy grows like ln ln m.

### How It Draws

```javascript
rings.forEach(ring => {
  const sr = ring.rho * scale;        // radius = M × scale
  // draw ring circle
  ctx.arc(cx, cy, sr, 0, 2*Math.PI);
  
  ring.points.forEach(({r, theta, lifts}) => {
    const x = cx + sr * Math.cos(theta + globalRot);
    const y = cy - sr * Math.sin(theta + globalRot);
    // color by selected mode, draw dot
    // if lifts: draw green line to next ring
  });
});
```

Trajectory lines connect same-r residues across consecutive rings, tracing the hyperbolic spiral visually.

---

## 3. Tab 2 — Farey & Circle

**Full title:** Farey Modular Residue Rings — Rational Unit Circle Structure  
**What it shows:** The Farey sequence F_N made geometric — each rational r/m placed at angle 2πr/m on ring m, with Ford circles, cross-mod connections, and gap chord overlays.

### The Farey Sequence

```
F_N = { r/m : 0 ≤ r ≤ m ≤ N, gcd(r,m) = 1 }   (sorted ascending)
|F_N| = 1 + Σ_{m=1}^{N} φ(m)  ≈  3N²/π²
```

Adjacent fractions a/b and c/d in F_N satisfy the **mediant property**:

```
bc − ad = 1     (unimodular adjacency)
```

Their mediant (a+c)/(b+d) is the next fraction inserted as N increases.

### How It Draws

Each rational r/m is placed at:

```
θ = 2πr/m        (angle on ring m)
ρ = radius(m)    (configurable: linear, sqrt, log, quadratic, unit circle)
```

**Radius function:**

```javascript
function radius(m) {
  if (scale === 'log')        t = log(m) / log(N);
  else if (scale === 'sqrt')  t = sqrt(m) / sqrt(N);
  else if (scale === 'quadratic') t = m² / N²;
  else if (scale === 'unitcircle') return R_max;   // all rings on one circle
  else                        t = (m−1) / (N−1);  // linear
  return R_min + (R_max − R_min) · t;
}
```

Blue dots: gcd(r,m)=1 (coprime — on the Farey sequence). Gray dots: gcd(r,m)>1 (non-coprime — reducible fractions).

### Ford Circles

For each reduced fraction r/m, the Ford circle has:

```
center = (r/m, 1/(2m²))    (in the upper half-plane)
radius = 1/(2m²)
```

Two Ford circles for p/q and r/s are **tangent** iff |ps − qr| = 1 (exactly the Farey adjacency condition). The tool draws Ford circles as tangent discs above the unit interval.

### Cross-Mod Connections

The cross-mod overlay traces residue r through rings N→1. For a fixed r, the sequence of appearances:

```
{m : gcd(r,m) = 1,  m ∈ [1,N]}
```

forms a path spiraling inward. These paths visualize the **Farey channel** each residue cuts through the modular structure.

### Gap Overlay

For primes p with forward gap g = next_prime(p) − p, the overlay marks:

```
(p mod N, (p+g) mod N)    as a chord on the outer ring
```

This shows which gap classes dominate the outer Farey ring — twin primes (g=2) produce many short chords; larger gaps produce longer chords.

### Display Modes

| Mode | What is drawn |
|---|---|
| Circle + Rectangle | Unit circle left, [0,1]×[0,1/m] rectangle right — dual view |
| Rectangle only | Farey fractions as a 2D plot: x=r/m, y=1/m |
| Circle only | Pure angular embedding on nested rings |
| gcd=1 & gcd>1 | Both coprime (blue) and non-coprime (gray) points |
| gcd=1 only | Farey points only |
| gcd>1 only | Non-coprime structure — the complement |
| 1/gcd(r,N) | Color by gcd — reveals divisibility structure |
| φ(r)/r | Euler totient ratio per residue |

### Key Identities Visualized

```
|F_N| = 1 + Σ_{m=1}^{N} φ(m)    (count of Farey fractions)

Σ_{r/m ∈ F_N} r/m = (|F_N| + 1)/2    (symmetry: F_N is symmetric about 1/2)

Δθ = 2π · (1/m − 1/(m+1)) = 2π/(m(m+1))    (minimum gap between adjacent Farey fractions)
```

---

## 4. Tab 3 — Gap ζ(2)

**Full title:** Gap-Class Decomposition of ζ(2) = π²/6  
**What it shows:** The Basel sum ζ(2) = Σ 1/n² decomposed by prime gap class — two structures (modular rings + gap decomposition) displayed in parallel to reveal how prime gap statistics control the zeta function value.

### The Main Result

```
ζ(2) = π²/6 = ∏_{p prime} p²/(p²−1)

     = ∏_{g ∈ G} P_g

where P_g = ∏_{p : next_prime(p)−p = g} p²/(p²−1)
```

G is the set of all even prime gaps {2, 4, 6, 8, 10, 12, …}. Each gap class g contributes a multiplicative factor P_g. Their product equals exactly π²/6.

**Why this factorizes:** The Euler product ζ(2) = ∏_p p²/(p²−1) is a product over all primes. Grouping primes by their forward gap g partitions the product by gap class.

### The Two Diagrams Drawn in Parallel

**Left — Modular ring diagram:**

Each rational r/m at angle 2πr/m on ring m (same geometry as Farey tab). Primes highlighted. Cross-mod connections show the Farey channel. Gap overlay marks (p mod N, (p+g) mod N) for selected gap g.

**Right — ζ(2) convergence by gap class:**

For each gap class g, the partial product P_g(x) = ∏_{p≤x: gap(p)=g} p²/(p²−1) is tracked as x grows. The chart shows each gap class's contribution converging toward its limiting factor. Gap class 2 (twin primes, if infinite) contributes most — the P_2 factor dominates.

### What This Draws Mathematically

```javascript
// For each prime p up to N:
const g = next_prime(p) - p;          // gap class
const factor = p*p / (p*p - 1);      // p²/(p²−1)
P_g[g] *= factor;                     // accumulate gap-class product
running_product *= factor;            // running ζ(2) approximation

// Draw convergence line for each gap class g
// Draw modular ring at ring m=p with gap-chord from p to p+g (mod N)
```

### Gap Class Breakdown

| Gap g | Example primes | Contribution P_g | Status |
|---|---|---|---|
| 2 | (3,5),(5,7),(11,13),… | > 1 (largest factor) | Twin prime conjecture open |
| 4 | (7,11),(13,17),… | moderate | Cousin primes — likely infinite |
| 6 | (5,11),(7,13),… | moderate | Sexy primes — likely infinite |
| 8, 10, 12, … | various | decreasing | All conjectured infinite |

The convergence chart lets you see empirically how each gap class's partial product stabilizes — twin primes saturate fastest because p²/(p²−1) → 1 slowly for small p.

### Connection to Modular Rings

```
ζ(2) = Σ_{M=1}^{∞} 1/M²  =  (total coprime pairs / total pairs)^{-1}  ·  (lift rate correction)

     = (6/π²)^{-1} · C^{-1} · d_FT^{-1}   (schematically)
```

The ring diagram makes this visible: the density of blue dots (coprime residues) approximates 6/π², and the density of green lift lines approximates C ≈ 0.5307. The ζ(2) gap decomposition shows how the prime gaps organize the multiplicative structure behind both constants.

### Ford Circles in Gap Context

The gap overlay draws chords on the Ford circle diagram: for twin primes (p, p+2), the chord connects angle 2πp/N to 2π(p+2)/N on the outer ring — short chords. For gap-6 primes the chords are longer. The distribution of chord lengths encodes the gap distribution of primes.

---

## 5. Tab 4 — Farey Summatory

**Full title:** Farey Sequence Interval Analysis — Exploration Platform  
**What it shows:** The Farey summatory function F(N) and its deviation from the theoretical mean, connecting prime number theory to the Riemann Hypothesis through the Franel–Landau theorem. Also includes: Farey sector analysis, summatory totient formula, and harmonic/waveform visualization of coprime distributions.

### The Farey Summatory Function

```
F(N) = Σ_{r/m ∈ F_N} r/m    (sum of all Farey fractions up to order N)
```

**Theoretical mean:** Since F_N is symmetric about 1/2:

```
F(N) = (|F_N| + 1) / 2  ·  (1/2)  ·  |F_N|  ≈  3N²/(2π²)   (leading term)
```

More precisely:

```
F(N) = (|F_N| − 1)/2 + 1/2  =  (Σ_{m=1}^{N} φ(m)) / 2  +  1/2
```

### The Deviation — Connection to RH

Define:

```
Δ(N) = F(N) − (|F_N| − 1)/2 − 1/2
```

**Franel–Landau Theorem (1924):** The Riemann Hypothesis is equivalent to:

```
Δ(N) = O(N^{1/2 + ε})   for every ε > 0
```

The Franel sum:

```
S(N) = Σ_{n=1}^{N} (F(n)/|F_n| − 1/2)²
```

satisfies S(N) = O(N^{ε−1}) iff RH is true. The tool plots both Δ(N) and S(N) as N grows, letting you observe empirically how the deviation behaves.

### Farey Sector Analysis

The interval (0,1) is partitioned into Farey sectors:

```
S_n = (1/(n+1), 1/n]    for n = 1, 2, 3, …
```

For each sector S_n, the tool counts coprime fractions C(n,N) = |{r/m ∈ F_N : r/m ∈ S_n}| and compares to the Farey Sector Formula:

```
C(n, N) ≈ 3N² / (π² · n(n+1))
```

This asymptotic holds with relative error < 0.2% for N > 100. The visualization draws each sector as a colored arc on the ring diagram with its exact count and the formula prediction side-by-side.

### Summatory Totient Formula

```
Σ_{k=1}^{N} φ(k) = (1/2) [1 + Σ_{k=1}^{N} μ(k) ⌊N/k⌋²]
```

where μ is the Möbius function. The tab computes this exactly using the Möbius inversion and compares to the asymptotic:

```
Σ_{k=1}^{N} φ(k) ≈ 3N²/π²
```

Step-by-step table shows the contribution of each k, the μ(k) value, and the running sum.

### Waveform / Harmonic Visualization

The coprime distribution on each ring is treated as a periodic function f_m: [0,2π) → {0,1} where f_m(θ) = 1 if ∃r with gcd(r,m)=1 and θ = 2πr/m. This is decomposed into Fourier modes. The tool offers several waveform bases for visualizing the residue distribution:

| Waveform | Formula | Mathematical role |
|---|---|---|
| Sine | sin(2πr/m) | Fundamental Fourier component |
| Triangle | 2/π arcsin(sin(2πr/m)) | Odd harmonics only |
| Square | sgn(sin(2πr/m)) | Dirichlet character analogy |
| Sawtooth | r/m − ½ | Linear ramp — related to Dedekind sums |
| √3/π | √3/π ≈ 0.5513 | Equilateral triangle lattice constant |
| √6/π | √6/π ≈ 0.7797 | Face-centered cubic constant |
| 1/π | 1/π ≈ 0.3183 | Wallis product limit |
| 2/π | 2/π ≈ 0.6366 | Average value of |sin| |

### How It Draws

The main visualization plots F(n) vs n as a curve, with:
- The theoretical line (|F_n|−1)/2 + 1/2 in gold
- The deviation Δ(n) = F(n) − theory in teal
- A histogram of |Δ(n)| binned by size to show the growth rate

The ring diagram (same geometry as Farey tab) highlights the fractions in the currently selected sector S_n, letting you see geometrically which angles correspond to a given Farey interval.

---

## 6. Tab 5 — Mod Reduction

**Full title:** Modular Reduction Projection Research Portal  
**What it shows:** The structure of ℤ/Mℤ visualized as a lattice — coprime and non-coprime residues, reduction projections, Euler totient geometry, divisor structure, and multi-modulus comparison. Also includes a 3D Farey Divisor Lattice.

### The Mathematical Object

For M ≥ 2, the ring of integers modulo M:

```
ℤ/Mℤ = {0, 1, 2, …, M−1}
```

splits into:
- **Coprime residues** (ℤ/Mℤ)× = {r : gcd(r,M)=1} — the multiplicative group, |·| = φ(M)
- **Reducible residues** — {r : gcd(r,M) > 1} — zero divisors and nilpotents, count = M−1−φ(M)

### Euler's Totient Formula (drawn)

```
φ(M) = M · ∏_{p|M} (1 − 1/p)
```

For M = p_1^{e_1} · p_2^{e_2} · … · p_k^{e_k}:

```
φ(M) = M · (p_1−1)/p_1 · (p_2−1)/p_2 · … · (p_k−1)/p_k
```

The tool draws a **factor tree** showing how each prime factor reduces the coprime count multiplicatively. Each prime p|M removes the fraction 1/p of residues.

### Reduction Projection

For residue r with gcd(r,M) = d, define:

```
r' = r/d    (reduced residue)
M' = M/d    (reduction modulus)
```

M' is the **reduction target** — r projects down to r' in ℤ/M'ℤ. The tool draws arrows from each reducible residue r to its projection r' on the simplified ring M', forming a **reduction graph**.

For example with M=12:
- r=4: gcd(4,12)=4, r'=1, M'=3 → projects to ring 3
- r=6: gcd(6,12)=6, r'=1, M'=2 → projects to ring 2
- r=8: gcd(8,12)=4, r'=2, M'=3 → projects to ring 3
- r=10: gcd(10,12)=2, r'=5, M'=6 → projects to ring 6

### Farey Channel Breakdown

For each Farey sector S_n = (1/(n+1), 1/n], the tool counts:

```
C_M(n) = |{r ∈ ℤ/Mℤ : r/M ∈ S_n, gcd(r,M)=1}|
```

and compares to the Farey Sector Formula:

```
C_M(n) ≈ φ(M) / (n(n+1))   × (3/π²)^{-1}
```

The bar chart shows how evenly coprime residues distribute across Farey sectors — for prime M they distribute almost uniformly; for highly composite M the distribution is uneven.

### How It Draws

**Single modulus view:** A circle of M points, each colored:
- Blue: gcd(r,M)=1 (coprime, in the multiplicative group)
- Shades of red/orange: gcd(r,M) = d > 1, darker = larger gcd

Reduction arrows from non-coprime r to their projection r' on the inner ring M'.

```javascript
// For each r in {0, …, M−1}:
const d = gcd(r, M);
const theta = 2 * Math.PI * r / M;
const x = cx + R * cos(theta), y = cy - R * sin(theta);
if (d === 1) {
  // coprime: draw blue point
} else {
  // reducible: draw orange point + arrow to (r/d) on ring (M/d)
  const rPrime = r / d, MPrime = M / d;
  const rho2 = radius(MPrime);
  const theta2 = 2 * Math.PI * rPrime / MPrime;
  drawArrow([x,y], [cx + rho2*cos(theta2), cy - rho2*sin(theta2)]);
}
```

**Multi-modulus view:** Side-by-side or overlay comparison of multiple M values. Shows how φ(M)/M varies — prime M gives maximum density; highly composite M gives sparsest coprime set.

**3D Farey Divisor Lattice:** A 3D visualization where:
- x-axis: fraction r/M
- y-axis: 1/M (Farey height)
- z-axis: gcd(r,M) or Ω(M) (prime factor count)

The coprime residues (gcd=1) form the **Stern–Brocot surface** at z=1. Non-coprime residues rise above it proportional to their gcd value.

### Key Statistics Shown

| Stat | Formula | Meaning |
|---|---|---|
| φ(M) | Euler totient | Size of multiplicative group |
| φ(M)/M | Coprime density of M | → 0 for M = primorial |
| Ω(M) | Total prime factors | Additive number theory |
| ω(M) | Distinct prime factors | Combinatorial structure |
| σ(M) | Sum of divisors | Perfect number theory |
| τ(M) | Number of divisors | Dirichlet series coefficient |
| ΔS_M | Modular entropy | −ln(φ(M)/M) |

---

## Mathematical Connections Across All Tabs

```
         ζ(2) = π²/6
              ‖
    ∏_p p²/(p²−1)  = C / d_FT
              ‖
    ∏_g P_g         [Gap ζ(2) tab]
    
    6/π² = lim φ/total  [all tabs]
    C ≈ 0.5307 = lim lift/φ  [main canvas + MLR Viz]
    
    Franel–Landau: RH ⟺ Δ(N) = O(N^{1/2+ε})  [Farey Summatory tab]
    
    Farey adjacency: bc−ad=1 ⟺ Ford circles tangent  [Farey & Circle tab]
    
    φ(M) = M∏(1−1/p) ⟺ coprime density on ring M  [Mod Reduction tab]
```

All five tool tabs and the main canvas visualize different facets of the same arithmetic: **how integers distribute by divisibility**, how that distribution encodes π, ζ(2), and the primes, and how the geometry of the unit circle makes these relationships visible.

---

*References: Feller & Tornier (1932), Franel (1924), Landau (1924), Hardy & Wright §§18–19, Ireland & Rosen Ch. 16, OEIS A065469.*  
*wessengetachew.github.io/MODZ/ · Wessen Getachew · 2026*
