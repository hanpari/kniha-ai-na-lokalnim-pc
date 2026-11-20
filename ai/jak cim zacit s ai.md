# Jaký software se učit pro práci s AI

Začátečníci často dělají stejnou chybu:

Nainstalují deset různých nástrojů, nerozumí základům a po měsíci mají pocit, že se v AI nedá vyznat.

Lepší přístup je učit se software postupně.

Představ si to jako řidičský průkaz:

```text

1. Naučit se řídit

2. Naučit se servisovat auto

3. Naučit se ladit motor

4. Naučit se stavět vlastní auto

```

U AI je to podobné.

---

# Fáze 1: Úplné základy

Cíl:

```text

Rozumět modelům

Promptům

RAG

Lokální AI

```

---

## 1. Ollama

Nejdůležitější software pro začátečníka.

Umožňuje:

- stahovat modely,

- spouštět modely,

- přepínat mezi modely.

Příklady:

```bash

ollama run qwen3

ollama run llama3.3

```

Co se naučit:

- pull

- run

- list

- create

- Modelfile

Úroveň:

```text

Povinné

```

---

## 2. Open WebUI

Grafické rozhraní nad Ollamou.

Naučí tě:

- pracovat s modely,

- vytvářet asistenty,

- používat znalostní báze,

- používat RAG.

Co se naučit:

```text

Knowledge Base

Workspace

Models

Tools

Prompty

```

Úroveň:

```text

Povinné

```

---

## 3. VS Code

Přestože nejde přímo o AI nástroj, stane se tvým hlavním pracovním prostředím.

Použití:

- Markdown

- Python

- Git

- Prompt Engineering

Pro autora jako jsi ty téměř nutnost.

Úroveň:

```text

Povinné

```

---

## 4. Git

Pokud budeš vytvářet:

- knowledge base,

- prompty,

- dokumentaci,

- LoRA,

Git se velmi hodí.

Nemusíš být expert.

Nauč se:

```bash

git clone

git pull

git commit

git push

```

Úroveň:

```text

Povinné

```

---

# Fáze 2: RAG a znalostní báze

Cíl:

```text

Postavit vlastního AI asistenta.

```

---

## 5. Qdrant

Nejpoužívanější vektorová databáze.

Použití:

```text

RAG

Vyhledávání znalostí

Dokumentace

```

Ve většině případů ji Open WebUI obslouží za tebe.

Přesto je dobré rozumět:

- kolekcím,

- embeddingům,

- vyhledávání.

Úroveň:

```text

Doporučeno

```

---

## 6. AnythingLLM

Alternativa k Open WebUI.

Skvělé pro:

- PDF

- Word

- Firemní dokumentaci

Někdy bývá jednodušší než Open WebUI.

Úroveň:

```text

Doporučeno

```

---

# Fáze 3: Obrazová AI

Cíl:

```text

Tvořit ilustrace

Obaly knih

Koncepty postav

```

---

## 7. ComfyUI

Nejdůležitější nástroj pro generování obrázků.

Dnes prakticky standard.

Umožňuje:

- FLUX

- Stable Diffusion

- LoRA

- ControlNet

- Upscaling

Co se naučit:

```text

Nodes

Workflows

Checkpoint

VAE

LoRA

```

Úroveň:

```text

Povinné pro obrázky

```

---

## 8. FLUX

Nejde o software, ale o model.

Pravděpodobně nejlepší start pro ilustrace.

Použití:

```text

Postavy

Fantasy

Obálky

Scény

```

Úroveň:

```text

Povinné pro ilustrace

```

---

# Fáze 4: LoRA a Fine-Tuning

Cíl:

```text

Učit modely vlastní data.

```

---

## 9. AI Toolkit (Ostris)

Dnes jeden z nejjednodušších způsobů trénování LoRA pro FLUX.

Použití:

```text

Style LoRA

Character LoRA

```

Úroveň:

```text

První nástroj pro LoRA

```

---

## 10. Kohya SS

Dlouholetý standard.

Mírně složitější.

Obrovské množství možností.

Použití:

```text

Stable Diffusion

SDXL

LoRA

```

Úroveň:

```text

Pokročilé

```

---

## 11. LLaMA-Factory

Jeden z nejlepších nástrojů na fine-tuning jazykových modelů.

Použití:

```text

Qwen

Llama

Gemma

Mistral

```

Úroveň:

```text

Pokročilé

```

---

# Fáze 5: Programování

Tady se z uživatele stává tvůrce.

---

## 12. Python

Nejdůležitější jazyk v AI.

Používá se téměř všude.

Nauč se:

```python

list

dict

for

function

file

json

```

Nemusíš být profesionální programátor.

Stačí základy.

Úroveň:

```text

Velmi důležité

```

---

## 13. Jupyter Notebook

Ideální na:

- experimenty,

- analýzu dat,

- embeddingy,

- fine-tuning.

Úroveň:

```text

Doporučeno

```

---

# Fáze 6: Profesionální AI

Po zvládnutí předchozího.

---

## 14. Docker

Téměř každá větší AI aplikace používá Docker.

Příklady:

```text

Open WebUI

Qdrant

Langflow

Flowise

```

Úroveň:

```text

Velmi doporučeno

```

---

## 15. Langflow

Grafické vytváření AI agentů.

Můžeš propojit:

```text

Model

RAG

Web Search

Databázi

```

bez programování.

Úroveň:

```text

Pokročilé

```

---

## 16. Flowise

Podobné jako Langflow.

Velmi dobré pro:

```text

AI agenty

Firemní chatboty

```

Úroveň:

```text

Pokročilé

```

---

# Co bych se učil na tvém místě

Pokud je tvůj cíl:

- Sixbound

- ilustrace

- překlady

- znalostní databáze

- vlastní AI asistent

šel bych přesně v tomto pořadí:

```text

1. Ollama

2. Open WebUI

3. Prompt Engineering

4. RAG

5. Qwen

6. FLUX

7. ComfyUI

8. LoRA pro FLUX

9. Python

10. Docker

11. LLaMA-Factory

12. AI Agenti

```

---

# Co bych zatím neřešil

Začátečníci často ztrácejí čas zde:

```text

Kubernetes

PyTorch internals

CUDA optimalizace

Distributed training

RLHF

Transformer architektury do hloubky

```

To je zajímavé až ve chvíli, kdy máš za sebou:

```text

Ollama

Open WebUI

RAG

ComfyUI

LoRA

```

---

# Minimální stack, který by měl umět každý AI nadšenec

```text

Ollama

Open WebUI

Qwen

RAG

VS Code

Git

FLUX

ComfyUI

Docker

Základy Pythonu

```

S těmito deseti technologiemi už dokážeš postavit:

- lokálního AI asistenta,

- systém nad PDF dokumentací,

- asistenta pro Sixbound,

- generátor ilustrací,

- vlastní LoRA postav,

- jednoduché AI agenty,

- překladový systém,

- znalostní bázi pro výuku nebo firmu.
