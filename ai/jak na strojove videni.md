# Jak vytvořit aplikaci se strojovým viděním pro použití v průmyslu

Strojové vidění (Machine Vision) je jedna z oblastí AI, která má v průmyslu skutečně měřitelné ekonomické přínosy.

Typické úlohy:

- kontrola kvality výrobků,

- detekce vad,

- měření rozměrů,

- třídění dílů,

- čtení QR kódů,

- čtení výrobních štítků,

- rozpoznávání objektů na dopravníku,

- kontrola montáže,

- počítání kusů.

Tento článek vysvětluje nejen jak aplikaci vytvořit, ale také jaké technologie použít a jak celý systém funguje.

---

# Co je strojové vidění?

Laicky:

```text

Kamera

+

Počítač

+

AI

=

Digitální inspektor

```

Místo člověka kontroluje výrobky kamera.

---

# Typický příklad

Výroba šroubků.

Každý kus musí mít:

- správný tvar,

- správný závit,

- správnou délku.

---

Dnes:

```text

Výrobek

&#x20;↓

Člověk

&#x20;↓

OK / NOK

```

---

Se strojovým viděním:

```text

Výrobek

&#x20;↓

Kamera

&#x20;↓

AI

&#x20;↓

OK / NOK

```

---

# Jak vypadá celý systém?

```text

Výrobek

&#x20;   │

&#x20;   ▼

&#x20;Kamera

&#x20;   │

&#x20;   ▼

&#x20;Počítač

&#x20;   │

&#x20;   ▼

&#x20;AI Model

&#x20;   │

&#x20;┌──┴───┐

&#x20;▼      ▼

&#x20;OK    NOK

```

---

# Krok 1: Definice problému

Nejprve musíš přesně vědět, co chceš kontrolovat.

Například:

## Dobré zadání

```text

Najdi praskliny na hliníkovém odlitku.

```

---

## Špatné zadání

```text

Hledej problémy.

```

AI neumí kontrolovat neurčité věci.

---

# Krok 2: Výběr kamery

V průmyslu bývá kamera důležitější než AI.

---

## Začátečnický projekt

Stačí:

```text

USB kamera

Logitech

Průmyslová webkamera

```

---

## Skutečný průmysl

Používají se:

```text

Basler

Hikrobot

IDS

Teledyne

```

---

# Krok 3: Osvětlení

Největší chyba začátečníků.

Myslí si:

```text

Lepší AI

=

lepší systém

```

Ve skutečnosti bývá problém zde:

```text

Špatné světlo

```

---

Typické pravidlo:

```text

50 % úspěchu = osvětlení

30 % kamera

20 % AI

```

---

# Krok 4: Sběr dat

Potřebuješ fotografie.

---

# Dobré kusy

Například:

```text

5000 fotografií

```

---

# Vadné kusy

Například:

```text

500 fotografií

```

---

Čím více variant, tím lépe.

---

# Krok 5: Označení dat

Musíš AI ukázat:

```text

Co hledat.

```

---

# Nástroje

Nejčastěji:

```text

Label Studio

CVAT

Roboflow

```

---

# Příklad

Na fotografii označíš:

```text

prasklina

škrábanec

deformace

```

---

Vznikne dataset.

---

# Jaké typy úloh existují?

---

# 1. Klasifikace

Nejjednodušší.

Otázka:

```text

Je výrobek dobrý?

```

Výstup:

```text

OK

```

nebo

```text

NOK

```

---

# Příklad

Kontrola lahví.

```text

Víčko nasazené?

```

Ano nebo ne.

---

# 2. Detekce objektů

Otázka:

```text

Kde se nachází problém?

```

---

Výstup:

```text

Škrábanec zde

```

s rámečkem.

---

Nejběžnější model:

```text

YOLO

```

---

# 3. Segmentace

Mnohem přesnější.

AI označí každý pixel.

---

Příklad:

```text

Přesná plocha koroze

```

