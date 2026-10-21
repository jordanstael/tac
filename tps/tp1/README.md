# TP1 : Exploration et enrichissement du corpus CAMille

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

## Enrichissement géographique avec l'API Nominatim

Dans le cadre de ce TP1, nous avons utilisé l'API Nominatim d'OpenStreetMap afin d'enrichir les informations géographiques présentes dans le corpus CAMille.

L'objectif est d'associer des coordonnées géographiques à certains noms de lieux mentionnés dans les documents historiques.

### Méthodologie

Le traitement a été réalisé en plusieurs étapes :

1. Extraction du texte d'un document PDF du corpus CAMille avec la bibliothèque Python `pymupdf`.
2. Recherche de noms de villes à partir d'une liste prédéfinie et d'expressions régulières.
3. Interrogation de l'API Nominatim pour récupérer les coordonnées géographiques des villes détectées.
4. Enregistrement des résultats dans un fichier CSV.

### Résultats obtenus

L'analyse du document `KB_JB230_1892-08-07_01-0003.pdf` a permis de détecter quatre villes : Bruxelles, Schaerbeek, Anvers et Gand.

Les quatre villes ont été enrichies avec leurs coordonnées géographiques grâce à l'API Nominatim.

Les résultats sont disponibles dans le fichier `camille_lieux_geographiques.csv`, qui contient les colonnes suivantes :

- `document` : nom du document PDF analysé ;
- `lieu` : nom de la ville détectée ;
- `latitude` : latitude obtenue grâce à l'API ;
- `longitude` : longitude obtenue grâce à l'API ;
- `nom_complet` : nom géographique complet renvoyé par Nominatim.

### Limites de la méthode

Cette première expérimentation présente certaines limites. La recherche repose sur une liste prédéfinie de villes et ne permet donc pas de détecter automatiquement tous les lieux du corpus.

De plus, les erreurs de reconnaissance optique des caractères (OCR) peuvent empêcher l'identification de certains noms géographiques. Une correspondance textuelle ne garantit pas non plus que le nom détecté désigne effectivement un lieu.

Enfin, les coordonnées fournies par Nominatim correspondent à des données géographiques actuelles et ne représentent pas nécessairement la situation historique des lieux mentionnés dans les documents.

### Fichiers du TP1

- `s3_scrape.ipynb` : automatisation du téléchargement des documents PDF du corpus CAMille.
- `s2_api.ipynb` : extraction des noms de villes et enrichissement géographique avec l'API Nominatim.
- `camille_lieux_geographiques.csv` : fichier contenant les résultats de l'enrichissement.
- `README.md` : documentation du travail réalisé.