# Typické nástroje (Tools), které AI používá

Když dnes lidé mluví o AI agentech, často si představují jeden velký model.

Ve skutečnosti bývá moderní AI systém složen z:

```text

AI Model

+

Tools

+

Paměť

+

RAG

+

Automatizace

```

Často se říká:

> Model myslí, nástroje konají.

Například samotný model neumí:

- stáhnout soubor,

- vytvořit PDF,

- odeslat e-mail,

- prohledat web,

- spustit SQL dotaz.

Musí použít nástroj.

---

# Jak funguje Tool Calling

Příklad:

Uživatel:

```text

Jaké bude zítra počasí?

```

AI si uvědomí:

```text

Nevím.

Potřebuji aktuální data.

```

Použije nástroj:

```text

Weather API

```

a teprve poté odpoví.

---

# Hlavní kategorie nástrojů

```text

Web

Dokumenty

Databáze

Kancelářské soubory

Obrázky

Zvuk

Kód

Automatizace

Komunikace

Průmyslové systémy

```

---

# 1. Web Search

Nejpoužívanější nástroj vůbec.

---

## Co umí

```text

Vyhledat informace

Otevřít stránky

Shrnovat články

Porovnávat produkty

```

---

## Příklady

Agent:

```text

Najdi nejnovější procesory AMD.

```

---

Použije:

```text

Google

Bing

SearxNG

Brave Search

```

---

# 2. PDF nástroje

Velmi časté ve firmách.

---

## Co umí

```text

Číst PDF

Vytvářet PDF

Spojovat PDF

Extrahovat text

```

---

## Příklady

```text

PyPDF2

pdfplumber

PDFium

ReportLab

```

---

## Agent

```text

Přečti smlouvu.

Najdi sankce.

Vytvoř shrnutí.

```

---

# 3. Word dokumenty

---

## Co umí

```text

DOCX

ODT

RTF

```

---

## Typické použití

```text

Generování smluv

Vytváření reportů

Automatické zápisy

```

---

## Knihovny

```text

python-docx

LibreOffice

Pandoc

```

---

# 4. Excel a tabulky

Jedny z nejdůležitějších firemních nástrojů.

---

## Co umí

```text

Číst XLSX

Upravovat XLSX

Dělat výpočty

Tvořit grafy

```

---

## Příklady

```text

Pandas

OpenPyXL

LibreOffice Calc

```

---

Agent:

```text

Analyzuj prodeje.

Najdi odchylky.

Vytvoř graf.

```

---

# 5. Databáze

Velmi často používané.

---

Model může komunikovat s:

```text

SQLite

MySQL

PostgreSQL

SQL Server

Oracle

```

---

## Dotaz

```text

Kolik kusů jsme prodali loni?

```

---

AI vytvoří SQL:

```sql

SELECT ...

```

a vrátí odpověď.

---

# 6. RAG

Technicky nejde o jeden nástroj.

---

Tvoří jej kombinace:

```text

Embedding model

+

Vector DB

+

Retriever

```

---

## Použití

```text

PDF

Normy

Dokumentace

Manuály

```

---

# 7. Vektorové databáze

Používají se téměř vždy s RAG.

---

Nejčastější:

```text

Qdrant

Chroma

FAISS

Milvus

Weaviate

```

---

## Úkol

Najít nejrelevantnější informace.

---

# 8. Python Runner

Extrémně důležitý nástroj.

Umožňuje modelu spouštět kód.

---

## Příklad

Uživatel:

```text

Vypočítej statistiku.

```

Model:

```python

import pandas as pd

...

```

spustí kód a vrátí výsledek.

---

## Použití

```text

Statistika

Grafy

Automatizace

Analýzy

```

---

# 9. Shell / Terminál

Agent může používat přímo operační systém.

---

## Příklady

```bash

ls

grep

git

ffmpeg

```

---

## Praktické použití

```text

Konverze videa

Zálohy

Správa souborů

```

---

# 10. Git

Velmi užitečné pro programátory.

---

Agent může:

```text

Commitovat

Porovnávat větve

Kontrolovat změny

Vytvářet release

```

---

# 11. E-mail

Velmi časté u AI agentů.

---

## Příklady

```text

SMTP

Outlook API

Gmail API

```

---

Agent může:

```text

Číst e-maily

Odpovídat

Třídit poštu

```

---

# 12. Kalendář

Používají téměř všechny kancelářské AI.

---

## Příklady

```text

Google Calendar

Outlook Calendar

Exchange

```

---

## Použití

```text

Hledání termínů

Plánování schůzek

Rezervace místností

```

---

# 13. Generování obrázků

Jedna z nejpoužívanějších skupin.

---

## Modely

```text

FLUX

SDXL

Stable Diffusion

DALL-E

```

---

## Agent

```text

Napiš scénu

↓

Generuj ilustraci

↓

Ulož PNG

```

---

# 14. Editace obrázků

---

Použití:

```text

Upscaling

Inpainting

Odstranění pozadí

```

---

## Nástroje

```text

ControlNet

IP Adapter

SAM

ESRGAN

```

---

# 15. OCR

OCR = převod obrázků na text.

---

Příklady:

```text

Tesseract

PaddleOCR

EasyOCR

```

---

Použití:

```text

Naskenované PDF

Faktury

Štítky

```

---

# 16. Přepis řeči

---

Příklady:

```text

Whisper

WhisperX

FasterWhisper

```

---

Použití:

```text

Schůzky

Rozhovory

Přednášky

```

---

# 17. Text To Speech

---

Příklady:

```text

Kokoro

Piper

XTTS

ElevenLabs

```

---

Použití:

```text

Audioknihy

Podcasty

Výukové materiály

```

---

# 18. PLC a průmyslové systémy

Ve výrobních podnicích.

---

Agent může komunikovat s:

```text

Siemens PLC

Modbus

OPC-UA

MQTT

```

---

Použití:

```text

Monitoring výroby

Kontrola linek

Alarmy

```

---

# 19. Strojové vidění

---

Agent používá:

```text

YOLO

OpenCV

SAM

```

---

Použití:

```text

Detekce vad

Kontrola výrobků

Počítání kusů

```

---

# 20. Automatizační platformy

Spojují více nástrojů dohromady.

---

## Nejčastější

```text

n8n

Make

Zapier

Node-RED

```

---

Například:

```text

Nový e-mail

↓

AI analýza

↓

Vytvoření PDF

↓

Uložení do SharePointu

↓

Odeslání odpovědi

```

---

# Jak vypadají pokročilí AI agenti

Například agent pro Sixbound:

```text

Qwen

+

RAG

+

Markdown parser

+

FLUX

+

Kokoro

+

PDF exporter

```

---

Agent pro firmu:

```text

Llama

+

Qdrant

+

PDF reader

+

SQL

+

Outlook

+

Excel

```

---

# Nejdůležitější nástroje, které bych se učil jako první

Pokud chceš stavět vlastní AI aplikace, pořadí by bylo:

```text

1. Ollama

2. Open WebUI

3. Web Search

4. RAG

5. Qdrant

6. Python Runner

7. PDF Tools

8. Excel Tools

9. Git

10. FLUX

11. Whisper

12. Kokoro

13. SQL

14. n8n

15. Langflow

```

Po zvládnutí těchto 15 oblastí budeš rozumět většině moderních AI agentů, které dnes používají firmy i vývojáři.
