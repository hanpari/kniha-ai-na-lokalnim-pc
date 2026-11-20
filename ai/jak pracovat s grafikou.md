# Důležité pojmy v generování obrázků pomocí AI

Když začneš používat ComfyUI, FLUX nebo Stable Diffusion, velmi rychle narazíš na pojmy jako:

- Checkpoint

- VAE

- LoRA

- ControlNet

- IP Adapter

- Sampler

- Scheduler

- CFG

- Denoising Strength

- Latent

- Upscaler

Začátečník často nerozumí, co která součást dělá.

Ve skutečnosti si celý systém můžeš představit jako digitálního ilustrátora.

---

# Přehled celé architektury

```text

Prompt

&#x20;  ↓

Checkpoint

&#x20;  ↓

LoRA

&#x20;  ↓

ControlNet

&#x20;  ↓

Sampler

&#x20;  ↓

VAE

&#x20;  ↓

Obrázek

&#x20;  ↓

Upscaler

&#x20;  ↓

Finální výstup

```

---

# Checkpoint

Checkpoint je samotný obrazový model.

Představuje "mozek ilustrátora".

Příklady:

```text

FLUX.1-dev

SDXL

Juggernaut

Pony

DreamShaper

```

---

## Co dělá?

Checkpoint určuje:

- kvalitu obrázků,

- styl,

- schopnosti modelu.

---

## Analogie

```text

Checkpoint = ilustrátor

```

Jiný checkpoint znamená jiného ilustrátora.

---

# VAE

VAE znamená:

```text

Variational Auto Encoder

```

Je to jeden z nejméně pochopených pojmů.

---

## Co dělá?

Model ve skutečnosti nekreslí přímo obrázek.

Nejdříve pracuje s komprimovanou verzí.

VAE převádí:

```text

obrázek

↔

latentní prostor

```

---

## Výsledek

Správné VAE:

- lepší barvy,

- lepší kontrast,

- méně artefaktů.

---

## Analogie

```text

Checkpoint = malíř



VAE = oči malíře

```

---

# Latent Space

Latent je "pracovní skica" obrázku.

Model většinu času nepracuje s pixely.

Pracuje s latentem.

---

## Analogie

```text

Latent = tužkový náčrt

```

Teprve VAE jej převede na skutečný obrázek.

---

# Sampler

Sampler určuje:

> Jakým způsobem bude obrázek vytvářen.

---

## Příklady

```text

Euler

Euler A

DPM++

DPM++ 2M

UniPC

```

---

## Praktický dopad

Stejný prompt může vypadat jinak podle sampleru.

---

## Analogie

```text

Sampler = technika malování

```

Například:

- akvarel

- tužka

- olej

Každá vede k trochu jinému výsledku.

---

# Scheduler

Řídí jednotlivé kroky generování.

Příklady:

```text

Linear

Karras

Exponential

Normal

```

---

## Co ovlivňuje?

- rychlost,

- ostrost,

- stabilitu obrazu.

---

## Analogie

```text

Scheduler = plán práce ilustrátora

```

---

# Steps

Určují počet výpočetních kroků.

Například:

```text

20

30

40

60

```

---

## Málo kroků

```text

rychlé

méně detailní

```

---

## Hodně kroků

```text

pomalejší

více detailů

```

---

## Analogie

```text

20 kroků = rychlá skica



50 kroků = dokončený obraz

```

---

# CFG Scale

CFG znamená:

```text

Classifier-Free Guidance

```

Určuje, jak poslušně model dodržuje prompt.

---

## Nízké CFG

```text

3-5

```

Model více improvizuje.

---

## Vysoké CFG

```text

10-15

```

Model více poslouchá.

---

## Analogie

```text

Nízké CFG



"Nakresli něco podobného."



Vysoké CFG



"Nakresli přesně tohle."

```

---

# LoRA

LoRA znamená:

```text

Low Rank Adaptation

```

---

## Co dělá?

Přidává checkpointu nové schopnosti.

Například:

```text

Styl ilustrací

Postava

Oblečení

Pózy

```

---

## Příklad

```text

FLUX

+

Jeremiah LoRA

=

FLUX který zná Jeremiáše

```

---

## Analogie

```text

LoRA = specializovaný kurz

```

---

# ControlNet

Jeden z nejmocnějších nástrojů vůbec.

---

## Co dělá?

Umožňuje přesně řídit kompozici obrázku.

Bez ControlNetu:

```text

Nakresli běžící postavu.

```

Model si vše vymyslí.

---

S ControlNetem:

```text

Tady je předloha.



Dodrž její pózu.

```

---

## Příklady použití

### Póza

```text

OpenPose

```

---

### Hrany

```text

Canny

```

---

### Hloubka

```text

Depth

```

---

### Silueta

```text

LineArt

```

