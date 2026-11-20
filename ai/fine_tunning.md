\# Fine-Tuning v praxi: textové modely a generování obrázků



Jedna z největších nejasností kolem AI je, že lidé používají slovo \*\*fine-tuning\*\* pro několik různých věcí.



Ve skutečnosti existují tři úrovně:



```text

1\. RAG

2\. LoRA Fine-Tuning

3\. Full Fine-Tuning

```



A každá řeší jiný problém.



\---



\# Kdy použít co?



\## Chci, aby model znal moje dokumenty



Použij:



```text

RAG

```



Příklad:



```text

Firemní směrnice

PDF dokumentace

Sixbound Lore

```



\---



\## Chci změnit styl odpovědí



Použij:



```text

LoRA Fine-Tuning

```



Příklad:



```text

Mluv jako učitel.

Piš jako právník.

Používej terminologii Sixbound.

```



\---



\## Chci vytvořit vlastní model



Použij:



```text

Full Fine-Tuning

```



To je ale řádově složitější.



\---



\# TEXTOVÉ MODELY



Například:



```text

Qwen

Llama

Mistral

Gemma

```



\---



\# Příklad 1: Sixbound asistent



Představ si, že chceš model naučit odpovídat na otázky o Sixbound.



\---



\## Špatný přístup



Vytvořit dataset:



```text

Kdo je Jeremiah?

Kdo je Lydia?

Kdo je Xavier?

```



a fine-tunovat.



\---



Proč je to špatně?



Protože při každé změně světa musíš model učit znovu.



\---



\## Lepší řešení



```text

RAG

```



\---



Struktura:



```text

Postavy.md

Bestiar.md

Historie.md

Magie.md

```



\---



Dotaz:



```text

Kdo je Jeremiah?

```



Model si najde odpověď v dokumentaci.



\---



\# Příklad 2: Změna stylu odpovědí



To už je úloha pro fine-tuning.



Chceš:



```text

Stručné odpovědi

Formální odpovědi

Výukový styl

```



\---



\## Dataset



```json

{

&#x20;"messages":\[

&#x20;  {

&#x20;    "role":"user",

&#x20;    "content":"Co je derivace?"

&#x20;  },

&#x20;  {

&#x20;    "role":"assistant",

&#x20;    "content":"Derivace vyjadřuje okamžitou rychlost změny funkce."

&#x20;  }

&#x20;]

}

```



\---



Další příklad:



```json

{

&#x20;"messages":\[

&#x20;  {

&#x20;    "role":"user",

&#x20;    "content":"Co je integrál?"

&#x20;  },

&#x20;  {

&#x20;    "role":"assistant",

&#x20;    "content":"Integrál lze chápat jako součet nekonečně malých příspěvků."

&#x20;  }

&#x20;]

}

```



\---



Takových dvojic potřebuješ:



```text

100+

```



pro první experiment.



\---



Lépe:



```text

1000+

```



\---



\# Trénování pomocí LLaMA Factory



\## Dataset



```text

sixbound.jsonl

```



\---



\## Model



```text

qwen3:8b

```



\---



\## LoRA nastavení



```text

Rank: 16



Alpha: 32



Learning Rate:

1e-4

```



\---



\## Výsledek



Vznikne:



```text

sixbound\_style\_lora

```



\---



\# Jak poznat, že se fine-tuning povedl?



Před:



```text

Odpověď:

obecná

```



\---



Po:



```text

Odpověď:

v požadovaném stylu

```



\---



\# Nejčastější chyba



Lidé chtějí model naučit fakta.



Například:



```text

Kdo je Xavier?

```



\---



To není ideální použití fine-tuningu.



\---



Fine-tuning:



```text

mění chování

```



\---



RAG:



```text

dodává znalosti

```



\---



\# GRAFICKÉ MODELY



Například:



```text

FLUX

SDXL

Stable Diffusion

```



\---



Tady je situace jiná.



U obrázků se LoRA používá mnohem častěji.



\---



\# Příklad 1: Stylová LoRA



Řekněme, že chceš naučit svůj:



```text

Red and White styl

```



\---



\## Dataset



Například:



```text

100 obrázků

```



v podobném stylu.



\---



Vlastnosti:



```text

Červenobílý monochrom

Vysoký kontrast

Přírodní motivy

```



\---



\## Trénink



Použiješ:



```text

AI Toolkit

```



nebo



```text

Kohya SS

```



\---



Výsledek:



```text

red\_white\_style.safetensors

```



\---



\# Použití



Prompt:



```text

red\_white\_style



castle on the hill

```



\---



Model začne používat naučený styl.



\---



\# Příklad 2: LoRA postavy



Například:



```text

Jeremiah Hawthorne

```



\---



\## Dataset



20-100 obrázků stejné postavy.



\---



Důležité:



```text

Stejný obličej

Stejné vlasy

Stejný věk

```



\---



\## Caption



Například:



```text

sxb\_jeremiah



young boy

dark hair

green coat

```



\---



Po tréninku:



```text

sxb\_jeremiah

standing in forest

```



\---



a model ví, jak má vypadat.



\---



\# Příklad 3: LoRA nestvůry



Například:



```text

Honker

```



\---



Dataset:



```text

50 obrázků Honkera

```



\---



Prompt:



```text

sxb\_honker

```



\---



Výsledek:



Konzistentní vzhled napříč ilustracemi.



\---



\# Příklad 4: LoRA organizace



Například:



```text

Mafie → Syndicate

```



\---



Můžeš naučit:



```text

uniformy

znaky

oblečení

symboliku

```



\---



Tím zajistíš konzistentní vizuální identitu.



\---



\# Trénink FLUX LoRA krok za krokem



\## 1



Připrav obrázky.



Například:



```text

50 PNG

```



\---



\## 2



Přidej popisky:



```text

001.jpg

001.txt



002.jpg

002.txt

```



\---



\## 3



Spusť AI Toolkit.



\---



\## 4



Nastav:



```text

Rank:

16

```



\---



```text

Epochs:

10-20

```



\---



\## 5



Trénuj.



\---



Výsledek:



```text

my\_style.safetensors

```



\---



\# Jak poznat přeučení?



\## Text



Model:



```text

opakuje stále stejné fráze

```



\---



\## Obrázky



Model:



```text

generuje neustále stejnou pózu

```



\---



Příčina:



```text

Příliš mnoho epoch.

```



\---



\# Jak poznat nedoučení?



\## Text



Model ignoruje styl.



\---



\## Obrázky



Postava se mění.



\---



Příčina:



```text

Málo epoch

nebo malý dataset

```



\---



\# Doporučený workflow pro Sixbound



\## Text



```text

RAG



Postavy

Historie

Bestiář

Magie

```



\---



\## Styl odpovědí



```text

LoRA Fine-Tuning

```



\---



\## Ilustrace



```text

Style LoRA



\+

Character LoRA

```



\---



\## Audioknihy



```text

Character Bible

\+

XTTS

```



\---



\# Pravidlo, které ti ušetří týdny práce



Před každým tréninkem si polož otázku:



```text

Chci model naučit znalosti?



nebo



Chci změnit chování?

```



Pokud chceš \*\*znalosti\*\*, téměř vždy použij:



```text

RAG

```



Pokud chceš \*\*styl, osobnost nebo vzhled\*\*, použij:



```text

LoRA Fine-Tuning

```



Až teprve ve chvíli, kdy potřebuješ vytvořit skutečně nový specializovaný model, má smysl řešit plný fine-tuning.

