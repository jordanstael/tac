# TP2 : Extraction d'information – Le Soir en 1960

### 1. Présentation du travail

Dans le cadre du TP2 de Traitement automatique de corpus, nous avons appliqué quatre techniques d'extraction d'information au sous-corpus CAMille (journal Le Soir). Nous avons travaillé sur une seule année : 1960.

Nous avons choisi cette année car elle est très riche pour la Belgique. Le Congo devient indépendant le 30 juin 1960, puis une crise éclate. De plus, le corpus contient 100 fichiers pour 1960 et ils couvrent les 12 mois.

### 2. Contenu du dossier

| Fichier | Contenu |
|---|---|
| `tp2_1960.ipynb` | Notebook de synthèse, qui reprend toutes les étapes dans l'ordre |
| `s1_keywords.ipynb` | Extraction de mots clés avec Yake |
| `s2_wordcloud.ipynb` | Enrichissement des stopwords et nuage de mots |
| `s3_ner.ipynb` | Reconnaissance d'entités nommées avec SpaCy |
| `s4_sentiment.ipynb` | Analyse de sentiment de 10 phrases (TextBlob et BERT) |
| `nuage_1960.png` | Nuage de mots de l'année 1960 |

Les notebooks du dossier `module3` ne sont pas modifiés. Nous les avons copiés ici avant de les adapter, pour garder la version d'origine du cours.

### 3. Données

Les fichiers texte se trouvent dans `tac/data/txt`. Le dossier `data` n'est pas publié sur GitHub. Il faut donc télécharger le corpus sur l'UV avant d'exécuter les notebooks.

Il faut exécuter `s2_wordcloud.ipynb` avant `s3_ner.ipynb`, car le premier crée le fichier `data/tmp/1960.txt` utilisé par le second.

### 4. Principaux résultats

- **Mots clés.** « Congo belge », « Nations Unies » et « New York » reviennent dans plusieurs pages. Cependant, les petites annonces pèsent lourd : « Agence Rossel » apparaît dans 17 fichiers sur 100.
- **Nuage de mots.** Nous avons fait passer la liste de stopwords de 200 à 511 mots, en trois étapes. Ce nettoyage retire environ 19 % des mots. « CONGO » passe alors de la 27e à la 3e place, derrière « BELGIQUE » et « BELGE ».
- **Entités nommées.** Les personnes les plus citées sont Van Looy, Khrouchtchev, Lumumba et Tshombe. Le Congo est le premier lieu étranger (181 mentions). Nous avons dû écarter environ un quart des mentions, car SpaCy confond les abréviations des annonces avec des noms.
- **Sentiment.** Les deux outils sont d'accord sur 6 phrases sur 10. Ils fonctionnent bien sur le sport et la culture, mais ils se trompent souvent sur les phrases politiques.

### 5. Limites

La qualité de l'OCR limite toutes les analyses. De plus, les outils utilisés ont été conçus pour des textes modernes. Leurs résultats sur un journal de 1960 doivent donc être lus avec prudence.