---

## Analogie

```text

ControlNet = režisér

```

Říká ilustrátorovi:

```text

Přesně takhle postavy rozmísti.

```

---

# OpenPose

Speciální typ ControlNetu.

---

## Co dělá?

Rozpozná:

- ruce,

- nohy,

- hlavu,

- trup.

---

## Výsledek

Můžeš přenášet pózy mezi obrázky.

---

## Analogie

```text

Kostra postavy

```

---

# Depth Map

Informace o vzdálenosti objektů.

---

## Co umožňuje?

AI pochopí:

```text

co je vpředu

co je vzadu

```

---

## Analogie

```text

3D mapa prostoru

```

---

# Canny Edge

Vytáhne hrany objektů.

---

## Použití

Pokud chceš zachovat:

```text

budovu

stroj

automobil

```

---

## Analogie

```text

Technický výkres

```

---

# IP Adapter

Velmi moderní technologie.

---

## Co dělá?

Učí model podle referenčního obrázku.

---

Příklad:

Nahraješ:

```text

Jeremiah.png

```

a řekneš:

```text

Nakresli Jeremiaha jako kapitána vzducholodi.

```

---

Model použije vzhled z obrázku.

---

## Analogie

```text

IP Adapter = fotografie herce

```

Ilustrátor ví, koho má kreslit.

---

# FaceID

Varianta IP Adapteru.

---

## Použití

Udržení stejného obličeje.

---

Například:

```text

20 ilustrací téže postavy

```

---

# Inpainting

Úprava části obrázku.

---

## Příklad

Na obrázku je špatná ruka.

Označíš ji.

AI překreslí pouze tuto oblast.

---

## Analogie

```text

Lokální retuš

```

---

# Outpainting

Rozšíření obrázku.

---

## Příklad

Máš:

```text

portrét

```

a chceš:

```text

celou scénu

```

AI dokreslí okolí.

---

# Upscaler

Zvětšení obrázku.

---

## Příklad

Původně:

```text

1024 × 1024

```

Po zvětšení:

```text

4096 × 4096

```

---

## Populární

```text

ESRGAN

RealESRGAN

4xUltraSharp

```

---

## Analogie

```text

Digitální lupa

```

---

# Denoising Strength

Používá se hlavně při img2img.

Určuje:

```text

Jak moc se smí obrázek změnit.

```

---

## Nízká hodnota

```text

0.2

```

Zachová většinu původního obrázku.

---

## Vysoká hodnota

```text

0.8

```

Skoro vše překreslí.

---

## Analogie

```text

0.2 = jemná úprava



0.8 = nový obraz inspirovaný původním

```

---

# Img2Img

Generování z obrázku.

---

## Text2Img

```text

Prompt

↓

Obrázek

```

---

## Img2Img

```text

Obrázek

↓

Prompt

↓

Nový obrázek

```

---

# Seed

Seed je náhodné číslo.

Například:

```text

12345

```

---

Pokud použiješ:

```text

stejný prompt

+

stejný seed

```

dostaneš prakticky stejný obrázek.

---

## Analogie

```text

Seed = výchozí inspirace ilustrátora

```

---

# Workflow

Workflow je samotný graf v ComfyUI.

Například:

```text

Checkpoint

&#x20;     ↓

LoRA

&#x20;     ↓

Prompt

&#x20;     ↓

Sampler

&#x20;     ↓

VAE

&#x20;     ↓

Upscaler

```

---

# Doporučené pořadí učení

Pokud začínáš s ComfyUI a FLUXem:

```text

1. Checkpoint

2. Prompt

3. Seed

4. Steps

5. CFG

6. VAE

7. LoRA

8. Img2Img

9. Inpainting

10. ControlNet

11. IP Adapter

12. Upscaling

13. Trénování LoRA

```

---

# Jednověté shrnutí

| Pojem | Jednoduché vysvětlení |

|---------|---------|

| Checkpoint | Hlavní model |

| VAE | Převodník mezi latentem a obrázkem |

| Latent | Rozpracovaný obraz |

| LoRA | Dodatečné naučené schopnosti |

| ControlNet | Přesné řízení kompozice |

| OpenPose | Řízení pór a kostry postavy |

| Depth | Informace o hloubce scény |

| Canny | Hrany a obrysy |

| IP Adapter | Učení podle referenčního obrázku |

| FaceID | Zachování stejného obličeje |

| Img2Img | Generování z obrázku |

| Inpainting | Oprava části obrázku |

| Outpainting | Rozšíření obrázku |

| Upscaler | Zvětšení rozlišení |

| Sampler | Metoda generování |

| Scheduler | Rozvrh generování |

| CFG | Jak moc poslouchat prompt |

| Seed | Náhodný základ obrázku |

| Workflow | Celý proces v ComfyUI |
