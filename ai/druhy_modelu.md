\# Přehled modelů pro Ollama: klasifikace, rozdíly a použití



Když otevřeš knihovnu Ollamy, najdeš desítky modelů:



```text

Llama

Qwen

Mistral

Gemma

DeepSeek

Phi

Command-R

Nous Hermes

Dolphin

Neural Chat

...

```



Začátečník často neví:



```text

Který model použít?

Jaké jsou rozdíly?

Kdy sáhnout po jiném modelu?

```



Dobrá zpráva je, že většina modelů spadá do několika hlavních skupin.



\---



\# Jak se v modelech orientovat



Model lze zařadit podle:



```text

1\. Architektury

2\. Velikosti

3\. Zaměření

4\. Licence

5\. Schopností

```



\---



\# Hlavní rodiny modelů



\## 1. Qwen



Vývojář:



```text

Alibaba

```



Dnes jeden z nejsilnějších open-weight modelů.



\---



\### Silné stránky



```text

Programování

Multijazyčnost

Logika

RAG

Agenti

```



\---



\### Slabší stránky



```text

Vyšší nároky než malé modely

```



\---



\### Typické použití



```text

Ollama

Open WebUI

RAG

AI agenti

Firemní asistenti

```



\---



\### Příklady



```bash

ollama run qwen3:8b

ollama run qwen3:14b

ollama run qwen3:32b

```



\---



\## Pro koho?



Pokud nevíš co použít:



```text

Vyber Qwen.

```



Je to dnes velmi bezpečná volba.



\---



\# 2. Llama



Vývojář:



```text

Meta

```



\---



Pravděpodobně nejznámější open modelová rodina.



\---



\### Silné stránky



```text

Kvalitní jazyk

Stabilita

Obrovský ekosystém

```



\---



\### Slabší stránky



V některých oblastech jej dnes Qwen překonává.



\---



\### Typické použití



```text

Chat

Asistenti

Výuka

Textová tvorba

```



\---



\### Příklady



```bash

ollama run llama3.1:8b

ollama run llama3.3

```



\---



\# 3. Gemma



Vývojář:



```text

Google

```



\---



Navržena pro efektivní provoz.



\---



\### Silné stránky



```text

Malé nároky

Vynikající poměr výkon/velikost

```



\---



\### Typické použití



```text

Notebooky

Mini PC

Lokální chat

```



\---



\### Příklady



```bash

ollama run gemma3:4b

ollama run gemma3:12b

```



\---



\# 4. Mistral



Vývojář:



```text

Mistral AI

```



\---



Francouzská společnost zaměřená na open modely.



\---



\### Silné stránky



```text

Rychlost

Kompaktnost

Dobré programování

```



\---



\### Použití



```text

Chat

Kód

Agenti

```



\---



\### Příklady



```bash

ollama run mistral

ollama run mistral-small

```



\---



\# 5. DeepSeek



Vývojář:



```text

DeepSeek

```



\---



Známý zejména díky reasoning modelům.



\---



\### Silné stránky



```text

Matematika

Logika

Analýza

Programování

```



\---



\### Nevýhody



```text

Pomalost

Delší přemýšlení

```



\---



\### Použití



```text

Složité problémy

Výzkum

Inženýrství

```



\---



\### Nevhodné pro



```text

Rychlý chat

```



\---



\# 6. Phi



Vývojář:



```text

Microsoft

```



\---



Extrémně malé modely.



\---



\### Silné stránky



```text

Rychlost

Malé nároky

```



\---



\### Použití



```text

Notebook

Mini PC

Vestavěná zařízení

```



\---



\### Příklady



```bash

ollama run phi4

```



\---



\# 7. Command-R



Vývojář:



```text

Cohere

```



\---



Navržen hlavně pro:



```text

RAG

Firemní použití

Dokumenty

```



\---



\### Použití



```text

Chat nad PDF

Technická dokumentace

```



\---



\# Specializované modely



\---



\# Coding modely



Optimalizované pro programování.



\---



Příklady:



```text

DeepSeek Coder

CodeLlama

Qwen Coder

StarCoder

```



\---



Použití:



```text

Python

C#

C++

Java

```



\---



\# Reasoning modely



Modely určené k přemýšlení.



\---



Příklady:



```text

DeepSeek-R1

QwQ

```



\---



Použití:



```text

Matematika

Analýza

Důkazy

```



\---



Nevýhoda:



```text

Pomalost

```



\---



\# Embedding modely



Nejsou určeny pro chat.



\---



Používají se pro:



```text

RAG

Vyhledávání

Vektorové databáze

```



\---



Příklady:



```bash

ollama run nomic-embed-text

```



```bash

ollama run bge-m3

```



\---



\# Vision modely



Umí pracovat s obrázky.



\---



Příklady:



```text

Qwen-VL

Llama Vision

Gemma Vision

```



\---



Použití:



```text

Analýza fotek

OCR

Diagramy

```



\---



\# Jak číst názvy modelů



Příklad:



```text

qwen3:14b

```



\---



Rozklad:



```text

qwen3

```



rodina modelu



\---



```text

14b

```



14 miliard parametrů



\---



Další příklad:



```text

qwen3:32b-q4

```



\---



Význam:



```text

Qwen 3



32 miliard parametrů



Q4 kvantizace

```



\---



\# Jak vybírat podle velikosti



\## 1B–4B



```text

Velmi rychlé

Nižší kvalita

```



Použití:



```text

Notebook

Experimenty

```



\---



\## 7B–14B



Nejoblíbenější kategorie.



Použití:



```text

Chat

RAG

Agenti

Dokumenty

```



\---



\## 30B–40B



Výrazně vyšší kvalita.



\---



Nevýhody:



```text

Více VRAM

Pomalejší

```



\---



\## 70B+



Téměř profesionální úroveň.



Použití:



```text

Výzkum

Komplexní analýzy

```



\---



\# Doporučení podle použití



\## Chci univerzální model



```bash

qwen3:14b

```



\---



\## Mám slabší počítač



```bash

gemma3:4b

```



\---



\## Chci programovat



```bash

qwen-coder

```



nebo



```bash

deepseek-coder

```



\---



\## Chci matematiku



```bash

deepseek-r1

```



\---



\## Chci RAG



```bash

qwen3:14b

\+

nomic-embed-text

```



\---



\## Chci AI agenta



```bash

qwen3:14b

```



\---



\## Chci maximální rychlost



```bash

phi4

```



nebo



```bash

gemma3:4b

```



\---



\# Doporučení pro většinu uživatelů Ollamy



Pokud dnes (2026) stavíš:



```text

Open WebUI

RAG

PDF

Agenty

Automatizaci

```



pak je velmi rozumný základ:



```bash

ollama pull qwen3:14b

ollama pull nomic-embed-text

```



Na této dvojici lze postavit:



\- chat nad PDF,

\- firemního asistenta,

\- studijního asistenta,

\- AI agenty,

\- knowledge base systémy,

\- pomocníka pro psaní knih,

\- překladový systém.



Až ve chvíli, kdy přesně víš, co ti chybí, má smysl přecházet na specializované modely jako DeepSeek-R1, Qwen-Coder nebo vision modely.

