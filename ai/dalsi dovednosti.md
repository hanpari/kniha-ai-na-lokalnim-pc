# Co ještě je dobré vědět o AI, když už zvládáš základy

Pokud už rozumíš:

- Ollama

- Open WebUI

- RAG

- LoRA

- Fine-Tuningu

- ComfyUI

- FLUX

- Agentům

pak ses dostal asi na úroveň, kde většina uživatelů končí.

Další posun už není ani tak o instalaci nových nástrojů, ale o pochopení hlubších principů.

---

# 1. AI je především práce s daty

Začátečníci si myslí:

```text

Lepší model = lepší výsledek

```

Zkušení uživatelé vědí:

```text

Lepší data = lepší výsledek

```

---

Například:

```text

Průměrný model

+

výborný RAG

```

často porazí:

```text

Špičkový model

+

špatná data

```

---

# 2. Většina problémů není problém AI

Příklad:

```text

Agent odpovídá špatně.

```

Začátečník:

```text

Potřebuji lepší model.

```

---

Zkušený uživatel:

```text

Mám správná data?

Mám správný prompt?

Mám správný RAG?

```

---

Velmi často je problém zde:

```text

Dokumentace

```

a ne v modelu.

---

# 3. Nauč se používat menší modely

Mnoho lidí honí:

```text

70B

120B

400B

```

---

V praxi se často používá:

```text

7B

14B

```

protože:

- odpovídají rychle,

- stojí méně,

- snadno se nasazují.

---

Profesionálové často preferují:

```text

rychlejší model

```

před

```text

o trochu chytřejším modelem

```

---

# 4. Prompt Engineering je stále důležitý

Přestože jsou modely lepší než před několika lety.

---

Špatně:

```text

Napiš článek.

```

---

Lépe:

```text

Napiš článek.



Cílová skupina:

Středoškoláci



Rozsah:

1500 slov



Struktura:

Úvod

Tři hlavní kapitoly

Závěr



Použij příklady.

```

---

Rozdíl bývá obrovský.

---

# 5. Nauč se pracovat s workflow

To je jeden z největších rozdílů mezi hobby uživatelem a profesionálem.

---

Začátečník:

```text

Prompt

↓

Výsledek

```

---

Pokročilý:

```text

Prompt

↓

Vyhledání dat

↓

Analýza

↓

Ověření

↓

Generování

↓

Export

```

---

Právě workflow vytváří hodnotu.

---

# 6. Nauč se logování

Pokud něco nefunguje:

```text

proč?

```

---

Měj log:

```text

Prompt

Použitý model

Použité dokumenty

Čas odpovědi

Použité nástroje

```

---

To dramaticky urychluje ladění.

---

# 7. Nauč se měřit kvalitu

Velmi důležité.

---

Místo:

```text

Zdá se mi lepší.

```

měj:

```text

Přesnost

Chybovost

Rychlost

Náklady

```

---

Například:

```text

Model A

95 %



Model B

92 %

```

Pak se rozhoduje mnohem snáze.

---

# 8. AI není databáze

To je jedno z nejčastějších nedorozumění.

---

Model:

```text

negarantuje fakta

```

---

Proto existují:

```text

RAG

Databáze

Web Search

```

---

Čím více pracuješ s fakty:

```text

finance

technika

věda

právo

```

tím méně bys měl spoléhat čistě na model.

---

# 9. Nauč se API

To je moment, kdy se z uživatele stává vývojář AI systémů.

---

Například:

```text

OpenAI API

Ollama API

Anthropic API

Google API

```

---

Jakmile zvládneš API:

```text

můžeš propojit cokoliv s čímkoliv

```

---

# 10. Nauč se JSON

Možná nejpodceňovanější znalost.

---

Agenti mezi sebou často komunikují takto:

```json

{

&#x20; "task": "generate_image",

&#x20; "character": "Jeremiah",

&#x20; "style": "Red and White"

}

```

---

JSON se objevuje úplně všude:

```text

API

RAG

Agenti

Automatizace

Konfigurace

```

---

# 11. Bezpečnost

Jakmile začneš používat AI ve firmě:

---

Řešíš:

```text

Osobní údaje

GDPR

Přístupová práva

Smlouvy

Interní dokumenty

```

---

Proto mnoho firem používá:

```text

Ollama

Open WebUI

Lokální RAG

```

místo cloudových služeb.

---

# 12. Multimodalita je budoucnost

Dnes už AI nepracuje jen s textem.

---

Běžný agent umí:

```text

Číst PDF

Vidět obrázky

Poslouchat zvuk

Vytvářet video

Generovat řeč

```

---

Proto je dobré chápat:

```text

Whisper

FLUX

XTTS

YOLO

```

stejně dobře jako LLM.

---

# 13. Největší hodnota je automatizace

Největší úsporu času nepřináší:

```text

lepší odpověď

```

ale:

```text

méně práce

```

---

Například:

```text

Příchozí PDF

↓

AI analýza

↓

Vytvoření shrnutí

↓

PDF report

↓

Odeslání e-mailem

```

bez zásahu člověka.

---

# 14. Agenti budou důležitější než modely

Před několika lety bylo hlavní téma:

```text

Jaký model používáš?

```

---

Dnes stále více platí:

```text

Jaké workflow používáš?

```

---

Rozdíl bývá:

```text

10 % model

90 % proces

```

---

# 15. Uč se řešit konkrétní problémy

Největší chyba samouků:

---

Naučí se:

```text

Transformer

Attention

Tokenizaci

Embeddings

```

do obrovských detailů.

---

Ale neumí vytvořit:

```text

Firemního asistenta

Audioknižního agenta

Systém pro Sixbound

Kontrolu kvality výrobků

```

---

Nejrychleji rosteš, když máš konkrétní projekt.

---

# Co bych se učil dál na tvém místě

Vzhledem k tomu, že tě zajímá:

- Sixbound

- RAG

- Audioknihy

- Agenti

- Ilustrace

- Průmyslové využití AI

viděl bych další krok takto:

```text

1. Python

2. Ollama API

3. JSON

4. Docker

5. Qdrant

6. n8n

7. Langflow

8. ComfyUI

9. XTTS

10. YOLO

```

Po zvládnutí těchto oblastí už nebudeš pouze uživatel AI, ale budeš schopný stavět vlastní lokální AI systémy od chatovacích asistentů přes audioknihy až po průmyslové aplikace.
