# 🔬 Tool Diagnostico Lesioni Basaloidi - v15.1 Fixed

Evidence-based tool interattivo per la diagnosi differenziale di lesioni basaloidi cutanee.

## [🚀 Prova il tool](https://infingardo.github.io/basaloid-diagnostic-tool/)

## ✨ Novità v15.1 - CRITICAL FIXES

### 🚨 **Logica diagnostica MAC vs Eccrine - CORRETTA**
- **Fix principale:** Discriminazione CK7+/Ber-EP4− basata su **presenza/assenza di duttali morfologici**
- MAC = CK7+/Ber-EP4− **SENZA duttali visibili** + infiltrazione profonda
- Eccrine = CK7+/CEA+ **CON duttali chiari** (Poroma/Spiroadenoma/Siringoma)
- **Tabella comparativa aggiornata:** Aggiunta colonna MAC con discriminanti critici

### 📊 **Enhanced Flowchart**
- SVG logic tree ora distingue correttamente il branch "NO duttali → MAC candidate"
- Feedback immediato: se CK7+ Ber-EP4− senza duttali = rosso alert

### 🧪 **IHC Analysis Script - Intelligenza Aumentata**
- Nuovi pattern recognition per MAC:
  - `ck7 && !berep4 && !cea && p63` → MAC alert (alta specificità)
  - `ck7 && cea && !berep4 && p63` → decision tree duttali (chiede verifica morfologia)
- Output contest-aware: MAC vs eccrina vs BCC

### 📋 **Tabella DD Espansa**
Ora include MAC con profilo IHC completo:
- Ber-EP4− (discrimina da BCC)
- CK7+ diffuso (non è BCC)
- Assenza duttali (non è eccrina classica)
- Invasione perineurale 50-80% (chiave di lettura)
- Stroma desmoplastico (feature morfologica)

### 🚨 **MAC Section Ricostruita**
- Enfasi su "doppio livello" morfologico (superficiale innocente vs profondo aggressivo)
- Pitfalls specifici per MAC
- Richiesta esplicita S100 per perineurale (50-80% dei casi)
- Management Mohs surgery con recidiva 40-60% se margini < 10mm
- Bibliografia MAC ampliata: 4 ref + Zalla et al. Mohs data

## Features

✅ **Flowchart diagnostico interattivo (v2)** - algoritmo decisionale corretto per MAC  
✅ **Analisi morfologica H&E** - scoring automatico  
✅ **Panel IHC completato** - diagnosi differenziale BCC, tricoblastoma, eccrine, MAC  
✅ **9 varianti BCC** - margini chirurgici, rischio recidiva, indicazioni Mohs  
✅ **DD lesioni eccrine** - poroma, idroadenoma, spiroadenoma, siringoma  
✅ **Carcinoma annessiale microcistico (MAC)** - morfologia, IHC, gestione aggressiva  
✅ **Tabella comparativa 6-entity** - BCC, 4 eccrine, MAC con profilo completo  
✅ **Bibliografia evidence-based** - 22 references aggiornate 2025  

## Uso

Tool progettato per supporto alla refertazione dermatopatologica.  
**Non sostituisce il giudizio clinico e la correlazione morfologica.**

## Tecnologie

- HTML5 + CSS3 + Vanilla JavaScript
- SVG embedded per flowchart v2
- Zero dipendenze esterne
- Mobile responsive

## Note Cliniche Critiche

**MAC è il "lupo travestito da agnello":**
- Morfologia superficiale innocente (siringoma-like)
- Infiltrazione profonda silente
- Assenza duttali ben definiti
- Cellularità bassa, mitosi rare → false reassurance
- **Ricadute 40-60% se Mohs inadeguato**

**La chiave diagnostica resta:**
1. Ber-EP4 negativo (non è BCC)
2. Assenza duttali chiari (non è eccrina)
3. CK7+ diffuso (differenziazione eccrina anomala)
4. Infiltrazione profonda + desmoplasia
5. **S100 essenziale** per perineurale

## Licenza

MIT License - uso educazionale

## Autore

[@Infingardo](https://github.com/Infingardo)

---

### Changelog v15.1
- ✏️ Flowchart: fix logica MAC vs eccrine
- 🧪 IHC script: pattern recognition MAC
- 📊 Tabella: colonna MAC aggiunta
- 🚨 MAC section: expanded 3x
- 📚 Bibliography: +2 ref MAC (Zalla Mohs data)
