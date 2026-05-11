# Proj-Chatbot

# CECCE Virtual Agent Chatbot

> Dans ce projet, je vais développer un chatbot informationnel connecté à ServiceNow Virtual Agent afin d’aider les employés du CECCE à retrouver plus facilement des informations importantes à partir du Google Sites public et des documents PDF associés.

## Description du projet

Dans ce projet, je vais développer un chatbot informationnel connecté à ServiceNow Virtual Agent afin d’aider les employés du CECCE à retrouver rapidement des informations présentes dans un Google Sites public ainsi que dans des documents PDF associés.

Ici, je vais utiliser la Gemini API ainsi que Gemini File Search afin d’effectuer une recherche intelligente dans les documents collectés. L’objectif principal du projet est de fournir des réponses simples, pertinentes et accompagnées de sources fiables.

Le système ne réalisera aucune action transactionnelle. Il servira uniquement comme assistant informationnel afin de faciliter l’accès aux procédures, politiques, coordonnées et documents de référence.

---

# Objectifs du projet

Dans ce projet, je pense que les objectifs les plus importants sont les suivants :

* Réduire le temps nécessaire pour retrouver une information.
* Simplifier la navigation dans le Google Sites du CECCE.
* Fournir des réponses plus claires et plus rapides aux employés.
* Utiliser un système moderne de recherche intelligente.
* Afficher des réponses avec des citations et des liens vers les sources.
* Construire une architecture simple, maintenable et évolutive.
* Préparer une intégration avec ServiceNow Virtual Agent.

---

# Technologies utilisées

Le projet utilise plusieurs technologies modernes afin de construire une solution stable et évolutive.

## Langages

* Python 3
* Markdown
* JSON

## Librairies Python

* requests
* beautifulsoup4
* markdownify
* pypdf
* google-genai
* python-dotenv
* pandas
* tenacity
* tqdm
* jupyter

## Outils et plateformes

* Gemini API
* Gemini File Search
* ServiceNow Virtual Agent
* GitHub
* GitHub Codespaces
* VS Code
* Jupyter Notebook

---

# Structure du projet

La structure du projet a été organisée afin de séparer clairement les différentes parties du système.

