# 🔬 Tool Diagnostico Lesioni Basaloidi - v15.4.1

Evidence-based tool interattivo per la diagnosi differenziale di lesioni basaloidi cutanee.

## [🚀 Prova il tool](https://infingardo.github.io/basaloid-diagnostic-tool/)

---

## ✨ Novità v15.4.1 (2026)

### 🧠 Logica diagnostica refactored

- **Flowchart v4:** Gate iniziale cambiato da "Retrazione stromale?" a **"Pattern BCC-like? (palizzata + retrazione/clefting)"** — più robusto su campioni con processing variabile
- **BCC da "diagnostico" a "fortemente suggestivo"** — con alert per DD trichoepithelioma se lesione piccola/simmetrica
- **Tricoblastoma:** logica più flessibile, nota su variabilità Ber-EP4 (può essere focale+)
- **MAC safeguard:** non concludere su punch superficiale — richiede infiltrazione profonda + desmoplasia

### 📋 Sezione INPUT CLINICO (nuova)

Campi obbligatori per accuratezza:
- Sede anatomica (zona H, palmo/pianta, tronco...)
- Tipo biopsia (punch superficiale, escissionale...)
- Recidiva sì/no
- Immunosoppressione sì/no

Alert dinamici contestuali basati sull'input.

### 🧪 Panel IHC esteso

**Nuovi marker:**
- CK5/6 (squamoide/basaloide)
- Adipofilina (sebaceo — molto più specifico di AR)
- GATA3 (mammella/uroteliale)
- TTF1 (polmone/tiroide)
- CDX2 (GI)

**Logica AR migliorata:**
- AR+ con Ber-EP4+ → "Non conclusivo per sebaceo (BCC è AR+ nel 50-70%)"
- AR+ senza Ber-EP4 → "Sospetto sebaceo, confermare con adipofilina"
- Adipofilina+ → "Carcinoma sebaceo probabile"

### 🔴 DD critiche aggiunte

**MAC vs BCC Micronodulare** — tabella comparativa dedicata:

| Feature | BCC Micronodulare | MAC |
|---------|-------------------|-----|
| Ber-EP4 | ✓✓ POSITIVO | NEGATIVO |
| Palizzata | Presente | Assente |
| CK7 | Negativo | ✓✓ POSITIVO |
| Microcisti cheratiniche | No | Sì |
| Perineurale | Rara | ~50-70% |

**Carcinoma sebaceo, metastasi cutanee, basosquamoso** — corner cases con panel IHC dedicati.

### ⚠️ Warning contestuali

Micro-label di safety nei punti critici:
- Morfologia: "Score non applicabile su biopsie tangenziali/superficiali"
- MAC: "Se punch superficiale, sospendere giudizio definitivo"
- Eccrine: "Correlare con sede anatomica"
- CK20/Merkel: "Altamente suggestivo" (non diagnostico) + caveat su Merkel CK20−

### 🐛 Bug fix

- Rimosso `DOMContentLoaded` toggle che richiudeva flowchart già attivo
- Pattern ibrido Ber-EP4+/CK7+ ora gestito (segnala combinazione insolita)

---

## Features complete

✅ **Flowchart diagnostico v4** — logica "pattern BCC-like" come gate iniziale  
✅ **Input clinico obbligatorio** — sede, biopsia, recidiva, immunosoppressione  
✅ **Analisi morfologica H&E** — scoring BCC-likeness (non "BCC")  
✅ **Panel IHC esteso** — 16 marker con logica decisionale  
✅ **10 varianti BCC** — incluso basosquamoso, con margini e indicazioni Mohs  
✅ **DD lesioni eccrine** — poroma, idroadenoma, spiroadenoma, siringoma  
✅ **MAC section** — morfologia, IHC, pitfalls, gestione aggressiva  
✅ **DD MAC vs BCC micronodulare** — tabella comparativa  
✅ **Carcinoma sebaceo** — logica AR vs adipofilina  
✅ **Metastasi cutanee** — GATA3, TTF1, CDX2  
✅ **Bibliografia evidence-based** — 22 references con DOI+PMID cliccabili  

---

## Tecnologie

- HTML5 + CSS3 + Vanilla JavaScript
- SVG embedded per flowchart v4
- Zero dipendenze esterne
- Mobile responsive

---

## Note Cliniche Critiche

### MAC — "Il lupo travestito da agnello"
- Morfologia superficiale innocente (siringoma-like)
- Infiltrazione profonda silente
- Assenza duttali **ben definiti** (pseudo-duttali possibili ma incompleti)
- Cellularità bassa, mitosi rare → false reassurance
- **Recidive 40-60% se margini inadeguati**
- **NON diagnosticare su punch superficiale!**

### La chiave diagnostica
1. Ber-EP4+ diffuso = BCC (ma DD trichoepithelioma se piccolo/simmetrico)
2. Ber-EP4− + CK7+ + no duttali ben definiti + infiltrazione = MAC
3. Ber-EP4− + stroma CD10/CD34+ + simmetria = follicolare
4. AR+ da solo NON basta per sebaceo (richiedere adipofilina)
5. **S100 sempre per perineurale in sospetto MAC**

### DD MAC vs BCC micronodulare
Entrambi hanno nidi piccoli infiltranti — **Ber-EP4 + CK7 panel obbligatorio!**

---

## Changelog

### v15.4.1 (2026-01-01)
- 🔧 DD MAC vs BCC micronodulare con tabella comparativa
- 🔧 Logica AR: da solo non conclusivo per sebaceo, richiede adipofilina
- 🔧 Corner cases sebaceo: nota su AR+ nel 50-70% dei BCC
- 📅 Anno corretto a 2026

### v15.4 (2026)
- 🔄 Flowchart v4: gate iniziale "Pattern BCC-like" invece di "Retrazione"
- 📋 Sezione INPUT CLINICO con alert dinamici
- 🧪 Nuovi marker: CK5/6, Adipofilina, GATA3, TTF1, CDX2
- ✏️ BCC da "diagnostico" a "fortemente suggestivo"
- ⚠️ Tricoblastoma: logica più flessibile + nota variabilità Ber-EP4
- ⚠️ MAC safeguard su punch superficiale
- 🔀 Pattern ibrido Ber-EP4+/CK7+ gestito
- 🐛 Fix bug DOMContentLoaded

### v15.3.1 (2026)
- ⚠️ Warning contestuali: morfologia, MAC, eccrine
- ✏️ CK20/Merkel: "altamente suggestivo" + caveat CK20−/TTF1−

### v15.3 (2026)
- 📊 Flowchart v3: ramo "IHC non conclusivo"
- ➕ Carcinoma basosquamoso nelle varianti
- 🧪 p40 integrato nell'algoritmo
- ✏️ Morfologia: wording "BCC-likeness"
- ✏️ MAC: "assenza duttali ben definiti" + nota pseudo-duttali
- 📚 Corner cases: sebaceo, metastasi, Merkel

### v15.2 (2025)
- 📚 Bibliografia: 22 referenze con DOI + PMID cliccabili
- 🎨 CSS enhanced per link bibliografia

---

## Uso

Tool progettato per supporto alla refertazione dermatopatologica.  
**Non sostituisce il giudizio clinico e la correlazione morfologica.**

⚠️ Score morfologico = operativo, non formalmente validato.  
⚠️ Compilare sempre INPUT CLINICO per accuratezza.

---

## Licenza

MIT License - uso educazionale

## Autore

[@Infingardo](https://github.com/Infingardo)

---

**Powered by evidence-based medicine ⭐ | Buon 2026! 🎉**
