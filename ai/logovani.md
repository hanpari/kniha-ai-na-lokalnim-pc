# Kde hledat logy AI systémů a jak je číst

Jedna z nejdůležitějších dovedností při práci s AI není promptování, ale schopnost zjistit:

```text

Co se vlastně děje uvnitř systému?

```

K tomu slouží logy.

Problém je, že různá část systému zapisuje logy na různá místa.

---

# Přehled

Typická AI sestava:

```text

Open WebUI

&#x20;    │

&#x20;    ▼

&#x20;  Ollama

&#x20;    │

&#x20;    ▼

&#x20; Qwen/Llama

&#x20;    │

&#x20;    ▼

&#x20;GPU (NVIDIA)

```

a případně:

```text

RAG

Qdrant

Whisper

XTTS

ComfyUI

```

Každá komponenta má vlastní logy.

---

# 1. Ollama

Nejčastější zdroj problémů.

---

## Windows

Otevři:

```powershell

ollama serve

```

Pokud Ollama neběží jako služba, uvidíš logy přímo v okně.

---

## Diagnostika

```powershell

ollama ps

```

---

Příklad:

```text

NAME          PROCESSOR

qwen3:14b     100% GPU

```

---

Dobrý stav:

```text

100% GPU

```

---

Podezřelý stav:

```text

100% CPU

```

---

## Co hledat

### Pomalé načítání

```text

loading model

```

znamená:

```text

model není v RAM

```

---

### GPU problém

```text

falling back to CPU

```

znamená:

```text

GPU není použito

```

---

# 2. NVIDIA GPU

Nejdůležitější log při hledání výkonu.

---

## Příkaz

```bash

nvidia-smi

```

---

Výstup:

```text

GPU Utilization

VRAM Usage

Power

Temperature

```

---

## Příklad

```text

GPU Util: 98%

VRAM: 15.2 GB / 16 GB

```

Interpretace:

```text

AI běží správně na GPU.

```

---

## Špatný příklad

```text

GPU Util: 2%

```

během generování.

Obvykle značí:

```text

CPU bottleneck

RAG bottleneck

disk bottleneck

```

---

# 3. Open WebUI

Pokud používáš Docker:

---

## Logy

```bash

docker logs open-webui

```

---

Průběžně:

```bash

docker logs -f open-webui

```

---

## Co zde hledat

### Chyby RAG

```text

Embedding failed

```

---

### Chyby Ollama

```text

Connection refused

```

---

### Chyby databáze

```text

Vector search failed

```

---

# 4. Qdrant

Pokud používáš RAG.

---

## Docker

```bash

docker logs qdrant

```

---

## Typické informace

```text

Search duration

Retrieved points

Collection size

```

---

# Praktický příklad

```text

Query duration:

15000 ms

```

znamená:

```text

15 sekund pouze vyhledávání

```

Model ještě ani nezačal odpovídat.

---

# 5. ComfyUI

Velmi důležité při generování obrázků.

---

Logy vidíš přímo v terminálu.

---

Příklad:

```text

Loading checkpoint

```

---

nebo:

```text

Loading VAE

```

---

nebo:

```text

Loading LoRA

```

---

## Co sledovat

### VRAM error

```text

CUDA out of memory

```

---

Příčina:

```text

nedostatek VRAM

```

---

Řešení:

```text

nižší rozlišení

menší model

menší batch size

```

---

# 6. Whisper

Přepis řeči.

---

Příklad:

```text

Loading model...

```

---

Častý problém:

```text

using CPU

```

---

To často znamená:

```text

10× pomalejší přepis

```

---

# 7. XTTS / Kokoro

Audioknihy.

---

Sleduj:

```text

Generation time

Inference time

```

---

Příklad:

```text

Generated 10 sec audio in 2 sec

```

Výborné.

---

Příklad:

```text

Generated 10 sec audio in 40 sec

```

Někde je problém.

---

# 8. Python aplikace

Pokud píšeš vlastní agenty.

---

Nejdůležitější pravidlo:

Loguj úplně všechno.

---

Špatně:

```python

answer = model(prompt)

```

---

Lépe:

```python

print("Sending prompt")

print("Prompt size:", len(prompt))

print("Calling model")

```

---

Ještě lépe:

```python

import logging



logging.info("Calling model")

```

---

# Jak logovat AI agenta

Minimum:

```text

Čas

Dotaz

Model

Počet tokenů

Čas RAG

Čas generování

Použité dokumenty

```

---

# Praktický příklad č. 1

## Uživatel

```text

Kdo je Honker?

```

---

## Log

```text

Question:

Kdo je Honker?



Retrieved:

Dragons.md



Generation:

2 sec

```

---

Zjištění:

```text

RAG našel špatný dokument.

```

Model je nevinný.

---

# Praktický příklad č. 2

## Problém

Qwen odpovídá minutu.

---

## Log

```text

Prompt:

36000 tokens



Generation:

150 tokens



Prompt processing:

52 sec



Generation:

3 sec

```

---

Zjištění:

```text

Problém je kontext.

```

Ne model.

---

# Praktický příklad č. 3

## FLUX

Trvá 5 minut.

---

## ComfyUI log

```text

CUDA out of memory

Falling back

```

---

Zjištění:

```text

Model se nevejde do VRAM.

```

---

# Praktický příklad č. 4

## Audioknižní agent

Pomalý.

---

## Log

```text

XTTS generation:

3 sec



FFmpeg processing:

50 sec

```

---

Zjištění:

```text

XTTS není problém.

```

Problém je export.

---

# Nejlepší nástroje pro sledování logů

## Windows

Vestavěně:

```text

PowerShell

```

---

Pokročilejší:

```text

Windows Terminal

```

---

# NVIDIA

```bash

nvidia-smi -l 1

```

Obnovování každou sekundu.

---

# Docker

```bash

docker logs -f open-webui



docker logs -f qdrant

```

---

# Python

```text

logging

```

nikoliv:

```text

print()

```

u větších projektů.

---

# Zlaté pravidlo AI diagnostiky

Při každém problému si polož otázku:

```text

Kde se ztratil čas?

```

A změř:

```text

1. RAG

2. Načtení modelu

3. Generování

4. Export

5. GPU

```

Jakmile víš, která část zabírá čas, bývá řešení většinou zřejmé.

Proto profesionálové téměř nikdy neladí AI podle pocitu. Nejdříve otevřou:

```text

ollama ps

nvidia-smi

docker logs

ComfyUI console

```

a teprve pak začnou cokoli měnit.
