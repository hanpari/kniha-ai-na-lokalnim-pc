# Jak funguje Ollama

Pokud jsi někdy používal ChatGPT, Copilot nebo Claude, komunikoval jsi s AI běžící někde na vzdálených serverech. **Ollama** funguje jinak. Umožňuje spouštět moderní jazykové modely přímo na vlastním počítači.

Díky tomu můžeš používat AI i bez internetu, bez měsíčního předplatného a s plnou kontrolou nad svými daty.

Tento článek vysvětluje, jak Ollama funguje, krok za krokem.

---

# Co je Ollama?

Ollama je program, který umožňuje jednoduše stahovat a spouštět lokální AI modely.

Můžeš si ho představit jako:

- Steam pro hry,

- Docker pro kontejnery,

- nebo správce balíčků pro AI modely.

Místo her nebo programů stahuješ modely jako:

- Llama

- Qwen

- Gemma

- DeepSeek

- Mistral

- Phi

---

# Proč Ollama vznikla?

Spuštění jazykového modelu není úplně jednoduché.

Bez Ollamy bys musel:

1. Najít správný model.

2. Stáhnout několik gigabajtů dat.

3. Nainstalovat potřebné knihovny.

4. Nakonfigurovat inferenční engine.

5. Ručně model spustit.

Ollama většinu této práce automatizuje.

Stačí napsat:

```bash

ollama run llama3

```

a model se stáhne i spustí.

---

# Jak vypadá celá architektura?

```text

&#x20;         Uživatel

&#x20;              │

&#x20;              ▼

&#x20;         WebUI nebo

&#x20;       příkazová řádka

&#x20;              │

&#x20;              ▼

&#x20;           Ollama

&#x20;              │

&#x20;     ┌────────┴────────┐

&#x20;     ▼                 ▼

&#x20;  AI Model         GPU/CPU

&#x20;     │                 │

&#x20;     └────────┬────────┘

&#x20;              ▼

&#x20;          Odpověď

```

---

# 1. Instalace Ollamy

První krok je instalace programu.

Po instalaci vznikne služba běžící na pozadí.

Její úkol je jednoduchý:

- spravovat modely,

- načítat modely do paměti,

- přijímat požadavky,

- vracet odpovědi.

Můžeš si ji představit jako malý server běžící ve tvém počítači.

---

# 2. Stažení modelu

Když zadáš:

```bash

ollama run qwen3

```

Ollama zjistí:

```text

Je model nainstalovaný?

```

Pokud ne:

```text

1. Najde model

2. Stáhne soubory

3. Uloží je na disk

4. Připraví je k použití

```

Stažení proběhne pouze jednou.

Příště už se model načte z lokálního disku.

---

# 3. Uložení modelu

Modely bývají velmi velké.

Typické velikosti:

| Model | Velikost |

|---------|---------:|

| 3B | 2–3 GB |

| 7B | 4–6 GB |

| 14B | 8–12 GB |

| 32B | 20+ GB |

Písmeno **B** znamená miliardy parametrů.

Například:

```text

7B

=

7 miliard parametrů

```

Parametry si můžeš představit jako znalosti uložené v neurální síti.

---

# 4. Načtení modelu do paměti

Po spuštění Ollama:

```text

Načte model z disku

&#x20;          ↓

Přenese ho do RAM

&#x20;          ↓

Připraví GPU nebo CPU

&#x20;          ↓

Čeká na dotazy

```

Právě tento krok bývá nejpomalejší.

Po načtení je komunikace mnohem rychlejší.

---

# 5. Prompt

Po zadání otázky:

```text

Jak funguje spalovací motor?

```

se vytvoří takzvaný **prompt**.

Prompt obsahuje:

- systémové instrukce,

- historii konverzace,

- aktuální otázku.

Například:

```text

Jsi učitel fyziky.



Uživatel:

Jak funguje spalovací motor?

```

---

# 6. Tokenizace

Počítač nerozumí textu přímo.

Nejprve ho musí rozdělit na tokeny.

Například:

```text

Kočka sedí na střeše.

```

se může změnit na:

```text

[521]

[810]

[45]

[1129]

[76]

```

Model pracuje s čísly, ne se slovy.

---

# 7. Inferenční engine

Tady začíná skutečná práce modelu.

Inferenční engine postupně počítá:

```text

Jaké bude další slovo?

```

Například:

```text

Kočka sedí na ...

```

Možné pokračování:

```text

střeše = 75 %

plotě = 12 %

židli = 8 %

stromě = 3 %

```

Model vybere jednu z variant.

Poté proces zopakuje.

---

# 8. Generování tokenů

Model nevytváří celé věty najednou.

Píše po malých částech.

Například:

```text

Kočka

```

↓

```text

Kočka sedí

```

↓

```text

Kočka sedí na

```

↓

```text

Kočka sedí na střeše.

```

Proto často vidíš, jak text postupně přibývá.

---

# 9. GPU a CPU

Výpočty může provádět:

## CPU

Klasický procesor.

Výhody:

- funguje na každém počítači,

- není potřeba grafická karta.

Nevýhody:

- bývá výrazně pomalejší.

---

## GPU

Grafická karta.

Výhody:

- násobně rychlejší výpočty,

- vyšší rychlost generování.

Nevýhody:

- omezení velikostí VRAM.

Například:

| Grafika | VRAM |

|----------|-------|

| RTX 3060 | 12 GB |

| RTX 4070 | 12 GB |

| RTX 4090 | 24 GB |

Čím větší model, tím více paměti potřebuje.

---

# 10. Kvantizace

Velké modely jsou obrovské.

Proto se používá kvantizace.

Původní model:

```text

70 GB

```

Po kvantizaci:

```text

40 GB

```

nebo

```text

20 GB

```

Ztráta kvality bývá malá, ale úspora paměti značná.

Proto většina modelů v Ollamě používá kvantizované verze.

---

# 11. API server

Ollama nekomunikuje jen s terminálem.

Současně nabízí API.

To znamená, že jiné programy mohou model používat.

Například:

```text

Open WebUI

AnythingLLM

LibreChat

VS Code

Aider

Continue

```

všechno může komunikovat s Ollamou.

---

# 12. Open WebUI

Mnoho lidí používá Ollamu společně s Open WebUI.

V takovém případě architektura vypadá takto:

```text

&#x20;         Uživatel

&#x20;              │

&#x20;              ▼

&#x20;        Open WebUI

&#x20;              │

&#x20;         HTTP API

&#x20;              │

&#x20;              ▼

&#x20;           Ollama

&#x20;              │

&#x20;              ▼

&#x20;           Model

&#x20;              │

&#x20;              ▼

&#x20;          Odpověď

```

Open WebUI je pouze grafické rozhraní.

Ollama je server.

Model provádí samotné výpočty.

---

# 13. RAG v Ollamě

Ollama umí spolupracovat i s dokumenty.

Příklad:

Nahraješ:

- PDF

- Word

- Markdown

- Zdrojové kódy

Systém:

1. Rozdělí dokument.

2. Vytvoří embeddingy.

3. Uloží je do databáze.

4. Vyhledává relevantní části.

5. Posílá je modelu.

Tak vzniká lokální firemní chatbot.

---

# Typický průchod požadavku

Při zadání:

> Vysvětli Newtonovy zákony.

proběhne:

```text

1. Dotaz od uživatele

&#x20;               ↓

2. Open WebUI

&#x20;               ↓

3. Ollama API

&#x20;               ↓

4. Načtený model

&#x20;               ↓

5. Tokenizace

&#x20;               ↓

6. Výpočet odpovědi

&#x20;               ↓

7. Generování tokenů

&#x20;               ↓

8. Zobrazení odpovědi

```

---

# Jak si Ollamu představit?

Nejjednodušší analogie je tato:

| Součást | Přirovnání |

|----------|------------|

| Ollama | Operační systém pro AI modely |

| Model | Mozek |

| GPU | Motor |

| Open WebUI | Ovládací panel |

| Prompt | Zadání úkolu |

| Tokeny | Slova rozřezaná na kousky |

| API | Telefonní linka mezi programy |

| RAG | Knihovník vyhledávající informace |

---

# Závěr

Ollama není AI model. Je to služba, která modely spravuje, načítá do paměti a zpřístupňuje je ostatním programům.

Pro začátečníka je nejjednodušší si představit:

```text

Open WebUI = volant

Ollama     = převodovka

GPU        = motor

Model      = řidičova hlava

```

Teprve všechny tyto části dohromady vytvářejí lokální AI asistenta, který běží přímo na tvém počítači bez nutnosti používat cloudové služby.
