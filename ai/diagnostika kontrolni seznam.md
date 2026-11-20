# AI Diagnostický Checklist

Tento checklist používám při řešení problémů s:

- Ollama

- Open WebUI

- RAG

- Qdrant

- ComfyUI

- FLUX

- Whisper

- XTTS

- AI agenty

Postupuj odshora dolů. Ve většině případů najdeš problém během několika minut.

---

# 1. Je problém skutečně reprodukovatelný?

## Ověř

- [ ] Problém nastává opakovaně.

- [ ] Umím jej vyvolat znovu.

- [ ] Není to jednorázové zpomalení.

## Příklad

```text

První dotaz trvá 30 sekund.

Druhý dotaz trvá 2 sekundy.

```

Pravděpodobně:

```text

Načítání modelu do RAM.

```

---

# 2. Běží model na GPU?

## Kontrola

```bash

ollama ps

```

## Hledej

```text

PROCESSOR

100% GPU

```

## Pokud vidíš

```text

100% CPU

```

pak:

- [ ] Zkontrolovat NVIDIA ovladače

- [ ] Restartovat Ollamu

- [ ] Ověřit CUDA

- [ ] Zkusit menší model

---

# 3. Je GPU skutečně vytížené?

## Kontrola

```bash

nvidia-smi

```

## Dobré hodnoty během generování

```text

GPU Utilization:

70-100 %



VRAM:

obsazena

```

---

## Podezřelé hodnoty

```text

GPU:

0-10 %

```

To často znamená:

- [ ] CPU bottleneck

- [ ] Čekání na RAG

- [ ] Čekání na disk

- [ ] Čekání na síť

---

# 4. Vejde se model do VRAM?

## Kontrola

```bash

nvidia-smi

```

## Příklad

```text

VRAM:

15.8 / 16 GB

```

---

## Varovné příznaky

```text

CUDA Out of Memory



Fallback



Offloading

```

---

## Řešení

- [ ] Menší model

- [ ] Silnější kvantizace

- [ ] Menší kontext

- [ ] Menší rozlišení obrázků

---

# 5. Není model příliš velký?

## Příklad

```text

RTX 3060



Qwen3 32B

```

---

Typické příznaky:

- [ ] 1-5 tokenů za sekundu

- [ ] Dlouhé čekání

- [ ] Swap do RAM

---

## Test

Vyzkoušej:

```text

Qwen3 32B

↓

Qwen3 14B

```

Pokud se rychlost výrazně zvýší:

```text

Problém byl ve velikosti modelu.

```

---

# 6. Není problém v historii chatu?

## Typické příznaky

Na začátku:

```text

2 sekundy

```

Po dlouhé konverzaci:

```text

20 sekund

```

---

## Test

- [ ] Otevři nový chat

- [ ] Zopakuj dotaz

Pokud je rychlý:

```text

Problém je kontext.

```

---

# 7. Není System Prompt příliš dlouhý?

## Špatně

```text

20 stran instrukcí

```

---

## Kontrola

Spočítej:

```text

Kolik má prompt řádků?

```

---

## Doporučení

- [ ] Pod 100 řádků

- [ ] Jasná a krátká pravidla

---

# 8. Není problém v RAG?

## Typické příznaky

Model začne odpovídat až za:

```text

10-30 sekund

```

---

## Kontrola

V logu najdi:

```text

Retrieved documents



Top K

```

---

## Podezřelé

```text

Top K = 20

```

---

## Doporučení

- [ ] Top K = 3 až 5

- [ ] Menší chunk size

- [ ] Lepší embedding model

---

# 9. Našel RAG správné dokumenty?

## Příklad

Dotaz:

```text

Kdo je Honker?

```

---

Vyhledané dokumenty:

```text

Dragons.md

```

---

To je jasný problém.

Model odpovídá špatně, protože dostal špatná data.

---

## Kontrola

- [ ] Jaké dokumenty byly načteny?

- [ ] Jsou relevantní?

- [ ] Obsahují odpověď?

---

# 10. Nezdržuje generování příliš dlouhé odpovědi?

## Příklad

Prompt:

```text

Vysvětli historii lidstva.

```

---

Výsledek:

```text

5000 tokenů odpovědi

```

---

## Řešení

- [ ] Nastavit max tokens

- [ ] Žádat stručnější odpovědi

- [ ] Použít kratší formát

---

# 11. Nečeká aplikace na externí nástroje?

## Kontrola

Používá agent:

- [ ] Web Search

- [ ] Python

- [ ] OCR

- [ ] RAG

- [ ] SQL

---

Příklad:

```text

Dotaz

↓

Prohledání webu

↓

Model

```

---

Model nemusí být problém.

Zdržuje webová vrstva.

---

# 12. Nejsou problémy s diskem?

## Kontrola

Model se načítá dlouho.

---

Porovnej:

```text

SSD

vs

HDD

```

---

## Doporučení

- [ ] NVMe SSD

- [ ] Dostatek místa

---

# 13. Nejsou spuštěné jiné AI procesy?

## Kontrola

```bash

nvidia-smi

```

---

Hledej:

```text

ComfyUI

Whisper

XTTS

Ollama

```

současně.

---

## Doporučení

- [ ] Ukončit nepoužívané modely

- [ ] Uvolnit VRAM

---

# 14. Diagnostika ComfyUI

## Pokud generace obrázku trvá dlouho

Kontrola:

- [ ] Rozlišení

- [ ] Počet LoRA

- [ ] ControlNet

- [ ] Upscaler

- [ ] VRAM

---

## Typické chyby

```text

CUDA Out Of Memory

```

---

## Řešení

- [ ] Menší rozlišení

- [ ] Menší batch size

- [ ] Menší checkpoint

---

# 15. Diagnostika audioknih

## XTTS

Kontroluj:

```text

Inference time

```

---

## FFmpeg

Kontroluj:

```text

Encoding time

```

---

Často není problém v AI.

Problém bývá v exportu.

---

# Nouzový rychlý test (5 minut)

Pokud je systém pomalý:

## Krok 1

```bash

ollama ps

```

GPU nebo CPU?

---

## Krok 2

```bash

nvidia-smi

```

Je GPU vytížené?

---

## Krok 3

Otevři nový chat.

---

## Krok 4

Dočasně vypni RAG.

---

## Krok 5

Vyzkoušej menší model.

---

# Diagnostická tabulka

| Příznak | Pravděpodobná příčina |

|----------|----------|

| 20 s ticho po otázce | Načítání modelu |

| 1-5 tokenů/s | CPU nebo moc velký model |

| GPU 0 % | Čekání na CPU, RAG nebo disk |

| GPU 100 %, pomalu | Model se nevejde do VRAM |

| Dlouhý chat = pomalost | Obří kontext |

| Špatné odpovědi | Vadný RAG |

| Špatné dokumenty | Vadné embeddingy |

| ComfyUI padá | Nedostatek VRAM |

| XTTS pomalé | GPU problém nebo export |

| RAG vrací nesmysly | Špatné chunki nebo Top K |

---

# Zlaté pravidlo

Nejdřív měř:

```text

1. GPU

2. VRAM

3. Kontext

4. RAG

5. Model

```

A teprve potom něco měň.

U většiny AI systémů bývá skutečný problém překvapivě v:

```text

RAG

VRAM

Kontextu

```

a nikoliv v samotném modelu.
