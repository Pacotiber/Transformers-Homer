# Transformers-gitan

Un Transformer encodeur-décodeur codé de zéro avec PyTorch, entraîné pour répondre comme Homer Simpson, en
français. Tout le code est dans `notebook.ipynb`.

[![Ouvrir dans Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Pacotiber/Transformers-gitan/blob/master/notebook.ipynb)

## Comment ça marche

Le modèle est d'abord pré-entraîné sur des sous-titres de films et de séries, pour apprendre à répondre à une
réplique en français, puis affiné sur les dialogues des Simpsons pour prendre le style d'Homer. On lui écrit
ensuite une phrase comme si on était Marge, et il répond.

L'entraînement se fait sur Google Colab avec un GPU T4 : il suffit d'ouvrir le notebook avec le bouton
ci-dessus et de tout exécuter. Les modèles sont sauvegardés dans Google Drive.

## Installation en local

```bash
uv sync
```

## Données

Le notebook télécharge lui-même ce dont il a besoin dans `data/` :

- les dialogues des Simpsons, depuis le dataset Hugging Face [Romaindcrl/Simpsons](https://huggingface.co/datasets/Romaindcrl/Simpsons) ;
- environ 200 Mo de sous-titres français du corpus OpenSubtitles ([OPUS](https://opus.nlpl.eu/)), pour le pré-entraînement.

Ni les données ni les modèles entraînés (`*.pt`) ne sont versionnés, ils sont trop gros pour GitHub.
