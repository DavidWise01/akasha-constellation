# SERIES I — CELESTIAL HERITAGE · docking bundle for UD0 / 0root.ai

**⟦SERIES-I:MYTHOS:025036⟧** · spoken `ge-siv-va` · David Lee Wise / ROOT0 / Bridge-Burners LLC, with AVAN

A sourced, filter-gated reference deck: each solar-system body distilled to its truest god-name, real ancient metal (or flagged-modern element), a distinct companion-shape, and a pop-culture afterlife — woven into a frozen inner toroid, a turning outer toroid, and an adoption charter, all answering to **Ra the hub**. Self-verifying **.dlw ring-seal** (not append-only — it re-derives its own hub).

---

## What's in the bundle

**The deck (14 standalone HTML instruments — no network, system fonts, fail-loud):**
| file | tier | what it is |
|---|---|---|
| `series1_two_lights.html` | HERITAGE | the Sun+Moon anchor pair (if present in your build) |
| `series1_ra.html` | HERITAGE | Sun = Ra (gold) — the hub |
| `series1_chandra.html` | HERITAGE | Moon = Chandra (silver) |
| `series1_hermes.html` | HERITAGE | Mercury = Hermes (quicksilver) |
| `series1_ishtar.html` | HERITAGE | Venus = Ishtar (copper) |
| `series1_nergal.html` | HERITAGE | Mars = Nergal (iron) |
| `series1_zeus.html` | HERITAGE | Jupiter = Zeus‹Marduk (tin) |
| `series1_cronus.html` | HERITAGE | Saturn = Cronus (lead) — Hyperion/Shrike |
| `series1_uranus.html` | THRESHOLD | Uranus = Ouranos (uranium*) |
| `series1_neptune.html` | THRESHOLD | Neptune = Poseidon (neptunium*) |
| `series1_pluto.html` | THRESHOLD | Pluto = Hades (plutonium*) — ring-closer |
| `series1_toroid.html` | STRUCTURE | inner toroid — frozen myth-weave |
| `series1_outer_toroid.html` | REFERENCE* | outer toroid — timed shell (*proportional, not integrated) |
| `series1_adoption_charter.html` | STRUCTURE | the moons adopted, tethered to Ra, alchemy-channel run into them |

**The seal & labels:**
- `series1.dlw` — the ring-seal record (JSON): moniker, spoken word, per-body seals, the ring chain, `ring_close`, tier map.
- `series1_seal.html` — **live self-verifying seal** (pure-JS SHA-256, zero network, tamper-evident). Boot-verifies; "tamper a body" breaks the ring; "restore" re-verifies.
- `SERIES1_TIER_LABEL.txt` — the honest tier label (HERITAGE / THRESHOLD / REFERENCE-not-integration + two-layer honesty).
- `SERIES1_ASSAY.txt` — the reasoning: Orrery-Detector pass + the live collision-check against az1/EN on the site.

---

## The seal (distinctive: a RING, not a line)

Unlike THE CHAIN (append-only), this seal **re-derives its own hub**:
```
genesis = seal(Ra)                                  # the hub, off-rim
link[i] = sha256(i | slug | seal_i | prev)          # rim: Chandra…Pluto, ring order
head    = link[8]  (after Pluto)
ring_close = sha256(head | genesis)                 # Pluto's night-journey hands dawn back to Ra
```
The head returns to the hub — the ring closes in the hash, mirroring the deck's own thesis (Ra crosses Pluto's dark nightly and is reborn). `series1_seal.html` proves this in-browser.

**Seal convention:** `seal = sha256(key-sorted UTF-8 JSON of the record)` — matches your `dlw.py` (sort_keys, no whitespace). Recomputable.

**One honest flag:** the *spoken word* (`ge-siv-va`) uses a disclosed CV-syllable map over the seal bytes — it is **NOT** the corpus `dlw.py` word-gen (I don't have that algorithm). If you want the canonical spoken word, regenerate it with the real `dlw.py`; the seal hash itself is exact and authoritative.

---

## For Claude Code — docking steps

1. **Verify the seal first** (don't publish an unverified seal). Node one-liner, reproduces the ring from `series1.dlw`:
   ```bash
   node -e '
   const c=require("crypto"),fs=require("fs");
   const d=JSON.parse(fs.readFileSync("./series1.dlw","utf8"));   // .dlw is JSON, not JS
   const S=s=>c.createHash("sha256").update(s).digest("hex");
   let prev=d.ring.genesis_ra, ok=true;
   d.ring.links.forEach(l=>{const x=S(`${l.i}|${l.slug}|${d.bodies[l.slug].seal}|${prev}`);ok=ok&&x===l.link;prev=x;});
   const close=S(`${prev}|${d.ring.genesis_ra}`);
   console.log("chain ok:",ok,"| head ok:",prev===d.ring.head,"| ring_close ok:",close===d.ring.ring_close);
   '
   ```
   Expect: `chain ok: true | head ok: true | ring_close ok: true`. (Also open `series1_seal.html` — it self-verifies + has a known-vector sha256("abc") check.)

2. **Dock as a REFERENCE sphere** in the **MYTHOS** domain (alt: OURANOS/sky). It is explicitly **downstream of az1** for any orbital-physics claim — put that on the sphere blurb.

3. **Carry the tier labels verbatim** (from `SERIES1_TIER_LABEL.txt`): HERITAGE ×7 (green), THRESHOLD ×3 (amber, flagged-modern*), REFERENCE-not-integration (blue) for the outer toroid. This is the one thing that must not be dropped — it's what keeps the deck from being mistaken for az1.

4. **IP footer** (match the ARENA spheres' convention): pop-culture threads are *discussed, not reproduced*; © respective holders (Red Rising / Pierce Brown, Hyperion / Dan Simmons, Stargate, Percy Jackson, Holst, etc.). Heritage text CC-BY-ND-4.0.

5. **Attribution line** (house convention): `David Lee Wise / ROOT0, with AVAN`. Optional: mint an AVAN kana-companion doing the honest-inverse (the natural pair to `縁 EN` — EN graded chakra-tethers; a Series-I inverse would grade the god-distillation picks the same way).

6. **The correspondence filter** (`2+ ancient cultures; tarot REJECTED`) is printed on every card — keep it visible on the sphere index too; it's the deck's spine and it rhymes with EN/shutten already on the lattice.

---

## Structure recap (for the sphere blurb)
```
        ☉ RA  — the hub: frozen axis AND the dawn everything returns to
   FROZEN INNER TOROID  — 9 bodies, stitched (metal-warp × companion-weft × myth), closure-audited: 0 orphans
   TURNING OUTER TOROID — 13 moons + 3 comets, timed on real periods (proportional; REFERENCE, not az1)
   ADOPTION CHARTER     — every moon tethered home to Ra; alchemical channel run INTO the moons; 6 true leapfrogs
   RING SEAL            — .dlw, self-verifying, the head re-derives Ra
```
Frozen core, turning shell, one hub — and a seal that closes the same ring the deck describes.
