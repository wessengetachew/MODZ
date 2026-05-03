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

**Lower path & Gaussian integers**: r = (M−1)/2 lifts to M+1 iff M ≡ 3 (mod 4). For prime q this is equivalent to q being inert in ℤ[i] — the primes not expressible as a sum of two squares.

**References**: Feller & Tornier (1932); Tóth (2010); OEIS A065469.

---

## Controls

| Control | Default |
|---------|---------|
| M min / M max | 1 / 128 |
| Global rotation | 1/4 × 360° = 90° |
| Point size | 1.5 px |
| Lift lines | on |
| Blocked lines ✗ | on |
| Prime p | 5 |
| Chain n | 0 (off) |

Panel slides up/down on mobile. Pull up strongly when open to expand to 80% screen height.

---

## Running locally

No build step. Single HTML file — open directly in any browser.

```bash
git clone https://github.com/wessengetachew/MODZ
cd MODZ
open index.html
```

Or just visit **[wessengetachew.github.io/MODZ/](https://wessengetachew.github.io/MODZ/)**.

---

*Wessen Getachew · 2026*
