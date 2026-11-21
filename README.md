# Fooocus Colab (fixed)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/alimemonzx/fooocus-colab/blob/main/fooocus_colab.ipynb)

A working version of the official [Fooocus](https://github.com/lllyasviel/Fooocus) Colab notebook for current Google Colab runtimes (Python 3.12).

1. Click **Open in Colab** above.
2. Runtime → Change runtime type → **T4 GPU**.
3. Run the cell. If Colab asks to restart the session, click **Cancel**.
4. Open the `gradio.live` link it prints.

The notebook clones the latest Fooocus on every run, so you always get the current upstream code.

## Why the official notebook breaks

- **NumPy vs CuPy:** Fooocus needs NumPy 1.26, but Colab's CuPy is built for NumPy 2, so startup fails with `numpy.core.multiarray failed to import`. The fix removes CuPy, which Fooocus doesn't need.
- **Gradio 3 vs new FastAPI:** Fooocus's Gradio 3.41 crashes on Colab's newer FastAPI with `unhashable type: 'dict'`. The fix pins FastAPI 0.104.1, Starlette 0.27.0 and Pydantic 1.10.19.

See [lllyasviel/Fooocus#4189](https://github.com/lllyasviel/Fooocus/issues/4189) for the upstream report.
