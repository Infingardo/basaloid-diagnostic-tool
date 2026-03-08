# Tool Diagnostico Lesioni Basaloidi — v16.1

**Autore:** Dr. Filippo Bianchi  
**Unità:** SC Anatomia Patologica — ASST Fatebenefratelli-Sacco, Milano  
**Versione:** 16.1 | **Anno:** 2026  
**Stack:** HTML5 + CSS + JavaScript puro — standalone, nessuna dipendenza esterna

---

## Cosa fa

Tool diagnostico interattivo per lesioni basaloidi cutanee. Supporta:

- **Morfologia** — punteggio pesato (palizzata, retrazione, basaloide, distacco artefattuale)
- **IHC** — Ber-EP4, CK7, CEA, p63, p40, EMA, S100, Bcl-2, CD10, CD34, CK5/6, CK20, sinaptofisina, organo-specifici
- **DD** — BCC (tutte le varianti), MAC, lesioni eccrine/poromatose, trichoepithelioma, metastasi, Merkel, SCC basaloide
- **Varianti BCC** — nodulare, superficiale, morfeiforme/sclerosante, infiltrativo, micronodulare, nodulare-cistico, basosquamoso, pigmentato
- **Alert clinici** — zona H, biopsia superficiale, immunosoppressione, recidiva
- **Sezione MAC dedicata** — checkbox morfologiche, safeguard campioni superficiali

---

## Logica algoritmica (motore JS)

### Gerarchia rami IHC (in ordine)

1. **Sebaceo** — EMA diffuso + p40 +/−
2. **Metastasi** — organo-specifici (TTF1, CDX2, GATA3)
3. **Merkel** — CK20 dot-like + MCV (CM2B4), sinaptofisina, cromogranina
4. **Pattern ibrido** — Ber-EP4+/CK7+ (DD annessiale/BCC con differenziazione)
5. **Blocco superficiale MAC** — Ber-EP4− con CK7+ e/o ≥2 criteri morfologici MAC su punch superficiale → richiede escissione profonda
6. **RAMO 1 — Eccrino franco** — `CK7+ && CEA+ && Ber-EP4− && hasMACMorph < 2`
7. **RAMO 2 — MAC candidato** — `Ber-EP4− && hasMACMorph ≥ 2` (CK7 è supporto, non grilletto)
8. **RAMO 3 — Indeterminato** — `Ber-EP4− && CK7+ && hasMACMorph < 2` (senza CEA)
9. **BCC classico** — Ber-EP4 diffuso + p63 + CK7−
10. **Ber-EP4 focale** — DD trichoepithelioma vs BCC infiltrativo
11. **Stroma CD10/CD34** — lesione follicolare
12. **Basosquamoso** — p40+ nelle aree squamoidi + EMA focale
13. **Default** — pannello non conclusivo

### Punteggio morfologico

| Feature | Punti |
|---|---|
| Palizzata periferica | +3 |
| Retrazione stromale (solo con palizzata) | +2 |
| Cellule basaloidi | +2 |
| Distacco artefattuale | +2 |
| **Totale** | **/9** |

≥6 = BCC-like alta probabilità; 3–5 = indeterminato; <3 = non BCC-like

### Soglia morfologica MAC

`hasMACMorph = macMorphScore >= 2` (almeno 2 tra: infiltrazione profonda, desmoplasia, microcisti, perineurale, assenza duttali ben definiti)

---

## Principi diagnostici implementati

- **Morfologia-first**: il vetrino guida, l'IHC supporta
- **CK7 accessorio in MAC**: Hoang et al. — CK7 nel 15% dei MAC vs 40% BCC infiltrativi; non è un criterio d'ingresso
- **CEA focale non esclude MAC**: la CEA può essere positiva nelle strutture duttali di MAC
- **Ber-EP4 non assoluto**: pattern diffuso fortemente orientante per BCC, ma non patognomonico; positività focale compatibile con tumori annessiali (siringoma condroide, porocarcinoma, spiroadenoma)
- **Safeguard superficiali**: qualunque profilo Ber-EP4−/sospetto su punch superficiale → blocco con richiesta escissione profonda
- **MCV in Merkel**: CM2B4 (IHC, LT-antigen nucleare); MCV+ ~80%, prognosi migliore; MCV− UV-driven, maggiore aggressività

---

## Riferimenti principali

- **NCCN Guidelines BCC** — Version 1.2026
- **Hoang MP et al.** — CK7/Ber-EP4 in MAC vs BCC infiltrativo. *Am J Surg Pathol* 2011
- **Afshar M et al.** — Ber-EP4 nei tumori del sweat apparatus. *J Cutan Pathol* 2022
- **WHO Classification of Skin Tumours** — 5th ed., 2023
- **Feng H et al.** — Clonal integration of MCC polyomavirus. *Science* 2008 — MCV discovery
- **Nghiem P et al.** — Pembrolizumab in MCC. *NEJM* 2016

---

## Deployment

GitHub Pages: `https://infingardo.github.io/`  
File: `index.html` (standalone, copiare direttamente)

---

## Disclaimer

Tool di supporto alla diagnosi. Non sostituisce il giudizio del patologo. Tutte le diagnosi richiedono correlazione clinico-morfologica. Vedi disclaimer interno al tool.
