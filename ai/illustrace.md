# Jak vytvořit systém pro generování ilustrací románu ve vlastním stylu pomocí Ollama, FLUX a Open WebUI

Tento návod ukazuje, jak vytvořit lokální AI systém, který bude generovat ilustrace pro konkrétní román ve stále stejném vizuálním stylu.

Například:

- fantasy román

- sci-fi série

- historický román

- manga

- dětská kniha

- svět Sixbound

Cílem není pouze generovat hezké obrázky.

Cílem je zajistit, aby:

- postavy vypadaly stále stejně,

- prostředí bylo konzistentní,

- styl odpovídal celé knize,

- ilustrace připomínaly práci jednoho ilustrátora.

---

# Jak bude systém fungovat

Architektura bude vypadat přibližně takto:

```text

&#x20;                        Autor

&#x20;                          │

&#x20;                          ▼

&#x20;                     Open WebUI

&#x20;                          │

&#x20;                          ▼

&#x20;                   Svět románu

&#x20;                (PDF, DOCX, MD)

&#x20;                          │

&#x20;                          ▼

&#x20;                         RAG

&#x20;                          │

&#x20;       ┌──────────────────┴──────────────────┐

&#x20;       ▼                                     ▼

&#x20;  Ollama                           Generátor obrázků

&#x20;(Qwen/Llama)                      (FLUX nebo SDXL)

&#x20;       │                                     │

&#x20;       └──────────────────┬──────────────────┘

&#x20;                          ▼

&#x20;                 Konzistentní prompty

&#x20;                          │

&#x20;                          ▼

&#x20;                      Ilustrace

```

---

# Co budeme potřebovat

## Jazykový model

Doporučuji:

```text

Qwen3 14B

Llama 3.3

Mistral Large

```

Úkol:

- znát svět románu,

- generovat prompty,

- hlídat konzistenci.

---

## Generátor obrázků

Ideálně:

```text

FLUX.1-dev

FLUX.1-schnell

SDXL

```

FLUX v současnosti bývá pro ilustrace knih velmi vhodný.

---

## Open WebUI

Bude sloužit jako rozhraní.

---

# Krok 1: Připrav dokumentaci světa

Nejdůležitější součást.

Vytvoř dokumenty:

```text

Postavy.docx

Lokace.docx

Historie.docx

Magie.docx

Styl_ilustraci.docx

```

---

# Příklad dokumentace postavy

```text

Jméno:

Jeremiah Hawthorne



Věk:

13 let



Vlasy:

čerňavé, lehce kudrnaté



Oči:

modrošedé



Postava:

hubený



Typické oblečení:

tmavě zelený kabát

mosazné knoflíky

kožené boty



Charakter:

zvídavý

odvážný

často působí zamyšleně

```

Čím přesnější dokumentace, tím lepší výsledky.

---

# Krok 2: Vytvoř stylovou bibli

To je něco, co většina lidí přeskočí.

Přitom je to nejdůležitější část.

---

## Příklad

```text

Styl:

Red and White



Barevnost:

červenobílý monochrom



Kontrast:

vysoký



Detail:

střední



Kompozice:

knižní ilustrace



Inspirace:

John Howe

Alan Lee

Arthur Rackham



Atmosféra:

melancholická

tajemná

poloabstraktní



Bez:

anime očí

3D renderů

komiksového vzhledu

```

Tento dokument bude určovat vzhled všech ilustrací.

---

# Krok 3: Nahraj dokumentaci do RAG

V Open WebUI vytvoř:

```text

Knowledge Base

```

Například:

```text

Sixbound Illustration Bible

```

Nahraj:

```text

Postavy.docx

Styl_ilustraci.docx

Bestiar.docx

Lokace.docx

```

---

# Co se stane

Systém vytvoří:

```text

Embeddingy

&#x20;↓

Vektorovou databázi

&#x20;↓

Vyhledávání znalostí

```

Tak bude AI znát svět knihy.

---

# Krok 4: Vytvoř ilustrátora

V Open WebUI vytvoř vlastního asistenta.

Například:

```text

Sixbound Illustrator

```

---

# System Prompt

Například:

```text

Jsi profesionální ilustrátor fantasy románu.



Při vytváření promptů vždy používej

informace nalezené v dokumentaci.



Nikdy nevymýšlej vzhled postavy,

pokud je definován ve znalostní bázi.



Udržuj konzistentní styl.



Dodržuj stylovou bibli.



Výstupem je pouze prompt

pro generátor obrázků FLUX.

```

---

# Krok 5: Generování promptů

Uživatel napíše:

```text

Vygeneruj ilustraci scény,

kde Jeremiah nachází první Honker.

```

