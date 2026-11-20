# Jak funguje WebUI pro umělou inteligenci

Když dnes používáš ChatGPT, Copilot, Claude nebo lokální modely jako Llama či Mistral, většinou s nimi komunikuješ prostřednictvím takzvaného **WebUI** (Web User Interface). Jde o webové rozhraní, které slouží jako prostředník mezi uživatelem a samotným AI modelem.

Tento článek vysvětluje jednotlivé části WebUI tak, aby jim porozuměl i středoškolák bez hlubších znalostí programování.

## Co je vlastně WebUI?

WebUI si můžeš představit jako **ovládací panel AI**.

Samotná umělá inteligence běží někde na serveru nebo ve tvém počítači. WebUI je pouze prostředí, přes které s ní komunikuješ.

### Jednoduchá analogie

| Součást auta | Součást AI systému |
|-------------|-------------------|
| Volant | WebUI |
| Motor | AI model |
| Palubní deska | Nastavení modelu |
| Řidič | Uživatel |

Stejně jako volant neobsahuje motor, ani WebUI není samotná umělá inteligence.

---

# 1. Textové pole (Prompt Box)

Nejdůležitější součást každého WebUI.

Sem zadáváš své požadavky:

```text
Napiš článek o českých hradech.
```

nebo

```text
Přelož tento text do angličtiny.
```

nebo

```text
Vytvoř obrázek kosmické lodi.
```

Po stisknutí klávesy Enter se tvůj požadavek odešle AI modelu.

### Co se děje na pozadí?

```text
Tvůj text
      ↓
WebUI
      ↓
AI model
      ↓
Odpověď
      ↓
Zobrazení v chatu
```

---

# 2. Chatové okno

Chatové okno uchovává historii konverzace.

Například:

**Ty**

> Co je fotosyntéza?

**AI**

> Fotosyntéza je proces...

**Ty**

> Vysvětli to jednodušeji.

AI ví, že stále mluvíte o fotosyntéze, protože vidí předchozí zprávy.

Této historii se říká **kontext**.

---

# 3. Systémový prompt

Běžný uživatel jej většinou nevidí.

Obsahuje instrukce typu:

```text
Odpovídej česky.
```

```text
Chovej se jako učitel.
```

```text
Pomáhej s programováním.
```

Tato pravidla určují chování modelu ještě předtím, než napíšeš první zprávu.

---

# 4. AI model

Model je skutečný „mozek“ celého systému.

Mezi nejznámější patří:

- GPT
- Claude
- Gemini
- Llama
- Qwen
- Mistral
- DeepSeek

Model provádí veškerou práci:

- analyzuje otázku,
- hledá souvislosti,
- vytváří odpověď.

WebUI pouze zobrazuje výsledky.

---

# 5. Nastavení generování

Mnohá WebUI umožňují měnit chování modelu pomocí různých parametrů.

## Temperature

Temperature určuje míru kreativity.

### Nízká teplota

```text
0.1
```

Výsledky:

- přesnější
- konzistentnější
- méně kreativní

Používá se například pro:

- matematiku,
- programování,
- technické texty.

### Vysoká teplota

```text
1.2
```

Výsledky:

- kreativnější
- méně předvídatelné
- více fantazie

Používá se například pro:

- povídky,
- brainstorming,
- tvorbu postav.

---

## Max Tokens

Určuje maximální délku odpovědi.

Například:

| Hodnota | Výsledek |
|----------|----------|
| 100 | krátká odpověď |
| 1000 | delší vysvětlení |
| 4000 | velmi rozsáhlý text |

Token není totéž co slovo.

Přibližně platí:

```text
1 token ≈ 0,75 slova
```

---

## Top-p

Další parametr ovlivňující kreativitu.

Laicky řečeno:

> Určuje, z kolika možných variant smí model vybírat.

Nízké hodnoty:

- konzervativní odpovědi

Vyšší hodnoty:

- pestřejší odpovědi

---

# 6. Kontextové okno

Kontextové okno představuje pracovní paměť modelu.

Obsahuje:

- předchozí zprávy,
- připojené soubory,
- systémové instrukce.

Moderní modely si dokážou pamatovat:

- tisíce,
- desetitisíce,
- někdy i statisíce tokenů.

Když je konverzace příliš dlouhá, nejstarší informace postupně vypadávají.

Podobně jako člověk nedokáže držet v hlavě nekonečné množství informací najednou.

---

# 7. Historie chatů