```text
# Structure du projet

```text
project_root/
│
├── notebooks/
│   ├── 01_site_map.ipynb
│   ├── 02_pages_to_markdown.ipynb
│   ├── 03_pdf_capture.ipynb
│   ├── 04_upload_to_file_search.ipynb
│   └── 05_ask_and_inspect_grounding.ipynb
│
├── data/
│   ├── raw_pages/
│   ├── raw_pdfs/
│   ├── markdown/
│   └── manifests/
│
├── src/
│   ├── crawler.py
│   ├── normalizer.py
│   ├── pdf_capture.py
│   ├── file_search_uploader.py
│   ├── ask_service.py
│   └── citation_formatter.py
│
├── api/
│   └── main.py
│
├── tests/
│   └── evaluation_questions.csv
│
├── requirements.txt
├── .env.example
└── README.md
```

# Explication des dossiers

## notebooks/

Ce dossier contient les notebooks Jupyter utilisés durant le développement du prototype.

Chaque notebook représente une étape importante du projet :

* cartographie du site
* extraction du contenu
* récupération des PDF
* intégration avec Gemini File Search
* validation des réponses et des citations

Les notebooks permettent de tester rapidement les fonctionnalités avant de les transformer en scripts Python plus propres.

---

## data/

Ce dossier contient toutes les données utilisées dans le projet.

### raw_pages/

Contient les pages HTML récupérées depuis le Google Sites.

### raw_pdfs/

Contient les fichiers PDF téléchargés.

### markdown/

Contient les versions Markdown des pages afin de faciliter l’indexation.

### manifests/

Contient les fichiers de métadonnées décrivant les documents collectés.

---

## src/

Ce dossier contient toute la logique Python principale du projet.

### crawler.py

Responsable du crawl du Google Sites et de la découverte des liens.

### normalizer.py

Nettoie les pages HTML et les convertit en Markdown.

### pdf_capture.py

Télécharge et gère les fichiers PDF détectés.

### file_search_uploader.py

Envoie les documents dans Gemini File Search.

### ask_service.py

Envoie les questions à Gemini et récupère les réponses.

### citation_formatter.py

Formate les citations et les liens des réponses.

---

## api/

Contient le backend API qui sera utilisé par ServiceNow.

Le backend recevra les questions envoyées par Virtual Agent, interrogera Gemini et retournera une réponse structurée.

---

## tests/

Contient les questions de test utilisées pour évaluer la qualité des réponses.

---

# Plan du projet

Pour ce projet, je vais avancer progressivement afin de valider chaque partie avant de passer à la suivante.

---

# Phase 0 – Préparation du projet

Dans cette première phase, je vais préparer toute la base du projet avant de commencer le développement du chatbot. Selon moi, cette étape est très importante parce qu’elle permet d’avoir une structure propre et organisée dès le début du projet. Je vais aussi préparer l’environnement de développement, les dossiers, les notebooks et les fichiers nécessaires afin de faciliter les prochaines étapes du développement.

## Objectif

Préparer l’environnement de développement et définir le périmètre du projet.

## Étapes

* Création du repository GitHub.
* Création de la structure du projet.
* Préparation des dossiers et fichiers.
* Installation des dépendances.
* Préparation des notebooks.
* Documentation initiale.
* Définition des objectifs.
* Préparation des questions d’évaluation.

## Résultat attendu

Un projet propre, organisé et prêt pour le développement.

---

# Phase 1 – Cartographie du Google Sites

Ici, je vais commencer à analyser le Google Sites afin de comprendre sa structure et identifier les pages importantes. Cette étape va me permettre de mieux comprendre comment le site est organisé et quelles sections seront utiles pour le chatbot. Je pense aussi que cette phase est importante afin d’éviter de récupérer des pages inutiles ou du contenu qui ne sera pas pertinent pour les utilisateurs.

## Objectif

Créer une carte des pages importantes du Google Sites.

## Étapes

* Analyser la page principale.
* Identifier les liens internes.
* Éliminer les doublons.
* Conserver uniquement les pages pertinentes.
* Sauvegarder les URLs dans un manifest.

## Résultat attendu

Une liste propre des pages et ressources importantes.

---

# Phase 2 – Extraction des pages HTML

Dans cette étape, je vais récupérer les pages HTML du Google Sites afin de préparer les données pour Gemini File Search. Je vais aussi nettoyer le contenu afin de retirer les éléments inutiles comme les menus ou certaines sections répétitives. Le but est d’obtenir des fichiers plus propres et plus faciles à analyser pour le système de recherche.

## Objectif

Récupérer le contenu des pages Google Sites.

## Étapes

* Télécharger les pages HTML.
* Nettoyer le contenu.
* Retirer les menus et éléments inutiles.
* Conserver uniquement l’information importante.
* Convertir le contenu en Markdown.

## Résultat attendu

Des fichiers Markdown lisibles et propres.

---

# Phase 3 – Récupération des PDF

Ici, je vais détecter et télécharger les documents PDF liés au Google Sites afin de les ajouter au corpus du chatbot. Plusieurs informations importantes peuvent être présentes dans ces documents, donc je vais devoir les organiser correctement et conserver leurs métadonnées. Cette étape va aussi permettre d’améliorer la qualité des réponses du chatbot.

## Objectif

Télécharger les documents PDF liés au Google Sites.

## Étapes

* Détecter les liens PDF.
* Télécharger les documents.
* Organiser les fichiers.
* Ajouter les métadonnées.
* Vérifier l’intégrité des PDF.

## Résultat attendu

Une collection de PDF utilisables par Gemini File Search.

---

# Phase 4 – Intégration Gemini File Search

Dans cette phase, je vais intégrer les documents dans Gemini File Search afin de permettre une recherche intelligente dans le contenu. Je pense que cette étape est l’une des plus importantes du projet parce qu’elle va permettre au modèle Gemini de retrouver rapidement les informations pertinentes dans les documents collectés.

## Objectif

Créer un espace de recherche intelligent.

## Étapes

* Créer un File Search Store.
* Envoyer les documents Markdown.
* Envoyer les PDF.
* Ajouter les métadonnées.
* Tester l’indexation.

## Résultat attendu

Un corpus entièrement indexé dans Gemini File Search.

---

# Phase 5 – Questions et réponses

Ici, je vais commencer à tester le comportement du chatbot avec de vraies questions. Cette phase va me permettre de vérifier si les réponses sont claires, pertinentes et correctement reliées aux bonnes sources. Je vais aussi tester plusieurs types de questions afin de voir comment le système réagit dans différentes situations.

## Objectif

Tester les réponses générées par Gemini.

## Étapes

* Envoyer des questions.
* Vérifier les réponses.
* Vérifier les citations.
* Tester les cas d’erreur.
* Ajuster les prompts.

## Résultat attendu

Des réponses fiables accompagnées de sources.

---

# Phase 6 – Évaluation de la qualité

Dans cette étape, je vais analyser la qualité des réponses et identifier les améliorations nécessaires. Je vais comparer les résultats obtenus avec les attentes du projet afin de voir si le chatbot répond correctement aux besoins des utilisateurs. Cette étape va aussi permettre d’améliorer progressivement la précision des réponses.

## Objectif

Mesurer la qualité des réponses.

## Étapes

* Préparer des questions réelles.
* Comparer les réponses.
* Vérifier les sources.
* Identifier les erreurs.
* Améliorer le corpus.

## Résultat attendu

Une preuve de concept fonctionnelle et stable.

---

# Phase 7 – Construction du backend API

Ici, je vais transformer le prototype en une API Python plus propre et réutilisable. Je vais organiser le code afin de rendre le projet plus professionnel et plus facile à maintenir. Cette étape sera importante pour préparer la connexion avec ServiceNow Virtual Agent.

## Objectif

Créer une API Python stable.

## Étapes

* Créer les endpoints.
* Ajouter la logique Gemini.
* Ajouter les réponses JSON.
* Ajouter la gestion des erreurs.
* Préparer l’intégration ServiceNow.

## Résultat attendu

Un backend prêt à être utilisé par Virtual Agent.

---

# Phase 8 – Intégration ServiceNow

Dans cette dernière phase, je vais connecter le backend du chatbot à ServiceNow Virtual Agent. Le but sera de permettre aux employés de poser leurs questions directement dans ServiceNow et de recevoir des réponses automatiquement. Je vais aussi tester l’affichage des réponses et des sources afin de rendre l’expérience utilisateur plus claire et plus simple.

## Objectif

Connecter le chatbot à ServiceNow Virtual Agent.

## Étapes

* Créer les appels REST.
* Envoyer les questions.
* Afficher les réponses.
* Afficher les sources.
* Tester les scénarios utilisateurs.

## Résultat attendu

Un chatbot fonctionnel dans ServiceNow.

---

# Fonctionnement général du système

Le système fonctionnera selon les étapes suivantes :

1. Le crawler visite le Google Sites.
2. Les pages et PDF sont collectés.
3. Les documents sont nettoyés et convertis.
4. Les documents sont envoyés dans Gemini File Search.
5. L’utilisateur pose une question dans ServiceNow.
6. Le backend envoie la question à Gemini.
7. Gemini recherche les documents pertinents.
8. Gemini génère une réponse.
9. Le backend retourne la réponse avec les sources.
10. Virtual Agent affiche le résultat à l’utilisateur.

---

# Architecture générale

```text
Google Sites + PDFs
        ↓
