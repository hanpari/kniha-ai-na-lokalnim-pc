# Jak zprovoznit lokální AI systém pro otázky a odpovědi nad PDF a Office dokumenty pomocí Ollama a Open WebUI

Tento návod ukazuje, jak vytvořit systém podobný firemnímu chatbotu, který odpovídá na otázky na základě vlastní dokumentace.

Například:

- technická dokumentace

- směrnice ISO

- pracovní postupy

- návody k obsluze

- diplomové práce

- Word dokumenty

- PDF soubory

- Excel tabulky

- Markdown dokumentace

Výsledkem bude AI chatbot, kterému můžeš položit otázku:

> Jaký je postup reklamace?

a chatbot najde odpověď v nahraných dokumentech.

---

# Co budeme potřebovat

## Software

- Ollama

- Open WebUI

- AI model

- Embedding model

---

# Jak bude systém fungovat

Celá architektura bude vypadat takto:

```text

&#x20;                  Uživatel

&#x20;                       │

&#x20;                       ▼

&#x20;                 Open WebUI

&#x20;                       │

&#x20;                       ▼

&#x20;                      RAG

&#x20;               (vyhledávání)

&#x20;                       │

&#x20;        ┌──────────────┴──────────────┐

&#x20;        ▼                             ▼

&#x20;  Vector Database             Dokumenty

&#x20;        │                    PDF/DOCX/XLSX

&#x20;        └──────────────┬──────────────┘

&#x20;                       ▼

&#x20;                    Ollama

&#x20;                       │

&#x20;                       ▼

&#x20;                  AI Model

&#x20;                       │

&#x20;                       ▼

&#x20;                    Odpověď

```

---

# Krok 1: Instalace Ollama

Stáhni Ollama:

```text

https://ollama.com

```

Po instalaci otevři příkazovou řádku a vyzkoušej:

```bash

ollama --version

```

Pokud se zobrazí číslo verze, Ollama běží správně.

---

# Krok 2: Instalace modelu

Pro dokumentaci doporučuji:

```bash

ollama pull qwen3:14b

```

nebo

```bash

ollama pull llama3.3:70b

```

podle výkonu počítače.

Pro většinu domácích PC je rozumné:

```bash

ollama pull qwen3:8b

```

nebo

```bash

ollama pull qwen3:14b

```

---

# Krok 3: Instalace embedding modelu

Pro RAG je potřeba embedding model.

Stáhni například:

```bash

ollama pull nomic-embed-text

```

nebo

```bash

ollama pull bge-m3

```

Embedding model neslouží k chatování.

Jeho úkolem je převádět dokumenty na vektory.

---

# Krok 4: Instalace Open WebUI

Nejjednodušší je Docker.

```bash

docker run -d 

-p 3000:8080 

--add-host=host.docker.internal:host-gateway 

-v open-webui:/app/backend/data 

--name open-webui 

ghcr.io/open-webui/open-webui:main

```

Poté otevři:

```text

http://localhost:3000

```

---

# Krok 5: Připojení Open WebUI k Ollamě

V nastavení Open WebUI nastav:

```text

Ollama URL:

http://host.docker.internal:11434

```

nebo

```text

http://localhost:11434

```

dle konfigurace.

Po připojení se zobrazí nainstalované modely.

Například:

```text

qwen3:14b

nomic-embed-text

```

---

# Krok 6: Zapnutí Knowledge Base

V Open WebUI najdeš sekci:

```text

Workspace

```

nebo

```text

Knowledge

```

podle verze.

Zde se vytváří znalostní báze.

---

# Krok 7: Vytvoření znalostní databáze

Klikni:

```text

Create Knowledge Base

```

Například:

```text

Firemní dokumentace

```

nebo

```text

Sixbound Lore

```

---

# Krok 8: Nahrání dokumentů

Nahraj:

```text

směrnice.pdf

reklamace.pdf

postupy.docx

bezpecnost.docx

```

