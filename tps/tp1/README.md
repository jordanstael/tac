# Ajoutez dans ce dossier les notebooks pour le TP1

## TP1 — Exploration du corpus CAMille

### 1. Présentation du travail

Dans le cadre du TP1 de Traitement automatique de corpus, nous avons travaillé sur le corpus CAMille. L'objectif était de récupérer automatiquement les documents PDF à partir du site web du cours, puis d'explorer leur contenu.

Pour cette activité, nous avons utilisé Python et les bibliothèques Requests, BeautifulSoup et PyMuPDF.

### 2. Récupération automatique des documents

Nous avons adapté le notebook `s3_scrape.ipynb` afin d'extraire automatiquement les liens vers les documents PDF du site CAMille.

Le programme a identifié 51 liens PDF. Il permet également de télécharger les documents manquants et de vérifier si les fichiers sont déjà présents dans le dossier `data/pdf`, afin d'éviter les téléchargements inutiles.

Lors de notre test, les 51 documents étaient déjà présents. Le programme n'a donc effectué aucun nouveau téléchargement et n'a signalé aucune erreur.

### 3. Exploration du corpus

**Longueur des documents**

L'analyse des 51 fichiers PDF avec PyMuPDF a montré que chaque document contient une seule page. Le corpus comprend donc 51 documents et 51 pages au total.

**Langue des documents**

L'examen des extraits textuels de cinq documents indique que ceux-ci sont principalement rédigés en français. Cependant, certaines erreurs de reconnaissance rendent des passages difficiles à lire.

**Thématiques observées**

Les extraits examinés abordent plusieurs sujets, notamment l'éducation, la politique, les faits divers, les transports et le commerce.

**Qualité de l'OCR**

Les textes extraits présentent de nombreuses erreurs de reconnaissance de caractères. Certains mots sont déformés, des lettres sont remplacées et des passages sont difficilement compréhensibles.

Ces erreurs peuvent compliquer les traitements automatiques, notamment la recherche de mots, l'analyse lexicale et l'identification d'entités nommées.

### 4. Conclusion

Cette première exploration montre que les 51 documents PDF du corpus CAMille sont accessibles et qu'une couche textuelle peut être extraite des cinq documents examinés.

Cependant, la qualité de cette couche textuelle est variable et comporte de nombreuses erreurs. Un travail de nettoyage ou de correction pourrait être nécessaire avant de réaliser certaines analyses linguistiques.

Les observations concernant les langues, les thématiques et la qualité de l'OCR reposent sur cinq documents et ne peuvent pas encore être généralisées à l'ensemble du corpus.