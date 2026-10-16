# Transformers-gitan

Un Transformer encodeur-décodeur codé from scratch (PyTorch) qui répond comme Homer Simpson.
Tout est dans `notebook.ipynb`.

[![Ouvrir dans Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Pacotiber/Transformers-gitan/blob/master/notebook.ipynb)

## Installation

```bash
uv sync
```

## Dataset

Les dialogues des Simpsons (en français) ne sont pas dans ce dépôt. Pour les récupérer :

```bash
git clone https://huggingface.co/datasets/Romaindcrl/Simpsons data/Simpsons
```

Le modèle entraîné (`homer_transformer.pt`) n'est pas versionné non plus : il est trop gros pour GitHub.
