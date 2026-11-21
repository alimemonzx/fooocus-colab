# Fooocus Colab (fixed)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alimemonzx/fooocus-colab/blob/main/fooocus_colab.ipynb)

A working version of the official [Fooocus](https://github.com/lllyasviel/Fooocus) Colab notebook for current Google Colab runtimes (Python 3.12). Anyone can use it, and it runs in your own Google account.

## How to start

1. Click **Open in Colab** above and sign in with your Google account.
2. **Runtime → Change runtime type → T4 GPU** (the free GPU works).
3. Click ▶ on the code cell. If Colab warns that the notebook wasn't authored by Google, click **Run anyway**.
4. Wait about 5–8 minutes while it installs and downloads models.
5. Open the `https://….gradio.live` link printed at the end. Keep the Colab tab open while you use Fooocus.

Your run, your images and any edits stay in your own Colab account. Nothing is saved back to this repo. To keep your own editable copy of the notebook, use **File → Save a copy in Drive**.

Colab deletes everything when the session ends, so download any images you want to keep.

The notebook downloads the latest Fooocus on every run, so you always get the current upstream code.

## Why the official notebook breaks

- **NumPy vs CuPy:** Fooocus needs NumPy 1.26, but Colab's CuPy is built for NumPy 2, so startup fails with `numpy.core.multiarray failed to import`. The fix removes CuPy, which Fooocus doesn't need.
- **Gradio 3 vs new FastAPI:** Fooocus's Gradio 3.41 crashes on Colab's newer FastAPI with `unhashable type: 'dict'`. The fix pins FastAPI 0.104.1, Starlette 0.27.0 and Pydantic 1.10.19.

See [lllyasviel/Fooocus#4189](https://github.com/lllyasviel/Fooocus/issues/4189) for the upstream report.