AI provede:

```text

Dotaz

&#x20;↓

Vyhledání postav

&#x20;↓

Vyhledání stylu

&#x20;↓

Vyhledání lokace

&#x20;↓

Sestavení promptu

```

Výstup:

```text

young dark-haired boy ...

```

velmi podrobný prompt.

---

# Krok 6: Generování obrázků

Prompt odešleš do:

```text

FLUX

```

nebo

```text

Stable Diffusion

```

Výsledkem je první ilustrace.

---

# Problém: postavy vypadají pokaždé jinak

Tady začíná pokročilejší část.

Bez dalších technik bude Jeremiah pokaždé trochu jiný.

Stejně jako kdyby každý obraz maloval jiný ilustrátor.

---

# Řešení 1: Character Sheets

Pro každou hlavní postavu vytvoř referenční obrázky.

Například:

```text

Jeremiah_front.png

Jeremiah_side.png

Jeremiah_portrait.png

```

---

# Řešení 2: LoRA

Nejlepší metoda.

---

## Co je LoRA?

LoRA je malý doplněk modelu.

Původní FLUX:

```text

FLUX

```

-

```text

Jeremiah_LoRA

```

=

```text

FLUX který zná Jeremiáše

```

---

# Trénování LoRA

Připrav:

```text

20-100 obrázků

```

stejné postavy.

Například:

```text

Jeremiah zepředu

Jeremiah z profilu

Jeremiah běží

Jeremiah sedí

Jeremiah ve škole

```

Poté LoRA natrénuješ.

---

# Výsledek

V promptu napíšeš:

```text

Jeremiah_Hawthorne

```

a model si vybaví konkrétní vzhled.

---

# Řešení 3: Stylová LoRA

Stejně lze naučit i styl.

Například:

```text

Sixbound Style

```

---

## Výsledek

Každá ilustrace:

- stejná barevnost,

- stejná kresba,

- stejná atmosféra.

---

# Krok 7: Automatizace

Po vytvoření LoRA může systém fungovat téměř automaticky.

---

## Dotaz

```text

Nakresli scénu:

Jeremiah, Lydia a Honker

utíkají lesem před Blackheartem.

```

---

## AI provede

```text

1. Vyhledá postavy

2. Vyhledá lokaci

3. Vyhledá styl

4. Vytvoří prompt

5. Připojí LoRA

6. Vygeneruje obrázek

```

---

# Pokročilá varianta

Profesionální workflow často vypadá takto:

```text

Román

&#x20;  ↓

RAG

&#x20;  ↓

Qwen

&#x20;  ↓

Prompt

&#x20;  ↓

FLUX

&#x20;  ↓

První ilustrace

&#x20;  ↓

ControlNet

&#x20;  ↓

Oprava kompozice

&#x20;  ↓

Upscaler

&#x20;  ↓

Finální obrázek

```

---

# Doporučený software

## Nejsnazší

```text

Ollama

Open WebUI

FLUX.1-dev

```

---

## Pokročilejší

```text

Ollama

Open WebUI

ComfyUI

FLUX

LoRA

ControlNet

RealESRGAN

```

---

# Jak by vypadal systém pro Sixbound

Například:

```text

Knowledge Base

&#x20;├── Postavy

&#x20;├── Lokace

&#x20;├── Organizace

&#x20;├── Bestiář

&#x20;├── Historie

&#x20;└── Styl ilustrací



LoRA

&#x20;├── Jeremiah

&#x20;├── Lydia

&#x20;├── Xavier

&#x20;├── Medard

&#x20;├── Blackheart

&#x20;└── Honker



Model

&#x20;├── Qwen3

&#x20;└── FLUX

```

Potom můžeš napsat:

```text

Nakresli scénu z kapitoly 17.

```

a systém:

1. Najde kapitolu.

2. Určí postavy.

3. Určí prostředí.

4. Sestaví prompt.

5. Použije LoRA.

6. Vygeneruje ilustraci ve správném stylu.

---

# Závěr

Pro ilustrace románu nestačí pouze nainstalovat FLUX. Skutečně použitelný systém se skládá ze čtyř vrstev:

```text

Vrstva 1

Znalosti o světě

(RAG)



Vrstva 2

Jazykový model

(Qwen/Llama)



Vrstva 3

Vizuální identita

(LoRA stylu)



Vrstva 4

Konzistence postav

(LoRA postav)

```

Právě kombinace **RAG + Qwen + FLUX + LoRA stylu + LoRA postav** umožňuje vytvořit systém, který dokáže dlouhodobě generovat ilustrace celého románu tak, aby připomínaly práci jednoho skutečného ilustrátora.