Python Crawler
        ↓
Markdown + Metadata
        ↓
Gemini File Search
        ↓
Gemini API
        ↓
Python Backend API
        ↓
ServiceNow Virtual Agent
        ↓
Utilisateur
```

---

# Approche de développement

Je vais développer ce projet de manière progressive afin de garder une structure claire et éviter les problèmes durant le développement.

La priorité sera donnée à :

* la qualité des données
* la stabilité du crawl
* la lisibilité des réponses
* la traçabilité des sources
* la simplicité de maintenance

Le projet commencera avec un prototype limité avant d’être étendu progressivement.

---

# Gestion des risques

## Risque : contenu trop volumineux

Solution : commencer avec un sous-ensemble limité.

## Risque : réponses incomplètes

Solution : améliorer les métadonnées et les prompts.

## Risque : doublons dans les documents

Solution : nettoyer le corpus avant l’indexation.

## Risque : coûts API élevés

Solution : limiter le volume durant le POC.

## Risque : réponses incorrectes

Solution : toujours afficher les sources.

---

# Installation du projet

## Cloner le repository

```bash
git clone <repository_url>
```

## Entrer dans le dossier

```bash
cd Proj-Chatbot
```

## Installer les dépendances

```bash
pip install -r requirements.txt
```

## Configurer les variables d’environnement

Créer un fichier `.env` à partir de `.env.example`.

---

# État actuel du projet

## Complété

* Création du repository GitHub
* Création de la structure du projet
* Préparation des dossiers
* Préparation des notebooks
* Configuration Git
* Documentation initiale

## En cours

* Préparation de la Phase 0
* Définition du périmètre
* Préparation des questions d’évaluation

## À venir

* Crawl du Google Sites
* Intégration Gemini API
* Intégration File Search
* Backend API
* ServiceNow Virtual Agent

---

# Conclusion

Avec ce projet, je veux construire un chatbot informationnel moderne capable d’aider les employés du CECCE à retrouver rapidement des informations importantes à partir d’un Google Sites public et de documents PDF.

L’approche retenue repose sur Gemini API et Gemini File Search afin d’obtenir un système plus simple, plus évolutif et plus facile à maintenir qu’un moteur de recherche entièrement personnalisé.

Le développement sera réalisé progressivement afin de valider chaque étape du système avant l’intégration finale avec ServiceNow Virtual Agent.

L’objectif final est de fournir une solution stable, claire, professionnelle et facilement extensible pour les futurs besoins du CECCE.
