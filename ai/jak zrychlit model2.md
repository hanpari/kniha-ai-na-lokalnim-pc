# Proč AI někdy odpovídá za 1 sekundu a jindy za minutu?

Když položíš otázku modelu, proběhne několik kroků:

```text

Otázka

&#x20;↓

Příprava promptu

&#x20;↓

Načtení modelu

&#x20;↓

Zpracování kontextu

&#x20;↓

Případné použití RAG

&#x20;↓

Generování tokenů

&#x20;↓

Odpověď

```

Zdržení může vzniknout prakticky v každém kroku.

---

# Situace 1: Model se teprve načítá do paměti

## Jak to poznáš

Po první otázce:

```text

20-60 sekund nic

```

Pak se náhle objeví odpověď.

Další dotazy už jsou rychlé.

---

## Co se děje

Model je uložen na disku:

```text

Qwen3 14B

≈ 9 GB

```

Při prvním použití se musí:

```text

Disk

&#x20;↓

RAM

&#x20;↓

GPU

```

načíst celý model.

---

## Příklad

Začneš den.

Napíšeš:

```text

Ahoj.

```

Čekáš:

```text

25 sekund

```

Potom:

```text

Jak funguje SQL?

```

a odpověď přijde za:

```text

2 sekundy

```

---

## Řešení

V Ollamě nastav:

```text

keep alive

```

nebo pravidelně model používej.

Například:

```bash

OLLAMA_KEEP_ALIVE=24h

```

Model zůstane v RAM.

---

# Situace 2: Model běží na CPU místo GPU

## Jak to poznáš

Odpověď se generuje takto:

```text

jedno slovo...

pauza...

další slovo...

pauza...

```

---

## Příklad

Otázka:

```text

Vysvětli teorii relativity.

```

Výstup:

```text

Tok:

3 tokeny/s

```

---

## Co se děje

CPU má například:

```text

20 jader

```

GPU má:

```text

5000+

výpočetních jednotek

```

AI je navržena především pro GPU.

---

## Kontrola

```bash

ollama ps

```

Výstup:

```text

PROCESSOR

100% CPU

```

---

## Řešení

- aktualizovat NVIDIA ovladače

- restartovat Ollamu

- používat menší model

- zajistit, aby se celý model vešel do VRAM

---

# Situace 3: Model se nevejde do VRAM

Nejčastější problém domácích sestav.

---

## Příklad

Máš:

```text

RTX 3060

12 GB VRAM

```

spustíš:

```text

Qwen3 32B

```

---

## Co se děje

GPU vezme:

```text

12 GB

```

zbytek uloží do RAM:

```text

20 GB

```

Při každém tokenu se přenášejí data.

---

## Výsledek

Odpověď:

```text

5× až 20× pomalejší

```

---

## Řešení

Místo:

```text

32B

```

použij:

```text

14B

```

nebo

```text

8B

```

které se celé vejdou do VRAM.

---

# Situace 4: Thinking / Reasoning model

Typické pro:

```text

DeepSeek-R1

QwQ

o1-like modely

```

---

## Jak to poznáš

Dlouho se nic neděje.

Například:

```text

20 sekund ticho

```

Potom model začne odpovídat.

---

## Co se děje

Model interně vytváří:

```text

úvahu

kroky řešení

analýzu

```

Teprve potom odpovídá.

---

## Příklad

Otázka:

```text

Vyřeš složitý matematický důkaz.

```

---

Běžný model:

```text

odpoví za 3 s

```

---

Reasoning model:

```text

15 s přemýšlí

5 s odpovídá

```

---

## Řešení

Používej:

```text

Qwen Instruct

Llama Instruct

Mistral Instruct

```

když nepotřebuješ uvažování krok za krokem.

---

# Situace 5: Obrovská historie konverzace

## Jak to poznáš

Každá další otázka je pomalejší.

---

## Příklad

Po 100 zprávách:

```text

Jak se jmenuje hlavní město Francie?

```

trvá déle než na začátku chatu.

---

## Co se děje

Model musí před odpovědí přečíst:

```text

všechny předchozí zprávy

```

---

## Schéma

```text

100 tokenů historie

&#x20;↓

rychlé



5000 tokenů historie

&#x20;↓

pomalejší



30000 tokenů historie

&#x20;↓

výrazně pomalejší

```

---

## Řešení

Začni nový chat.

Nebo sniž:

```text

Context Length



32768

↓

8192

```

---

# Situace 6: Příliš rozsáhlý RAG

Velmi časté v Open WebUI.

---

## Jak to poznáš

Před odpovědí:

```text

10-30 sekund nic

```

---

## Co se děje

Dotaz:

```text

Jak funguje reklamace?

```

RAG připojí:

```text

40 stran dokumentace.

```

---

Model musí vše přečíst.

---

## Řešení

Sniž:

```text

Top K



10

↓

3

```

a velikost chunků.

---

# Situace 7: Příliš dlouhý system prompt

## Špatný příklad

Agent má:

```text

5000 řádků pravidel

```

---

Při každém dotazu model čte:

```text

pravidla

+

historii

+

otázku

```

---

## Řešení

Místo:

```text

20 stran instrukcí

```

vytvoř:

```text

10-20 jasných pravidel

```

---

# Situace 8: Příliš dlouhá odpověď

## Příklad

Napíšeš:

```text

Popiš historii lidstva.

```

---

Model generuje:

```text

3000 tokenů

```

---

I rychlý model potřebuje čas.

---

## Řešení

Do promptu:

```text

Shrň ve 3 odstavcích.

```

nebo

```text

Odpověz stručně.

```

---

# Situace 9: Současně běží více modelů

## Příklad

Máš spuštěno:

```text

Qwen

FLUX

XTTS

Embedding model

```

najednou.

---

VRAM se rozdělí.

---

## Důsledek

Každý model zpomalí.

---

## Řešení

```bash

ollama stop

```

nepoužívaných modelů.

---

# Situace 10: Pomalý disk

Nejčastěji u HDD.

---

## Projev

První spuštění modelu trvá dlouho.

---

## Příklad

```text

Qwen 14B



SSD:

10 sekund



HDD:

40 sekund

```

---

## Řešení

Přesunout modely na:

```text

NVMe SSD

```

---

# Jak diagnostikovat problém za 2 minuty

## Krok 1

```bash

ollama ps

```

---

Pokud vidíš:

```text

100% CPU

```

→ problém je GPU.

---

## Krok 2

Změř rychlost generování.

Pokud máš:

```text

2-5 tokenů/s

```

→ model je příliš velký.

---

## Krok 3

Otevři nový chat bez RAG.

Pokud je najednou rychlý:

```text

problém je RAG nebo kontext

```

---

## Krok 4

Vyzkoušej menší model.

Například:

```text

Qwen3 14B

↓

Qwen3 8B

```

Pokud se zrychlí 3× až 5×:

```text

problém byl ve velikosti modelu.

```

---

# Doporučení pro běžné domácí PC

## RTX 3060 12 GB

```text

Qwen3 8B nebo 14B (Q4)

Context 8192

Top K = 3-5

GPU inference

bez reasoning režimu

```

To obvykle vede k odezvám:

```text

1-3 sekundy

```

místo:

```text

30-60 sekund

```

u špatně nastavené konfigurace.
