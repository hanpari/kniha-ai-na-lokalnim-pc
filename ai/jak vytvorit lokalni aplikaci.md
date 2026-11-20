# Jak vytvořit AI agenta a distribuovat ho jako lokální program

Jakmile zvládneš:

- Ollama

- Open WebUI

- RAG

- LoRA

začne tě zajímat další krok:

> Jak vytvořit vlastního AI agenta, kterého může používat kdokoliv jako běžný program?

Například:

- Sixbound Assistant

- Firemní chatbot

- Asistent pro dokumentaci

- Generátor audioknih

- Překladatel

- AI vypravěč

Princip je překvapivě jednoduchý.

---

# Co je AI agent?

Model sám o sobě není agent.

Model pouze odpovídá.

Agent je:

```text

Model

+

Pravidla

+

Nástroje

+

Uživatelské rozhraní

```

Například:

```text

Qwen

+

RAG

+

Databáze

+

Tlačítka

+

GUI

```

---

# Jak vypadá architektura?

```text

&#x20;     Uživatel

&#x20;          │

&#x20;          ▼

&#x20;     GUI aplikace

&#x20;          │

&#x20;          ▼

&#x20;     AI Agent

&#x20;          │

&#x20;   ┌──────┼───────┐

&#x20;   ▼      ▼       ▼

&#x20;Ollama   RAG   Nástroje

&#x20;   │

&#x20;   ▼

&#x20;Model

```

---

# Nejdřív si odpověz na otázku

Co má agent dělat?

Například:

## Asistent pro Sixbound

```text

Číst světovou bibli

Odpovídat na otázky

Generovat ilustrace

```

---

## Firemní asistent

```text

Práce s PDF

Vyhledávání postupů

Shrnutí směrnic

```

---

## Audioknihový agent

```text

Číst román

Přiřazovat hlasy

Generovat MP3

```

---

# Nejjednodušší cesta

Pokud nechceš programovat.

---

## Open WebUI

Vytvoř:

```text

Knowledge Base

```

Přidej:

```text

PDF

DOCX

Markdown

```

Vytvoř asistenta.

Nastav:

```text

System Prompt

Model

Nástroje

```

Hotovo.

---

Takový agent funguje lokálně.

Nevýhoda:

```text

Musí mít nainstalovaný Open WebUI.

```

---

# Druhá úroveň

Vlastní desktopová aplikace.

---

# Technologie

Nejčastější kombinace:

```text

Python

+

Ollama

+

GUI

```

---

GUI může být:

```text

Tkinter

PyQt

CustomTkinter

```

---

Architektura:

```text

Program

&#x20;    │

&#x20;    ▼

&#x20;Ollama API

&#x20;    │

&#x20;    ▼

&#x20;  Qwen

```

---

# Příklad

Tvé okno programu:

```text

+--------------------+

| Sixbound Assistant |

+--------------------+

|                    |

| Kdo je Honker?     |

|                    |

+--------------------+

| Odeslat            |

+--------------------+

```

Pod kapotou:

```python

response = ollama.chat(...)

```

---

# Třetí úroveň

Agent s více nástroji.

---

Například:

```text

Chat

+

RAG

+

Generování obrázků

+

Audioknihy

```

---

Proces:

```text

Dotaz

&#x20;↓

Plánování

&#x20;↓

Výběr nástroje

&#x20;↓

Výsledek

```

---

# Proč Python?

Protože téměř všechny AI knihovny používají Python.

Například:

```text

LangChain

LlamaIndex

Transformers

CrewAI

```

---

# Jak vytvořit instalátor?

Když už aplikace funguje.

---

# Varianta 1

PyInstaller

Nejjednodušší.

```bash

pip install pyinstaller

```

Poté:

```bash

pyinstaller main.py --onefile

```

Vznikne:

```text

SixboundAssistant.exe

```

---

Výhody:

```text

Jediný EXE soubor

```

Nevýhody:

```text

Velká velikost

```

---

# Varianta 2

Inno Setup

Nejběžnější způsob.

---

Výsledek:

```text

setup.exe

```

jako klasický instalační program.

---

Instalátor může:

```text

Vytvořit zástupce

Instalovat Ollamu

Stáhnout model

Přidat ikonu

```

---

# Jak distribuovat model?

To bývá největší problém.

---

# Špatná cesta

Přibalit:

```text

Qwen3 14B

```

do instalátoru.

Výsledek:

```text

10+ GB

```

---

# Lepší cesta

Instalátor stáhne model při prvním spuštění.

Například:

```bash

ollama pull qwen3:14b

```

---

Používají to prakticky všechny větší projekty.

---

# Jak distribuovat RAG?

Závisí na velikosti.

---

## Malé projekty

Přibalit databázi.

```text

Qdrant

Chroma

```

---

## Velké projekty

Nechat aplikaci index vytvářet sama.

---

# Jak vypadá profesionální produkt?

Například:

```text

setup.exe

```

instaluje:

```text

Program

Ollama

Model

Qdrant

Konfiguraci

```

Po spuštění:

```text

Uživatel klikne

↓

Program zjistí model

↓

Pokud chybí, stáhne ho

↓

Spustí agenta

```

---

# Jak bych to udělal pro Sixbound

Architektura:

```text

Sixbound Assistant

│

├── Qwen3

├── RAG

├── Character Bible

├── Lore Database

├── Illustration Module

└── Audiobook Module

```

---

Instalace:

```text

setup.exe

&#x20;     ↓

Instalace Ollamy

&#x20;     ↓

Stažení Qwen

&#x20;     ↓

Načtení databáze

&#x20;     ↓

Spuštění asistenta

```

---

# Doporučené pořadí učení

Pokusit se napsat plnohodnotného agenta hned je chyba.

Doporučuji:

```text

1. Ollama

2. Open WebUI

3. RAG

4. Python

5. Ollama API

6. CustomTkinter

7. PyInstaller

8. Qdrant

9. LangChain

10. AI Agenti

```

---

# Nejmenší použitelný produkt

Pokud bys chtěl vytvořit svůj první distribuovatelný AI program, stačí:

```text

Python

+

CustomTkinter

+

Ollama

+

Qwen3

+

PyInstaller

```

To je méně než tisíc řádků kódu a získáš:

```text

Vlastní EXE

Vlastní GUI

Lokální model

Bez cloudu

Bez předplatného

```

Právě touto cestou dnes vzniká většina menších lokálních AI aplikací pro Windows.
