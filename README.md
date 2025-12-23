# Mining Software Repositories – Analyse du Dataset AIDev

## 1. Présentation du Projet

Ce projet présente une analyse exploratoire du **dataset AIDev**, réalisée dans le cadre d’une activité de *Mining Software Repositories (MSR)*.
L’objectif est d’étudier les caractéristiques, la contribution et le devenir des *pull requests* générées par des agents de programmation basés sur l’intelligence artificielle dans des projets open-source hébergés sur GitHub.

L’analyse suit un pipeline de données reproductible comprenant le chargement du dataset, le prétraitement des données, le calcul des métriques, la visualisation des résultats et la discussion des limitations.

---

## 2. Description du Dataset

Le **dataset AIDev** est un dataset public qui regroupe des *pull requests* générées par des agents de programmation IA (par exemple : OpenAI Codex, GitHub Copilot, Devin, Cursor).
Il est distribué via la plateforme Hugging Face et stocké au format **Parquet**.

Principales informations contenues dans le dataset :
- Métadonnées des pull requests (titre, description, état)
- Dates du cycle de vie (création, fermeture, fusion)
- Informations sur les repositories GitHub
- Identification de l’agent IA ayant généré chaque pull request

⚠️ **Remarque importante :**  
Le dataset contient exclusivement des pull requests générées par des agents de programmation IA. Aucune pull request générée par des développeurs humains n’est incluse.

---

## 3. Critères d’Inclusion et d’Exclusion

Afin de préparer un dataset exploitable pour l’analyse, les critères suivants ont été appliqués :

### Critères d’inclusion :
- Pull requests disposant d’une date de création valide
- Pull requests ayant un état final connu (fusionnée ou fermée)

### Critères d’exclusion :
- Pull requests avec des informations temporelles manquantes ou incohérentes
- Entrées ne permettant pas de calculer le temps de traitement

Après le prétraitement, le subset final contient :

- **859 927 pull requests**
- **14 attributs**

Ce subset est utilisé pour l’ensemble des analyses présentées.

---

## 4. Pipeline de Données Reproductible

Le pipeline d’analyse est implémenté dans un notebook Jupyter et comprend les étapes suivantes :

1. Chargement du dataset à l’aide de la bibliothèque Python `datasets`
2. Nettoyage et préparation des données
3. Création d’un subset basé sur les critères d’inclusion et d’exclusion
4. Calcul des métriques
5. Visualisation et interprétation des résultats

Toutes les étapes sont entièrement reproductibles.

---

## 5. Calcul des Métriques

Les métriques suivantes sont calculées afin de répondre aux questions de recherche :

- **Proportion de pull requests générées par des agents IA**
- **Taux de fusion** (proportion de pull requests fusionnées)
- **Taux de fermeture sans fusion**
- **Temps de traitement moyen** (en jours)
- **Contribution relative de chaque agent IA**

Le résultat final est une table propre et prête à l’analyse résumant l’ensemble de ces métriques.

---

## 6. Analyse et Visualisation

Les résultats sont analysés à l’aide de statistiques descriptives et de visualisations, notamment :

- Diagrammes en barres illustrant la contribution relative des agents IA
- Boîtes à moustaches (*boxplots*) montrant la distribution du temps de traitement des pull requests

Ces analyses permettent de répondre aux questions de recherche suivantes :
- RQ1 : Devenir des pull requests générées par des agents IA
- RQ2 : Temps de traitement des pull requests générées par des agents IA
- RQ3 : Contribution relative des agents IA dans le dataset AIDev

---

## 7. Limitations et Menaces à la Validité

Plusieurs limitations doivent être prises en compte :

- L’absence de pull requests générées par des développeurs humains empêche toute comparaison directe entre contributions humaines et contributions automatisées.
- La forte domination de certains agents (par exemple OpenAI Codex) peut biaiser les métriques globales.
- Les métriques utilisées sont purement quantitatives et ne permettent pas d’évaluer la qualité technique ou sémantique du code proposé.

Ces limitations sont inhérentes au dataset et sont explicitement discutées dans l’analyse.

---

## 8. Instructions d’Installation et d’Exécution

### Prérequis
- Python 3.8 ou supérieur
- pandas
- matplotlib
- datasets (Hugging Face)

### Exécution
1. Installer les bibliothèques Python requises
2. Ouvrir le notebook `AIDEVNotebook.ipynb`
3. Exécuter toutes les cellules du notebook dans l’ordre

Le dataset sera automatiquement téléchargé depuis la plateforme Hugging Face.

---

## 9. Reproductibilité

Tous les résultats présentés dans le rapport peuvent être reproduits en exécutant le notebook selon les instructions ci-dessus.
Aucune intervention manuelle n’est nécessaire.