Open WebUI začne dokumenty zpracovávat.

---

# Co se děje na pozadí?

Představ si PDF o 500 stranách.

Systém provede:

```text

PDF

&#x20;↓

Rozdělení na odstavce

&#x20;↓

Embedding model

&#x20;↓

Vektory

&#x20;↓

Vector database

```

To může trvat několik minut.

Provádí se pouze jednou.

---

# Krok 9: Vytvoření vlastního asistenta

Open WebUI umožňuje vytvořit specializovaného bota.

Například:

```text

ISO Asistent

```

nebo

```text

Technická Dokumentace

```

---

## System Prompt

Doporučuji:

```text

Odpovídej pouze na základě dodané dokumentace.



Pokud odpověď nelze v dokumentaci nalézt,

napiš:



"Informace nebyla nalezena

v dostupných dokumentech."



Uváděj zdrojový dokument.

```

Tím výrazně snížíš halucinace.

---

# Krok 10: První dotaz

Uživatel zadá:

```text

Jaký je postup reklamace?

```

---

# Co se stane uvnitř systému?

```text

Otázka

&#x20;↓

Embedding otázky

&#x20;↓

Vyhledání podobných odstavců

&#x20;↓

Nalezení relevantních dokumentů

&#x20;↓

Poslání modelu

&#x20;↓

Generování odpovědi

```

---

# Praktický příklad

V PDF je uvedeno:

```text

Reklamaci musí zákazník podat do 30 dnů.

```

Položíš otázku:

```text

Do kdy lze podat reklamaci?

```

Systém najde příslušný odstavec a odpoví:

> Reklamaci je nutné podat do 30 dnů od vzniku důvodu reklamace.

---

# Jaké formáty fungují nejlépe?

## Výborné

```text

PDF

DOCX

TXT

Markdown

HTML

```

---

## Použitelné

```text

PPTX

XLSX

CSV

```

---

## Horší

Naskenované PDF jako obrázek.

Například:

```text

smlouva_scan.pdf

```

V takovém případě musí proběhnout OCR.

---

# Doporučené modely

## Slabší počítač

16 GB RAM

```text

qwen3:8b

gemma3:12b

```

---

## Střední počítač

32 GB RAM

```text

qwen3:14b

llama3.1:8b

```

---

## Výkonný počítač

64+ GB RAM nebo silná GPU

```text

qwen3:32b

llama3.3:70b

deepseek-r1

```

---

# Typické chyby

## Příliš velký model

Například:

```text

70B model

```

na notebooku s 16 GB RAM.

Výsledek:

```text

Velmi pomalé odpovědi

```

---

## Příliš mnoho dokumentů najednou

Například:

```text

100 000 stran PDF

```

První indexace může trvat hodiny.

---

## Špatný prompt

Místo:

```text

Používej pouze dokumentaci.

```

někteří nechají výchozí nastavení.

Pak AI začne více halucinovat.

---

# Jak poznat, že RAG funguje?

Polož otázku:

```text

Co je ve třetím odstavci směrnice XYZ?

```

Pokud model odpoví správně a cituje dokument, používá databázi.

Pokud začne odpovídat obecnými znalostmi, RAG není správně nastaven.

---

# Výsledek

Po dokončení získáš lokální systém podobný firemnímu Copilotu:

```text

PDF

DOCX

XLSX

PPTX

&#x20;       ↓

&#x20;Open WebUI

&#x20;       ↓

&#x20;     RAG

&#x20;       ↓

&#x20;    Ollama

&#x20;       ↓

&#x20;     Qwen

&#x20;       ↓

&#x20;    Odpověď

```

Takový systém je ideální například pro:

- firemní směrnice,

- technickou dokumentaci,

- projektovou dokumentaci,

- normy ISO,

- školní materiály,

- svět Sixbound,

- znalostní databáze pro výuku matematiky, fyziky a chemie.
