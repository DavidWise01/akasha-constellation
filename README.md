# AKASHA — THE CONSTELLATION

**⟦AKASHA:CONSTELLATION:F64291⟧** · hub **ROOT0** · a **seal of seals**
David Lee Wise / ROOT0 / Bridge-Burners LLC, with AVAN · 2026

Three mythos-decks, each built the same way — take a body or a book, distill its truest
figures, build one honest instrument per figure (measurement first, fail-loud, verify-then-ship,
every claim tiered **LIT** / **AMBER**), and fold the deck into a cryptographic ring-seal that
closes back on its own hub. **The three ring-seals are themselves folded into one super-ring that
answers to ROOT0.** Nothing here asks to be believed; everything here can be **re-checked**.

**Live:** open `index.html` (the front door) and `constellation_seal.html` (the seal of seals,
self-verifying in-browser).

---

## The three seeds — make · unmake · harmony

| seed | pole | channel | moniker | deck |
|---|---|---|---|---|
| ☉ **RA** — the giver | make | metal | `SERIES-I:MYTHOS:025036` | [Celestial Heritage](https://davidwise01.github.io/series-1-celestial-heritage/) |
| ☽ **ERIS** — the breaker | unmake | ice | `SERIES-II:MYTHOS:8AB003` | [The Scattered Field](https://davidwise01.github.io/series-2-scattered-field/) |
| ☾ **NEMESIS** — the reckoner | harmony | shadow | `SERIES-III:MYTHOS:4B5483` | [The Shadow](https://davidwise01.github.io/series-3-the-shadow/) |

**The figure** (flagged interpretive): the three seeds mirror the **make / harmony / unmake**
ternary of Icarium — the ternary that ran inside a single sleeper-orrery, now running across the
whole corpus. RA gives; ERIS breaks; NEMESIS reckons (retribution as the restoring force). Nemesis
wears both the shadow and the balance — the deeper pole is the reckoning. *The pole-mapping is a
reading, not a measurement, and is marked as such.*

Each deck is browsable locally here (`series1_*.html`, `series2_*.html`, `series3_*.html`) and
lives in full — with its own self-verifying landing — at the linked repos.

---

## The seal — a RING of rings

```
seed[i]    = sha256("idx|HUB|pole|moniker|closure")
chain[i]   = sha256(chain[i-1] | seed[i])       # folds from genesis (ROOT0)
head       = chain[-1]
ring_close = sha256(head | genesis)             # closes back to ROOT0  →  F64291…
```

Series II (8AB003) and III (4B5483) are bound by their **full ring-closes**; Series I is bound by
its **published moniker** 025036 — the constellation seals *what is published* about each seed,
which is exactly what a seal-of-seals should do. Honestly flagged in `constellation.dlw`.

**Verify offline** (Node — reproduces the super-ring from `constellation.dlw`):

```bash
node -e '
const c=require("crypto"),fs=require("fs");
const d=JSON.parse(fs.readFileSync("./constellation.dlw","utf8"));
const S=s=>c.createHash("sha256").update(s).digest("hex");
let acc=d.genesis, ok=true;
d.seeds.forEach(s=>{const seal=S(s.record); ok=ok&&seal===s.seal; acc=S(acc+"|"+seal);});
console.log("seeds ok:",ok,"| head ok:",acc===d.head,"| ring_close ok:",S(acc+"|"+d.genesis)===d.ring_close);
'
# → seeds ok: true | head ok: true | ring_close ok: true
```

Every `*_seal.html` recomputes its SHA-256 chain in your browser from an embedded pure-JS
implementation — **zero-network, tamper-evident**. Open one, hit the tamper button, and watch a
single flipped byte break the ring. The `.dlw` files are plain JSON. **The seal is the argument.**

---

Fully static, offline, no build step. Series sources & licenses travel with each deck
(Asimov's *Nemesis* (1989) discussed-not-reproduced, © the Asimov estate; heritage text
CC-BY-ND-4.0). Attribution: **David Lee Wise / ROOT0 / Bridge-Burners LLC, with AVAN**.
