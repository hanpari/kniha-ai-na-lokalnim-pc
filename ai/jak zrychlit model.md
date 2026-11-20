# Jak donutit lokální AI model odpovídat co nejrychleji

Pokud používáš Ollamu, Open WebUI nebo jiný lokální systém, rychlost odpovědi závisí na několika faktorech.

Mnoho lidí hledá:

```text

"Jak model zrychlit?"

```

ale správná otázka je:

```text

"Kde vzniká zdržení?"

```

Existují totiž čtyři hlavní příčiny pomalosti.

---

# 1. Příliš velký model

Nejčastější problém.

Například:

```text

Qwen3 32B

DeepSeek R1 70B

Llama 70B

```

na běžném PC.

---

## Co se děje?

Model musí při každém tokenu počítat miliardy parametrů.

Čím větší model:

```text

více paměti

více výpočtů

nižší rychlost

```

---

## Praktický příklad

Přibližná rychlost:

| Model | Tokenů/s |

|---------|---------:|

| 7B | 30-100 |

| 14B | 20-60 |

| 32B | 5-20 |

| 70B | 1-10 |

---

## Řešení

Místo:

```text

Qwen3 32B

```

zkus:

```text

Qwen3 14B

```

nebo

```text

Qwen3 8B

```

Často získáš:

```text

5× vyšší rychlost

```

za cenu jen malého poklesu kvality.

---

# 2. Model neběží na GPU

To bývá druhý největší problém.

---

## Jak poznat problém?

Například:

```text

Qwen 14B

```

odpovídá:

```text

1–5 tokenů/s

```

---

To téměř jistě znamená:

```text

CPU inference

```

namísto:

```text

GPU inference

```

---

## Kontrola

V Ollamě:

```bash

ollama ps

```

uvidíš například:

```text

PROCESSOR



100% GPU

```

nebo

```text

100% CPU

```

---

## Řešení

Ujisti se, že:

- máš aktuální ovladače NVIDIA

- Ollama detekuje GPU

- model se vejde do VRAM

---

# 3. Model se nevejde do VRAM

Velmi časté.

Například:

```text

RTX 3060

12 GB VRAM

```

a model:

```text

Qwen3 32B

```

---

Co se stane:

```text

část na GPU

část v RAM

```

To bývá extrémně pomalé.

---

## Řešení

Používej model, který se vejde celý do VRAM.

Například:

| VRAM | Doporučení |

|--------|------------|

| 8 GB | 7B model |

| 12 GB | 8B-14B |

| 16 GB | 14B-20B |

| 24 GB | 32B |

---

# 4. Používáš "Thinking model"

Velmi časté u:

```text

DeepSeek R1

QwQ

o1-like modelů

```

---

Takové modely dělají:

```text

skryté přemýšlení

```

než začnou odpovídat.

---

Výsledek:

```text

5-60 sekund ticho

```

a pak teprve odpověď.

---

## Řešení

Použij běžný model:

```text

Qwen Instruct

Llama Instruct

Gemma

```

místo reasoning modelů.

---

# 5. Příliš dlouhý kontext

Pokud Open WebUI posílá:

```text

20 stran historie

```

model musí všechno přečíst.

---

## Symptomy

První token přichází za:

```text

10-30 sekund

```

---

## Řešení

Zkrať:

```text

Context Length

```

Například:

```text

32768

```

→

```text

8192

```

---

# 6. Obří systémový prompt

Někteří uživatelé mají:

```text

5 stran instrukcí

```

v každém agentovi.

---

Model je musí číst při každé otázce.

---

## Špatně

```text

2000 řádků pravidel

```

---

## Lépe

```text

20-50 řádků pravidel

```

---

# 7. RAG vrací příliš mnoho dat

Například:

```text

50 chunků

```

po 1000 tokenech.

---

Model pak dostane:

```text

50000 tokenů

```

a dlouho je čte.

---

## Řešení

Snížit:

```text

Top K

```

například:

```text

10

```

→

```text

3

```

---

# 8. Vypni zbytečné nástroje

Agent někdy před odpovědí:

```text

prohledává web

prohledává PDF

používá Python

```

---

Pak čekáš na:

```text

vyhledání

+

model

```

---

## Řešení

Pro běžný chat používej čistý model.

---

# 9. Použij správnou kvantizaci

Modely existují v různých variantách.

Například:

```text

Q2

Q3

Q4

Q5

Q6

Q8

```

---

## Rychlost

Přibližně:

```text

Q4

```

bývá nejlepší kompromis.

---

Pro domácí použití doporučuji:

```text

Q4_K_M

```

nebo

```text

Q5_K_M

```

---

# 10. Omez délku odpovědí

Mnoho modelů generuje zbytečně dlouhé texty.

---

## Do System Prompt

Přidej:

```text

Odpovídej stručně.



Pokud uživatel nepožaduje detailní vysvětlení,

omezi odpověď na několik odstavců.

```

---

Model potom generuje méně tokenů.

---

# Největší zrychlení v praxi

Pokud máš například:

```text

RTX 3060 12 GB

```

doporučuji:

```text

Qwen3 14B Q4

8192 context

GPU inference

bez reasoning módu

```

oproti:

```text

Qwen3 32B

32768 context

CPU fallback

```

můžeš získat klidně:

```text

10× až 30× vyšší rychlost

```

---

# Moje doporučení pro většinu uživatelů Ollamy

## Chci maximální rychlost

```text

Gemma 7B

Qwen 8B

Mistral 7B

```

---

## Chci kompromis

```text

Qwen3 14B Q4

```

---

## Chci nejlepší kvalitu

```text

Qwen3 32B

Llama 70B

```

ale musíš počítat s výrazně pomalejší odezvou.

---

# Diagnostika za 30 sekund

Spusť:

```bash

ollama ps

```

Pokud uvidíš:

```text

100% CPU

```

našel jsi viníka.

Pokud uvidíš:

```text

100% GPU

```

a model je stále pomalý, bývá problém nejčastěji v:

```text

příliš velkém modelu

obřím kontextu

reasoning modelu

```

Právě tyto tři věci způsobují většinu případů, kdy lokální AI odpovídá desítky sekund až minutu.
