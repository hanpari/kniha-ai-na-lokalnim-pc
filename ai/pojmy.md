# Důležité pojmy v AI: LoRA, Fine-Tuning, Embeddingy a další

Když se začneš zajímat o lokální AI, Ollamu nebo generování obrázků pomocí FLUX či Stable Diffusion, velmi rychle narazíš na pojmy jako:

- LoRA

- Fine-Tuning

- Embedding

- Checkpoint

- Quantization

- Context Window

- RAG

- Inference

- Prompt Engineering

Začátečníkovi to často připadá jako cizí jazyk. Ve skutečnosti jde jen o různé součásti AI ekosystému.

---

# Checkpoint

Začněme nejzákladnějším pojmem.

Checkpoint je samotný natrénovaný model.

Například:

```text

llama3:8b

qwen3:14b

deepseek-r1

flux1-dev

```

Tohle všechno jsou checkpointy.

Můžeš si checkpoint představit jako:

> Hotový mozek AI.

Obsahuje všechny naučené parametry.

---

## Analogie

```text

Mozek člověka = Checkpoint

```

---

# Fine-Tuning

Fine-tuning znamená další učení již existujícího modelu.

Například vezmeš model:

```text

Llama 3

```

a doučíš ho:

- na právní dokumenty,

- na medicínu,

- na programování,

- na vlastní knížky.

Vznikne specializovaná verze.

---

## Analogie

Představ si středoškoláka.

Už má obecné vzdělání.

Pak jde na medicínu.

To je fine-tuning.

---

# LoRA

LoRA znamená:

```text

Low Rank Adaptation

```

Je to jeden z nejdůležitějších pojmů v moderní AI.

---

## Proč vznikla?

Představ si model:

```text

70 miliard parametrů

```

Jeho přetrénování může stát miliony korun.

LoRA umožňuje změnit chování modelu bez úpravy celého modelu.

---

## Jak funguje?

Původní model zůstane nedotčen.

Vedle něj vznikne malý balíček změn.

Například:

```text

Llama3

&#x20;  +

LoRA

=

Nové chování

```

---

## Velikost

Model:

```text

40 GB

```

LoRA:

```text

100 MB

```

nebo

```text

500 MB

```

Proto se LoRA používá velmi často.

---

## Příklad

Máš generátor obrázků FLUX.

Naučíš jej kreslit:

```text

styl mangy

```

Nemusíš vytvářet nový model.

Vytvoříš pouze LoRA.

---

## Analogie

```text

Model = člověk



LoRA = nové brýle

```

Pořád je to stejný člověk.

Jen se dívá trochu jinak.

---

# DreamBooth

DreamBooth je speciální druh trénování obrazových modelů.

Používá se hlavně k naučení konkrétní osoby nebo objektu.

Například:

- tvůj obličej,

- tvůj pes,

- tvoje auto.

Po dokončení můžeš napsat:

```text

Můj pes jako astronaut.

```

a AI ví, jak tvůj pes vypadá.

---

# Embedding

Embedding převádí význam na čísla.

Například:

```text

pes

kočka

štěně

```

budou ve vektorovém prostoru blízko sebe.

Model pak nemusí hledat přesně stejná slova.

Může hledat podobný význam.

---

## Analogie

Představ si mapu města.

Pojmy s podobným významem bydlí ve stejné čtvrti.

---

# Vektorová databáze

Embeddingy je potřeba někam uložit.

K tomu slouží:

- Chroma

- Qdrant

- FAISS

- Milvus

Jejich úkolem je najít:

```text

nejpodobnější informaci

```

a to velmi rychle.

---

# RAG

Retrieval Augmented Generation.

RAG umožňuje modelu používat externí dokumenty.

---

## Bez RAG

```text

Dotaz

&#x20;↓

Model

&#x20;↓

Odpověď

```

---

## S RAG

```text

Dotaz

&#x20;↓

Vyhledání dokumentů

&#x20;↓

Model

&#x20;↓

Odpověď

```

---

## Praktický příklad

Máš:

```text

500 PDF souborů

```

a zeptáš se:

> Co se píše o motoru V8?

Systém:

1. Najde správné PDF.

2. Vybere relevantní pasáže.

3. Přidá je do promptu.

4. AI odpoví.

---

# Prompt

Prompt je všechno, co pošleš modelu.

Například:

```text

Vysvětli fotosyntézu.

```

je prompt.

---

## Prompt Engineering

Prompt Engineering znamená:

> Umění pokládat otázky AI.

Například:

Špatně:

```text

Napiš článek.

```

Lépe:

```text

Napiš článek pro středoškoláky

v rozsahu 1000 slov

s příklady a obrázky.

```

---

# System Prompt

Speciální neviditelný prompt.

Například:

```text

Jsi učitel fyziky.

```

nebo

```text

Odpovídej česky.

```

Určuje chování modelu.

---

# Token

Token je základní jednotka textu.

Model nevidí:

```text

kočka

```

Model vidí:

```text

1837

```

nebo několik tokenů.

Veškerá komunikace probíhá pomocí tokenů.

---

# Kontextové okno

Kontextové okno určuje:

```text

Kolik tokenů si model pamatuje.

```

Například:

| Model | Kontext |

|---------|---------:|

| Starší GPT | 8k |

| Moderní model | 128k |

| Některé modely | 1M+ |

---

# Inference

Inference je samotné odpovídání.

Když model dostane prompt:

```text

Co je gravitace?

```

začne počítat odpověď.

Tomuto procesu se říká inference.

---

# Inference Engine

Program, který model skutečně spouští.

Příklady:

- Ollama

- llama.cpp

- vLLM

- TensorRT-LLM

---

## Analogie

```text

Model = motor



Inference Engine = převodovka

```

---

# Quantization

Kvantizace zmenšuje model.

Například:

```text

Původní:

70 GB



Po kvantizaci:

35 GB

```

Výsledkem je:

- méně paměti,

- rychlejší běh,

- menší nároky na GPU.

---

# MoE (Mixture of Experts)

Moderní technika používaná velkými modely.

Místo jednoho obřího mozku má model více specialistů.

Například:

```text

Expert 1 = matematika

Expert 2 = programování

Expert 3 = jazyky

Expert 4 = logika

```

Při každém dotazu se aktivují pouze relevantní experti.

---

# Hallucination

Halucinace označuje situaci, kdy AI vytvoří neexistující informaci.

Například:

- smyšlenou knihu,

- neexistující citaci,

- vymyšlenou webovou stránku.

Není to chyba v programu.

Je to důsledek toho, že model předpovídá text místo skutečného ověřování faktů.

---

# Agent

Agent je AI, která umí používat nástroje.

Například:

```text

AI

&#x20;↓

Web

&#x20;↓

Kalendář

&#x20;↓

Python

&#x20;↓

E-mail

```

Běžný model pouze píše.

Agent dokáže konat.

---

# Multimodální model

Multimodální model pracuje s více typy dat.

Například:

- text,

- obrázky,

- zvuk,

- video.

Můžeš mu ukázat fotografii a položit otázku.

---

# Nejdůležitější pojmy jednou větou

| Pojem | Jednoduše |

|---------|---------|

| Checkpoint | Samotný model |

| Fine-Tuning | Další výuka modelu |

| LoRA | Malý balíček změn modelu |

| Embedding | Převod významu na čísla |

| Vektorová databáze | Úložiště embeddingů |

| RAG | Vyhledávání v dokumentech |

| Prompt | Otázka pro AI |

| System Prompt | Skryté instrukce |

| Token | Kousek textu |

| Kontextové okno | Paměť modelu |

| Inference | Proces odpovídání |

| Inference Engine | Program spouštějící model |

| Quantization | Zmenšení modelu |

| MoE | Skupina specializovaných expertů |

| Hallucination | Vymyšlená informace |

| Agent | AI používající nástroje |

---

# Závěr

Pokud dnes používáš Ollamu, Open WebUI nebo generátory obrázků jako FLUX a Stable Diffusion, můžeš si celý ekosystém představit takto:

```text

Checkpoint      = mozek

LoRA            = nová specializace

Prompt          = otázka

Token           = slovo rozdělené na části

Kontext         = krátkodobá paměť

Embedding       = význam převedený na čísla

RAG             = knihovník

Inference       = přemýšlení

Inference Engine= motor modelu

Agent           = AI s rukama a nástroji

```

Jakmile pochopíš těchto 10-15 pojmů, budeš rozumět většině diskusí o moderní AI, Ollamě, Open WebUI, FLUXu, Stable Diffusion i velkých jazykových modelech.
