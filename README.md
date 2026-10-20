![Made with Python](https://forthebadge.com/images/badges/made-with-python.svg)
![Jupyter](https://img.shields.io/badge/-Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

```ascii
██████╗ ██████╗ ██████╗ ██╗  ██╗
██╔══██╗██╔══██╗██╔══██╗██║ ██╔╝
██████╔╝██║  ██║██████╔╝█████╔╝
██╔══██╗██║  ██║██╔══██╗██╔═██╗
██║  ██║██████╔╝██║  ██║██║  ██╗
╚═╝  ╚═╝╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝
       by Hex (@RemiH06)          version 0.1
```

![MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)

## Overview

### General Description

RDRK es una exploración inicial de los datos del hackathon *Rare Disease, Real Kid: MVA Hackathon 2026* (Sage Bionetworks, Hugging Face y MVA Society). El reto parte de un caso clínico real con sospecha o diagnóstico de aneuploidía variegada mosaico (MVA), un síndrome de inestabilidad cromosómica asociado a mutaciones bialélicas en `BUB1B`, `CEP57` o `TRIP13`, y pide priorizar variantes a partir de secuenciación de genoma completo (~85 GB de datos).

El repo contiene un solo notebook, `exploracion.ipynb`, que cubre los primeros pasos: listar los archivos del dataset, descargar el VCF ya llamado y el documento de fenotipo, revisar el encabezado del VCF, hacer QC básico (FILTER, SNVs contra indels, razón Ti/Tv), contar variantes por cromosoma y filtrar por posición los tres genes candidatos conocidos.

**Estado: cerrado.** El proyecto se detuvo aquí. No hubo recursos de cómputo ni almacenamiento para sostener los datos, y el conocimiento de genómica clínica necesario para un enfoque sólido de priorización (anotación con VEP o SnpEff, ClinVar, gnomAD, HPO) rebasó lo que se tenía a la mano. Se deja público como registro de una exploración de un problema de esta naturaleza y complejidad, no como una solución. El notebook no llegó a ejecutarse completo y se publica sin salidas.

```diff
- Este repo NO incluye datos. El dataset está gateado y sus términos prohíben redistribuirlo y exigen borrarlo al terminar el hackathon.
- Las coordenadas de los genes candidatos están en GRCh38 y no se verificaron contra la build real del VCF.
- No es una herramienta de diagnóstico ni debe usarse con fines clínicos.
```

## Installation

1. Pide acceso al dataset [`SageBio/mva-hackathon-2026-data`](https://huggingface.co/datasets/SageBio/mva-hackathon-2026-data) con tu cuenta de Hugging Face y acepta sus términos.
2. Instala las dependencias:
   ```bash
   pip install jupyter pandas matplotlib huggingface_hub python-docx
   ```
3. Inicia sesión en Hugging Face:
   ```bash
   hf auth login
   ```
4. Abre `exploracion.ipynb` y ejecútalo en orden. Los archivos se descargan a `data/`, que está en `.gitignore`.

## Features

- Listado de archivos del dataset con su tamaño, sin necesidad de autenticación.
- Descarga del VCF (~315 MB), su índice y el documento de fenotipo clínico.
- Lectura del encabezado del VCF para identificar build de referencia, caller y anotación.
- QC básico: conteo por FILTER, SNVs contra indels y razón Ti/Tv.
- Variantes por cromosoma.
- Filtro por posición de `BUB1B`, `CEP57` y `TRIP13`.

## Future Features

Quedaron como ideas, sin planes de implementarlas:

- Anotar el VCF completo con VEP o SnpEff y cruzar con ClinVar y gnomAD.
- Ampliar la lista de genes del punto de control mitótico (`CENPE`, `CENPF`, `NDC80`, `ZWILCH`).
- Cruzar los términos del fenotipo contra HPO para armar una lista de candidatos priorizada.
- Re-llamar variantes desde los FASTQ si se sospecha que el VCF omitió alguna.

## Autoría

por Hex ([@RemiH06](https://github.com/RemiH06))
