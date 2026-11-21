# Fooocus Colab (fixed)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alimemonzx/fooocus-colab/blob/main/fooocus_colab.ipynb)

A working version of the official [Fooocus](https://github.com/lllyasviel/Fooocus) Colab notebook for current Google Colab runtimes (Python 3.12). Anyone can use it, and it runs in your own Google account.

## How to start

1. Click **Open in Colab** above and sign in with your Google account.
2. **Runtime → Change runtime type → T4 GPU** (the free GPU works).
3. Click ▶ on the code cell. If Colab warns that the notebook wasn't authored by Google, click **Run anyway**.
4. Wait about 8–10 minutes while it installs and downloads models.
5. Open the `https://….gradio.live` link printed at the end. Keep the Colab tab open while you use Fooocus.

Your run, your images and any edits stay in your own Colab account. Nothing is saved back to this repo. To keep your own editable copy of the notebook, use **File → Save a copy in Drive**.

Colab deletes everything when the session ends, so download any images you want to keep.

The notebook downloads the latest Fooocus on every run, so you always get the current upstream code.

## Why the official notebook breaks

Fooocus was built for Python 3.10–3.11 and packages from 2024. Colab keeps upgrading its own Python (3.13 as of late 2026) and preinstalled packages, so the official notebook fails in different ways over time: NumPy/CuPy import errors, Gradio/FastAPI `unhashable type: 'dict'` crashes, and packages that can't build on Python 3.13.

This notebook doesn't use Colab's Python at all. It uses [uv](https://github.com/astral-sh/uv) to download Python 3.11 and install the exact versions in [`requirements-colab.txt`](requirements-colab.txt) (torch 2.1.0 with CUDA 12.1, Gradio 3.41.2 with a compatible FastAPI, NumPy 1.26.4) into a separate environment, then runs the latest Fooocus there. Colab updates can't change that environment.

See [lllyasviel/Fooocus#4189](https://github.com/lllyasviel/Fooocus/issues/4189) for the upstream report.
