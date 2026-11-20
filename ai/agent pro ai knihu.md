# Jak vytvořit AI agenta pro čtení audioknih

Tento návod ukazuje, jak vytvořit systém, který dokáže automaticky převést román, povídku nebo dokument do audioknihy.

Nebudeme pouze generovat hlas.

Cílem bude vytvořit skutečného agenta, který umí:

- načíst text,

- rozdělit jej na kapitoly,

- identifikovat postavy,

- přiřadit hlasy,

- generovat audio,

- spojit kapitoly,

- vytvořit metadata,

- exportovat MP3 nebo M4B.

Výsledkem bude něco podobného profesionální audioknize.

---

# Co je agent pro audioknihy?

Běžný TTS (Text To Speech) systém funguje takto:

```text

Text

&#x20;↓

Hlas

&#x20;↓

Audio

```

Agent dělá více:

```text

Román

&#x20;↓

Analýza postav

&#x20;↓

Rozdělení scén

&#x20;↓

Přiřazení hlasů

&#x20;↓

Generování zvuku

&#x20;↓

Audiokniha

```

---

# Jak bude systém vypadat?

```text

&#x20;            Román

&#x20;              │

&#x20;              ▼

&#x20;        Open WebUI

&#x20;              │

&#x20;              ▼

&#x20;        Qwen nebo Llama

&#x20;              │

&#x20;     ┌────────┼─────────┐

&#x20;     ▼                  ▼

&#x20;Analýza textu      Databáze postav

&#x20;     │                  │

&#x20;     └────────┬─────────┘

&#x20;              ▼

&#x20;         TTS systém

&#x20;              │

&#x20;              ▼

&#x20;         WAV soubory

&#x20;              │

&#x20;              ▼

&#x20;        Kapitoly MP3

&#x20;              │

&#x20;              ▼

&#x20;          Audiokniha

```

---

# Krok 1: Vyber jazykový model

Model bude fungovat jako režisér.

Jeho úkolem není mluvit.

Jeho úkolem je chápat text.

Doporučuji:

```text

Qwen3 14B

Qwen3 32B

Llama 3.3

```

---

# Krok 2: Vyber generátor hlasu

To je nejdůležitější část.

Dnes existují tři hlavní cesty.

---

# Možnost 1: Piper

Nejjednodušší.

Výhody:

- lokální

- rychlé

- zdarma

Nevýhody:

- méně přirozené hlasy

Použití:

```text

Povídky

Technické dokumenty

E-learning

```

---

# Možnost 2: Kokoro

V současnosti velmi populární.

Výhody:

- výborná kvalita

- nízké nároky

Použití:

```text

Audioknihy

Podcasty

Vyprávění

```

---

# Možnost 3: XTTS v2

Nejpokročilejší lokální řešení.

Výhody:

- klonování hlasů

- emoce

- vysoká kvalita

Nevýhody:

- vyšší nároky

Použití:

```text

Profesionální audioknihy

```

---

# Krok 3: Připrav text

Například:

```text

Kapitola 1

Kapitola 2

Kapitola 3

```

Ideálně:

```text

Markdown

DOCX

EPUB

TXT

```

---

# Krok 4: Analýza postav

LLM může vytvořit seznam postav.

Například:

```text

Jeremiah Hawthorne

Lydia Carver

Xavier Valehart

Honker

```

---

# Výsledek

Agent vytvoří databázi:

```json

{

&#x20;"Jeremiah":"hlas_1",

&#x20;"Lydia":"hlas_2",

&#x20;"Xavier":"hlas_3"

}

```

---

# Krok 5: Rozlišení dialogů

Původní text:

```text

"Kam jdeme?" zeptal se Jeremiah.



"Nevím," odpověděla Lydia.

```

Agent jej rozdělí:

```text

Narrator

Jeremiah

Lydia

```

---

# Krok 6: Přiřazení hlasů

Příklad:

```text

Vypravěč

→ mužský hlas



Jeremiah

→ mladý hlas



Lydia

→ ženský hlas



Xavier

→ hlubší hlas

```

---

# Krok 7: Generování řeči

Proces:

```text

Text

&#x20;↓

TTS

&#x20;↓

WAV

```

Probíhá po odstavcích.

---

# Proč ne po kapitolách?

Dlouhé kapitoly často vedou k:

- přehlcení paměti,

- horší intonaci,

- pádům programu.

Lepší je:

```text

Odstavec

&#x20;↓

Audio

&#x20;↓

Další odstavec

```

---

# Krok 8: Spojení audia

Vzniknou stovky souborů:

```text

001.wav

002.wav

003.wav

...

```

Agent je spojí:

```text

chapter01.mp3

```

---

# Krok 9: Generování metadat

Například:

```text

Název

Autor

Kapitola

Číslo stopy

```

---

# Krok 10: Export

Nejběžnější formáty:

```text

MP3

```

---

Pokročilé:

```text

M4B

```

M4B podporuje:

- kapitoly,

- záložky,

- pokračování poslechu.

To používá například Audible.

---

# Jednoduchá verze systému

Pro začátečníka:

```text

Ollama

+

Qwen

+

Kokoro

+

Open WebUI

```

Umí:

- převod textu na hlas,

- základní analýzu,

- více hlasů.

---

# Pokročilá verze

```text

Ollama

+

Qwen3

+

XTTS v2

+

RAG

+

Open WebUI

```

Umí:

- databázi postav,

- různé hlasy,

- hlasové klony,

- znalost světa románu.

---

# Využití RAG

U dlouhých sérií vzniká problém.

V kapitole 50 si agent nemusí pamatovat:

```text

Jak mluví Jeremiah.

```

---

Řešením je:

```text

Character Bible

```

Například:

```text

Jeremiah:

13 let

Zamyšlený

Mluví klidně



Lydia:

Energická

Rychlá řeč

```

---

RAG zajistí, že agent vždy najde správný profil postavy.

---

# Klonování hlasů

Nejpůsobivější funkce.

Dodáš:

```text

30 sekund hlasového vzorku

```

Agent vytvoří:

```text

Digitální kopii hlasu

```

Pak může číst celý román.

---

# Workflow pro Sixbound

Ideální řešení:

```text

Markdown kapitoly

&#x20;       │

&#x20;       ▼

&#x20;     Qwen

&#x20;       │

&#x20;       ▼

&#x20;Analýza dialogů

&#x20;       │

&#x20;       ▼

&#x20;Character Bible

&#x20;       │

&#x20;       ▼

&#x20;     XTTS

&#x20;       │

&#x20;       ▼

&#x20;    MP3/M4B

```

---

# Jaké znalosti potřebuješ?

Nejdříve:

```text

Ollama

Open WebUI

Prompt Engineering

```

Pak:

```text

Kokoro

XTTS

FFmpeg

```

Nakonec:

```text

Python

RAG

AI Agenti

```

---

# Doporučené pořadí pro samouka

```text

1. Ollama

2. Open WebUI

3. Qwen

4. Kokoro

5. FFmpeg

6. XTTS

7. RAG

8. Python

9. Langflow

10. Automatizace

```

---

# Cíl

Po zvládnutí těchto kroků dokážeš vytvořit systém, který z markdownu, DOCX nebo EPUB automaticky vyrobí audioknihu:

```text

Román

&#x20; ↓

Analýza

&#x20; ↓

Postavy

&#x20; ↓

Hlasy

&#x20; ↓

TTS

&#x20; ↓

MP3/M4B

```

a udržuje konzistentní vypravěče i dialogy napříč stovkami kapitol bez ručního zpracování každé kapitoly.
