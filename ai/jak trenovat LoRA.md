# Jak natrénovat vlastní LoRA lokálně krok za krokem

Tento návod je určen pro začátečníka, který chce naučit AI:

- konkrétní postavu z románu,

- vlastní výtvarný styl,

- ilustrátorský rukopis,

- konkrétní objekt,

- konkrétní prostředí.

Například:

- Jeremiah Hawthorne

- Lydia Carver

- Honker

- Sixbound styl

- vlastní červenobílý Red and White styl

Budeme používat:

```text

Windows

FLUX

ComfyUI

AI Toolkit (Ostris)

NVIDIA GPU

```

Protože v roce 2026 jde o nejjednodušší a zároveň nejkvalitnější cestu pro FLUX LoRA.

---

# Co je LoRA v praxi?

Představ si model FLUX jako absolventa umělecké školy.

Umí kreslit skoro všechno.

Neumí ale tvoji postavu.

LoRA je krátký specializační kurz.

Situace po tréninku:

```text

FLUX

+

Jeremiah LoRA

=

FLUX který zná Jeremiáše

```

Přitom nemusíš přeučovat celý model.

---

# Jak silný počítač potřebuješ?

## Rozumné minimum

```text

RTX 3060 12 GB

32 GB RAM

100 GB volného místa

```

---

## Komfortní sestava

```text

RTX 4070 Ti Super

RTX 4080

RTX 4090



64 GB RAM

```

---

# Krok 1: Vyber, co chceš učit

Existují dva hlavní typy LoRA.

## Character LoRA

Naučí konkrétní postavu.

Například:

```text

Jeremiah Hawthorne

```

---

## Style LoRA

Naučí vizuální styl.

Například:

```text

Red and White

```

---

# Krok 2: Připrav dataset

To je nejdůležitější fáze.

Špatný dataset = špatná LoRA.

---

## Character LoRA

Ideálně:

```text

20–100 obrázků

```

Stejná postava.

Různé:

- pózy,

- výrazy,

- osvětlení,

- vzdálenosti.

---

## Příklad

Ne pouze:

```text

20 portrétů

```

ale:

```text

portrét

celá postava

profil

běh

sed

skok

chůze

```

---

# Krok 3: Konzistence

Na všech obrázcích musí být stejná osoba.

Pokud jednou přidáš:

```text

blond vlasy

```

a jindy:

```text

černé vlasy

```

LoRA se zmate.

---

# Krok 4: Pojmenování obrázků

Každý obrázek musí mít textový popis.

Například:

```text

001.jpg

001.txt



002.jpg

002.txt

```

---

## Obsah popisu

```text

sxb_jeremiah,

young boy,

dark wavy hair,

green coat,

full body

```

---

# Proč token?

Protože potřebuješ unikátní klíč.

Například:

```text

sxb_jeremiah

```

nebo:

```text

sxb_honker

```

Po tréninku budeš používat právě tento výraz.

---

# Krok 5: Instalace AI Toolkit

Dnes je nejjednodušší řešení:

```text

Ostris AI Toolkit

```

---

## Instalace

```bash

git clone https://github.com/ostris/ai-toolkit

```

Poté:

```bash

pip install -r requirements.txt

```

---

# Krok 6: Stažení FLUX modelu

Potřebuješ základní model.

Například:

```text

FLUX.1-dev

```

LoRA se učí nad konkrétním modelem.

---

# Krok 7: Konfigurace tréninku

Nejdůležitější parametry.

---

## Rank

Určuje sílu LoRA.

Typicky:

```text

16

```

nebo

```text

32

```

---

### Menší

```text

8

```

Menší soubor.

Méně detailů.

---

### Větší

```text

64

```

Více detailů.

Riziko přeučení.

---

# Krok 8: Learning Rate

Rychlost učení.

Typicky:

```text

0.0001

```

---

Pokud je příliš vysoká:

```text

LoRA se přeučí.

```

Pokud příliš nízká:

```text

prakticky se nic nenaučí.

```

---

# Krok 9: Epochs

Kolikrát dataset projde tréninkem.

Začátečník:

```text

10-20 epoch

```

---

Pokročilý:

```text

20-50 epoch

```

---

# Krok 10: Spuštění tréninku

Proces vypadá:

```text

Obrázky

&#x20;    ↓

Captiony

&#x20;    ↓

FLUX

&#x20;    ↓

Výpočet GPU

&#x20;    ↓

LoRA

```

---

# Jak dlouho to trvá?

Přibližně:

| GPU | Čas |

|-------|------|

| RTX 3060 | 1–6 hodin |

| RTX 4070 | 30–180 minut |

| RTX 4090 | 15–90 minut |

Záleží na datasetu.

---

# Krok 11: Průběžné checkpointy

Každých několik epoch se uloží:

```text

epoch_5.safetensors



epoch_10.safetensors



epoch_15.safetensors

```

Nejlepší bývá otestovat více verzí.

Ne vždy je poslední nejlepší.

---

# Krok 12: Testování

Po dokončení:

```text

Jeremiah_LoRA.safetensors

```

nakopíruješ do:

```text

ComfyUI/models/loras

```

---

# Použití

Prompt:

```text

sxb_jeremiah



standing in forest

fantasy illustration

```

Pokud LoRA funguje správně, objeví se výcviková postava.

---

# Jak poznat přeučení?

Typické příznaky:

- pořád stejná póza,

- stejný výraz,

- stejné pozadí,

- artefakty.

Příklad:

```text

Model umí jen jednu fotografii.

```

To znamená, že se naučil obrázky kopírovat místo generalizace.

---

# Jak poznat nedoučení?

Příznaky:

- postava se mění,

- špatná barva vlasů,

- špatný obličej.

Pak je potřeba:

```text

více epoch

```

nebo

```text

lepší dataset

```

---

# Jak trénovat stylovou LoRA

Postup je téměř stejný.

Jen místo postavy používáš:

```text

50–500 obrázků

```

ve stejném stylu.

Například:

```text

červenobílé ilustrace

```

---

# Stylový token

Například:

```text

sixbound_style

```

Potom v promptu:

```text

sixbound_style,

Jeremiah in forest,

fantasy illustration

```

---

# Nejlepší workflow pro román

Pro dlouhou sérii bych doporučil:

```text

LoRA 1

Jeremiah



LoRA 2

Lydia



LoRA 3

Xavier



LoRA 4

Honker



LoRA 5

Sixbound Style

```

Poté můžeš kombinovat:

```text

<lora:jeremiah:1>



<lora:lydia:1>



<lora:sixbound_style:0.8>

```

a získáš velmi konzistentní ilustrace.

---

# Nejčastější chyba začátečníků

Začátečníci si myslí:

```text

Potřebuji více obrázků.

```

Ve skutečnosti většinou potřebují:

```text

lepší obrázky

```

20 kvalitních obrázků bývá často lepších než 200 nekvalitních.

---

# Doporučení pro Sixbound

Pro tvůj případ bych netrénoval vše najednou.

Pořadí:

```text

1. Sixbound Style LoRA

2. Jeremiah

3. Lydia

4. Honker

5. Xavier

6. Blackheart

```

Jakmile budou hotové tyto LoRA, dokážeš generovat ilustrace celých kapitol s velmi vysokou vizuální konzistencí a bez nutnosti znovu popisovat vzhled každé postavy v každém promptu.