Většina WebUI ukládá staré konverzace.

Typicky v levém panelu vidíš:

```text
Pomoc s Pythonem
Překlad kapitoly
Návrh prezentace
Příprava na zkoušku
```

Díky tomu můžeš:

- pokračovat v rozdělané práci,
- vracet se ke starším odpovědím,
- hledat staré informace.

---

# 8. Nahrávání souborů

Moderní WebUI umožňují přikládat soubory.

Například:

- PDF
- DOCX
- XLSX
- TXT
- PNG
- JPG

Poté můžeš napsat:

> Shrň tento dokument.

nebo

> Najdi v PDF všechny termíny odevzdání.

---

## Jak to funguje?

```text
Soubor
   ↓
WebUI
   ↓
Zpracování obsahu
   ↓
AI model
   ↓
Odpověď
```

---

# 9. RAG (Retrieval Augmented Generation)

Tato technologie umožňuje AI pracovat s externími dokumenty.

Bez RAG:

```text
Otázka
   ↓
Model
   ↓
Odpověď
```

S RAG:

```text
Otázka
   ↓
Vyhledání relevantních dokumentů
   ↓
Model
   ↓
Odpověď
```

---

## Praktický příklad

Firma má dokumentaci o 10 000 stranách.

Zaměstnanec se zeptá:

> Jak funguje modul fakturace?

Systém:

1. Najde relevantní stránky.
2. Přidá je do promptu.
3. Odešle je modelu.
4. Model odpoví.

Právě díky RAG dnes funguje většina firemních chatbotů.

---

# 10. Embedding model

Aby bylo možné vyhledávat podle významu, používají se embeddingy.

Embedding převádí text na dlouhý seznam čísel.

Například:

```text
Kočka
↓
[0.12, -0.55, 0.83, ...]
```

Počítač potom může porovnávat podobnost významů.

Díky tomu pochopí, že:

- kočka,
- kocour,
- kotě

jsou významově blízko.

---

# 11. Vektorová databáze

Embeddingy se ukládají do speciální databáze.

Často se používají:

- FAISS
- Chroma
- Qdrant
- Milvus

Jejich úkolem je velmi rychle najít podobné dokumenty.

Pokud zadáš:

> Fakturace zákazníků

databáze najde texty, které se fakturace týkají, i když neobsahují přesně stejná slova.

---

# 12. Nástroje (Tool Calling)

Moderní AI už nemusí spoléhat pouze na vlastní znalosti.

Může používat nástroje.

Například:

- webové vyhledávání,
- kalkulačku,
- Python,
- generátor obrázků,
- databáze,
- e-mailové systémy.

---

## Příklad

Uživatel:

> Jaké bude zítra počasí?

AI:

```text
1. Rozpozná potřebu aktuálních dat
            ↓
2. Zavolá nástroj pro počasí
            ↓
3. Získá informace
            ↓
4. Vytvoří odpověď
```

Stejným způsobem může řešit složitější úlohy.

---

# 13. Typický průběh práce

Představ si následující požadavek:

> Shrň mi PDF a vytvoř prezentaci.

Systém obvykle provede:

```text
1. Načtení PDF
            ↓
2. Rozdělení textu na části
            ↓
3. Analýza obsahu
            ↓
4. Vytvoření shrnutí
            ↓
5. Návrh snímků
            ↓
6. Vygenerování prezentace
            ↓
7. Nabídnutí souboru ke stažení
```

---

# Celková architektura systému

```text
             Uživatel
                 │
                 ▼
        ┌────────────────┐
        │     WebUI      │
        └────────────────┘
                 │
                 ▼
        ┌────────────────┐
        │   AI Model     │
        └────────────────┘
                 │
      ┌──────────┼──────────┐
      ▼          ▼          ▼
   Soubory    Nástroje     RAG
      │          │          │
      └──────────┴──────────┘
                 │
                 ▼
             Odpověď
```

# Závěr

WebUI není samotná umělá inteligence. Je to prostředí, které umožňuje pohodlně komunikovat s AI modely, pracovat se soubory, vyhledávat informace a využívat různé nástroje.

Pro středoškoláka může být nejjednodušší představa následující:

- **WebUI je kokpit letadla.**
- **AI model je motor.**
- **RAG je knihovník.**
- **Nástroje jsou specializovaní pomocníci.**
- **Kontextové okno je krátkodobá paměť.**

Teprve společně vytvářejí systém, který dnes označujeme jako moderní AI asistenty.