---

Použití:

- lakovny,

- hutnictví,

- automobilový průmysl.

---

# 4. Měření

AI určí:

```text

průměr

délku

šířku

```

---

Použití:

```text

strojírenství

```

---

# Nejdůležitější AI modely

---

# YOLO

Nejpoužívanější model ve strojovém vidění.

---

Umí:

```text

detekovat objekty

počítat objekty

sledovat objekty

```

---

Příklad:

```text

Šroub

Matice

Ložisko

```

---

# Segment Anything (SAM)

Model od Meta.

---

Použití:

```text

Automatické označování objektů.

```

Velmi užitečné při přípravě datasetů.

---

# OpenCV

Není AI.

Je to knihovna pro práci s obrazem.

---

Umí například:

```text

Načíst obrázek

Filtrovat obraz

Měřit vzdálenosti

Pracovat s kamerou

```

---

V průmyslu se používá téměř vždy.

---

# Typická architektura

Pro kontrolu kvality.

```text

Basler kamera

&#x20;      │

&#x20;      ▼

&#x20;   OpenCV

&#x20;      │

&#x20;      ▼

&#x20;     YOLO

&#x20;      │

&#x20;      ▼

&#x20;Rozhodnutí

&#x20;      │

&#x20;  ┌───┴───┐

&#x20;  ▼       ▼

&#x20;OK       NOK

```

---

# Jak aplikaci vytvořit

---

# Varianta 1 - Bez AI

Pokud je problém jednoduchý.

Například:

```text

Je díra přítomna?

```

Použij:

```text

OpenCV

```

---

Výhoda:

```text

rychlé

jednoduché

spolehlivé

```

---

# Varianta 2 - S AI

Pokud hledáš:

```text

praskliny

deformace

škrábance

```

Použij:

```text

YOLO

```

---

# Trénování modelu

Postup:

```text

Fotografie

&#x20;     ↓

Označení

&#x20;     ↓

Dataset

&#x20;     ↓

YOLO

&#x20;     ↓

Trénování

&#x20;     ↓

Model

```

---

# Hardware

Pro vývoj:

```text

RTX 3060

RTX 4060

RTX 4070

```

---

Pro výrobu často stačí:

```text

Mini PC

Intel NUC

Průmyslový počítač

```

---

# Jak vznikne aplikace

Python:

```text

Kamera

&#x20;↓

OpenCV

&#x20;↓

YOLO

&#x20;↓

GUI

```

---

Například:

```text

+---------------------+

| Kamera              |

|                     |

| [obraz]             |

|                     |

| Stav: OK            |

+---------------------+

```

---

# Jak distribuovat program

Po dokončení:

```bash

pyinstaller app.py --onefile

```

Vznikne:

```text

inspection.exe

```

---

Lze jej instalovat na výrobní počítače.

---

# Pokročilá verze

Po zvládnutí základů.

---

Přidáš:

```text

Databázi

PLC komunikaci

ERP systém

MES systém

Dashboard

```

---

Architektura:

```text

Kamera

&#x20;  │

&#x20;  ▼

YOLO

&#x20;  │

&#x20;  ▼

Průmyslové PLC

&#x20;  │

&#x20;  ▼

Výrobní linka

```

---

# Jak bych postupoval jako úplný začátečník

Pořadí učení:

```text

1. Python

2. OpenCV

3. NumPy

4. YOLO

5. Label Studio

6. Trénování YOLO

7. PyQt nebo CustomTkinter

8. PyInstaller

9. PLC komunikace

10. Průmyslové kamery

```

---

# Minimální funkční projekt

Například:

```text

USB kamera

+

Python

+

OpenCV

+

YOLO

+

PyInstaller

```

Takový systém dokáže:

- rozpoznávat součástky,

- hledat vady,

- počítat kusy,

- třídit výrobky,

a představuje velmi dobrý první krok do průmyslového strojového vidění.
