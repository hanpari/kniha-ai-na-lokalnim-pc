# Co je AI model, jak vzniká a jak funguje

Když dnes používáš ChatGPT, Copilot, Claude, Gemini nebo lokální modely přes Ollamu, ve skutečnosti komunikuješ s takzvaným **AI modelem**.

Mnoho lidí si představuje AI jako nějakou digitální bytost, která myslí podobně jako člověk. Ve skutečnosti je AI model obrovská matematická struktura obsahující miliardy čísel, která se naučila předpovídat další slova, obrázky nebo jiné informace.

Tento článek vysvětluje, co je AI model, jak vzniká, jak funguje a jaké druhy modelů dnes existují.

---

# Co je AI model?

AI model je program, který byl natrénován na velkém množství dat.

Jeho úkolem je nalézat vzory a souvislosti.

Například si všimne, že:

```text

Kočka často mňouká.

Pes často štěká.

Auto často jezdí.

```

Po miliardách podobných příkladů začne chápat vztahy mezi slovy a pojmy.

Neučí se ovšem jako člověk.

Nechápe význam přímo.

Učí se statistické vztahy.

---

# Jednoduchá analogie

Představ si studenta, který přečetl miliony knih.

Zapamatoval si:

- slovní zásobu,

- větné konstrukce,

- fakta,

- vztahy mezi pojmy.

Pak dostane otázku:

> Jak funguje letadlo?

Nezačne hledat odpověď v knize.

Vytvoří ji z toho, co se naučil.

Přesně tak funguje AI model.

---

# Co tvoří AI model?

Uvnitř modelu jsou takzvané parametry.

Parametry jsou čísla.

Hodně čísel.

Opravdu hodně.

Například:

| Model | Počet parametrů |

|---------|----------------|

| 1B | 1 miliarda |

| 7B | 7 miliard |

| 13B | 13 miliard |

| 70B | 70 miliard |

| 405B | 405 miliard |

Parametry představují znalosti modelu.

Čím více parametrů, tím více vztahů si model dokáže zapamatovat.

Není to ale jediné měřítko kvality.

---

# Jak AI model vzniká?

Vývoj probíhá ve třech hlavních fázích.

```text

Sběr dat

&#x20;     ↓

Trénování

&#x20;     ↓

Doladění

```

---

# 1. Sběr dat

První krok je získání dat.

Mohou pocházet z:

- knih,

- článků,

- Wikipedie,

- dokumentace,

- zdrojových kódů,

- vědeckých prací,

- diskusních fór.

Vývojáři často shromáždí biliony slov.

Takové množství textu by člověk četl tisíce let.

---

# 2. Příprava dat

Ne všechna data jsou kvalitní.

Proto se odstraňují:

- duplicity,

- spam,

- reklamy,

- poškozené texty,

- bezcenný obsah.

Například:

```text

KUPTE SI TOHNLE!!!

```

může být odstraněno.

Cílem je vytvořit co nejkvalitnější trénovací sadu.

---

# 3. Trénování modelu

To je nejnáročnější část.

Model dostává věty typu:

```text

Kočka sedí na ...

```

a snaží se odhadnout další slovo.

Například:

```text

střeše

```

Když se splete:

```text

vrtulníku

```

upraví své parametry.

Tento proces se opakuje miliardkrát.

---

## Jak si to představit?

Představ si žáka, který dostává jeden diktát za druhým.

Po každé chybě dostane opravu.

Postupně se zlepšuje.

Přesně to dělá AI model během tréninku.

---

# 4. Neuronová síť

Většina moderních AI používá neuronové sítě.

Inspirace pochází z biologického mozku.

Nejde však o skutečný mozek.

Spíše o matematickou síť propojených výpočtů.

Zjednodušeně:

```text

Vstup

&#x20; ↓

Výpočty

&#x20; ↓

Výpočty

&#x20; ↓

Výpočty

&#x20; ↓

Výsledek

```

Moderní modely obsahují desítky až stovky vrstev.

---

# 5. Transformer

Transformer je architektura, která způsobila současnou AI revoluci.

Všechny známé modely používají nějakou variantu transformeru:

- GPT

- Claude

- Gemini

- Llama

- Qwen

- Mistral

- DeepSeek

Transformer umožňuje sledovat vztahy mezi slovy i na velmi dlouhé vzdálenosti.

Například ve větě:

