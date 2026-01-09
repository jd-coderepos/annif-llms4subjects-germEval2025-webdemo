# Annif BM-Ensemble Demo Application (Docker-based)

This repository provides a **minimal, reproducible setup** to run **Annif** with selected **GermEval 2025 LLMs4Subjects models** (BM ensemble, Bonsai, MLLM) via **Docker**, and to use Annif through its **built-in Web UI and REST API**.

---

## Overview

You will:

1. Install Docker  
2. Start an Annif Docker container  
3. Download pre-trained GermEval 2025 models from Hugging Face  
4. Launch Annif’s Web UI on `localhost`  
5. Test subject recommendations interactively  

---

## 1. Install Docker

Install **Docker Desktop** from:

https://docs.docker.com/get-docker/

Ensure Docker is running and has **≥ 8 GB RAM** available.

---

## 2. Prepare a local working directory

Create an empty directory, e.g.:

```
C:\path\to\annif-projects
```

This directory will persist all Annif data.

---

## 3. Start the Annif Docker container

```bat
cd /d C:\path\to\annif-projects

docker run -it --rm ^
  -p 5000:5000 ^
  -v "%cd%":/annif-projects ^
  quay.io/natlibfi/annif bash
```

---

## 4. Download GermEval 2025 models

Inside the container:

```bash
cd /annif-projects

annif download --trust-repo "gnd-bm-ensemble-*" NatLibFi/Annif-LLMs4Subjects-GermEval2025-data
annif download --trust-repo "gnd-bonsai-*" NatLibFi/Annif-LLMs4Subjects-GermEval2025-data
annif download --trust-repo "gnd-mllm-*" NatLibFi/Annif-LLMs4Subjects-GermEval2025-data
```

Available models:
https://huggingface.co/NatLibFi/Annif-LLMs4Subjects-GermEval2025-data

---

## 5. Verify installation

```bash
annif list-projects
```

---

## 6. Launch the Web UI

```bash
annif run --host 0.0.0.0 --port 5000
```

Open:
http://localhost:5000

---

## 7. Test predictions

Select:
- `gnd-bm-ensemble-de` (recommended)

Paste text and click **Suggest**.

---

## 8. Screenshots

Add screenshots here:

```
docs/screenshots/
```

---

## References

- Annif: https://github.com/NatLibFi/Annif  
- Models: https://huggingface.co/NatLibFi/Annif-LLMs4Subjects-GermEval2025-data  
