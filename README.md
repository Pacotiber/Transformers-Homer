# Transformers-Homer

Un transformer entraîné pour parler comme Homer Simpson. C'est-à-dire beaucoup de bêtises et de donuts.


## Réglages :

Le modèle a 11,1 millions de paramètres avec une taille d'embedding de 256.
Il utilise le tokenizer de tiktoken.
J'ai d'abord commencé avec un très gros modèle d'environ 100 millions de paramètres.
Les résultats étaient très mauvais : le modèle parlait à peine français.
J'ai donc diminué le nombre de paramètres.

Au départ, le modèle avait trois tables qui faisaient le même travail :
- `encoder.token_embedding_table` (token -> vecteur) ;
- `decoder.token_embedding_table` (token -> vecteur, pour les mêmes tokens) ;
- `decoder.lm_head` (vecteur -> score de chaque token, le chemin inverse).

J'ai donc tout mis en commun. J'ai aussi diminué la taille des embeddings.

## Dataset :

Le dataset de pré-entraînement est un dataset de sous-titres de films trouvé sur Hugging Face : https://huggingface.co/datasets/sentence-transformers/parallel-sentences-opensubtitles.
Le dataset de fine-tuning a aussi été récupéré sur Hugging Face. Il s'agit de toutes les répliques de centaines d'épisodes des Simpsons, sous la forme : `Marge: ... Homer: ... Bart: ...`

## Comment ça marche :

Pour un résultat un peu plus concluant, le modèle est d'abord pré-entraîné sur des sous-titres de films et de séries pour apprendre à répondre à des questions en français. Ensuite, il est fine-tuné sur les répliques d'Homer pour essayer d'avoir son style.
Pour le tester, on lui envoie une phrase qui commence par « Marge: » pour que le modèle comprenne à qui il s'adresse. Puis on l'appelle en commençant sa réponse par « Homer: » pour qu'il comprenne qu'il doit répondre comme Homer. Il pourrait tout à fait répondre comme un autre personnage des Simpsons.
L'entraînement s'est fait sur Google Colab avec un GPU T4.

## Résultat :

Bien que le résultat ne soit pas super concluant, il reste quand même intéressant.
Le modèle arrive à faire des phrases, même si elles ne sont pas super logiques. Sur certains outputs, on reconnaît aussi le style d'Homer.