```text

Pavel vzal knihu, otevřel ji a přečetl první kapitolu.

```

model chápe, že:

```text

ji = knihu

```

i když jsou mezi nimi další slova.

---

# Jak model odpovídá?

Po položení otázky:

```text

Proč je obloha modrá?

```

model provede:

```text

Otázka

&#x20;  ↓

Tokenizace

&#x20;  ↓

Neuronová síť

&#x20;  ↓

Pravděpodobnosti

&#x20;  ↓

Nový token

&#x20;  ↓

Další token

&#x20;  ↓

Odpověď

```

---

# Co jsou tokeny?

Model nepracuje přímo se slovy.

Pracuje s tokeny.

Například:

```text

fotografie

```

může být rozděleno na:

```text

foto

graf

ie

```

Nebo na číselné reprezentace.

Model tedy ve skutečnosti manipuluje s čísly.

---

# Proč se AI někdy mýlí?

AI není databáze.

Nevyhledává fakta.

Generuje nejpravděpodobnější pokračování.

Někdy vytvoří:

- nepřesnost,

- smyšlené jméno,

- neexistující zdroj,

- nesprávný výpočet.

Tomu se říká:

## Halucinace

Model vytvoří informaci, která zní věrohodně, ale není pravdivá.

---

# Jaké druhy AI modelů existují?

Dnes existuje několik hlavních kategorií.

---

# 1. Jazykové modely (LLM)

Nejznámější skupina.

Pracují především s textem.

Příklady:

- GPT

- Claude

- Llama

- Mistral

- Qwen

- DeepSeek

Použití:

- psaní článků,

- překlady,

- programování,

- shrnování.

---

# 2. Modely pro obrázky

Generují obrázky.

Například:

```text

Nakresli hrad v zimě.

```

Model vytvoří nový obrázek.

Zástupci:

- Stable Diffusion

- FLUX

- Midjourney

- DALL-E

---

# 3. Modely pro video

Generují videa.

Například:

```text

Drak letí nad horami.

```

Výsledkem může být krátká animace.

Příklady:

- Sora

- Veo

- Kling

---

# 4. Modely pro zvuk

Pracují s hlasem a hudbou.

Dokážou:

- mluvit,

- přepisovat řeč,

- vytvářet hudbu.

Příklady:

- Whisper

- ElevenLabs

- Suno

---

# 5. Multimodální modely

Pracují s více typy dat současně.

Mohou:

- číst text,

- analyzovat obrázky,

- poslouchat zvuk.

Například:

```text

Nahraj fotografii motoru a popiš závadu.

```

Multimodální model zvládne obojí.

---

# 6. Specializované modely

Jsou zaměřeny na konkrétní oblast.

Například:

- medicínu,

- právo,

- chemii,

- programování.

Jejich cílem bývá vyšší přesnost v daném oboru.

---

# Open source vs. uzavřené modely

## Open Source

Model lze stáhnout a provozovat lokálně.

Příklady:

- Llama

- Qwen

- Gemma

- Mistral

Výhody:

- zdarma,

- kontrola nad daty,

- lokální provoz.

---

## Uzavřené modely

Běží pouze na serverech firmy.

Příklady:

- GPT

- Claude

- Gemini

Výhody:

- často vyšší výkon,

- jednodušší použití.

Nevýhody:

- závislost na poskytovateli.

---

# Jak si AI model představit?

Nejlepší analogie je tato:

| Součást | Přirovnání |

|----------|------------|

| Trénovací data | Učebnice |

| Trénování | Studium |

| Parametry | Zapamatované znalosti |

| Prompt | Otázka od učitele |

| Tokeny | Slova rozdělená na části |

| Transformer | Způsob myšlení modelu |

| Inferenční engine | Proces odpovídání |

| Model | Mozek |

---

# Závěr

AI model není myslící bytost ani databáze. Je to obrovská matematická struktura složená z miliard parametrů, která byla natrénována na obrovském množství dat.

Když položíš otázku, model nehledá odpověď jako ve slovníku. Místo toho krok za krokem předpovídá nejpravděpodobnější pokračování na základě všeho, co se během tréninku naučil.

Právě tato jednoduchá myšlenka:

```text

Předpověz další token.

```

stojí za většinou moderní umělé inteligence, od ChatGPT přes Copilot až po lokální modely běžící v Ollamě.
