# 🌍 Prévision de la Demande Touristique & Modélisation du Déficit Capacitaire (Maroc 2030)

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.0+-orange.svg)
![Data Science](https://img.shields.io/badge/Data%20Science-Deep%20Learning-success.svg)
![Statut](https://img.shields.io/badge/Statut-Achevé-brightgreen.svg)

> **Un outil d'aide à la décision basé sur l'Intelligence Artificielle hybride pour anticiper l'impact de la Coupe du Monde 2030 sur les infrastructures hôtelières marocaines.**

## 📖 Contexte du Projet

En 2030, le Royaume du Maroc co-organisera la Coupe du Monde de la FIFA, un événement planétaire (un "Cygne Noir" statistique) qui générera un afflux touristique sans précédent. 

Ce projet de fin d'études en ingénierie (IA & Data Technologies) répond à une problématique stratégique majeure : **Le réseau hôtelier marocain actuel sera-t-il capable d'absorber ce choc de la demande ?**

Pour y répondre, nous avons développé un moteur d'inférence de bout en bout, allant du nettoyage des données historiques jusqu'à la simulation visuelle des déficits en lits d'hôtels pour les grandes métropoles recueillant les matchs de la coupe  (Marrakech, Agadir, Casablanca, Tanger, Fès, Rabat).

## 🧠 L'Approche Scientifique (Modélisation Hybride)

L'anticipation d'un événement inédit pose une limite mathématique fondamentale aux réseaux de neurones classiques (phénomène de *Weight Starvation*). Notre méthodologie contourne ce problème par une **approche hybride** :

1. **Deep Learning (SimpleRNN) :** Un réseau de neurones récurrent modélise la croissance tendancielle naturelle, la forte saisonnalité du pays et la résilience post-Covid.
2. **Heuristique Métier (Le Choc Exogène) :** Un coefficient multiplicateur paramétrable (ex: +45%) est injecté en post-processing spécifiquement sur l'été 2030 pour simuler la magnitude inédite de l'événement sportif.
3. **Confrontation Offre vs Demande :** La prévision de la demande est mathématiquement superposée au plafond de la capacité hôtelière théorique (lits disponibles) afin d'isoler et de quantifier précisément les zones de **déficit capacitaire** (infrastructures à construire).

## 🗂️ Structure du Répertoire

- `notebooks/` : Contient le code source principal (`.ipynb`). Le pipeline inclut la préparation des données, le benchmark des modèles (Baseline vs RNN), le forecasting autorégressif et le calcul des capacités.
- `docs/` : Contient le code source de la documentation technique rédigée en Markdown.
- `mkdocs.yml` : Fichier de configuration pour le déploiement du site web documentaire.

## 📚 Documentation Officielle (Read the Docs)

L'intégralité du rapport de recherche, des explications mathématiques, des choix d'architecture et des graphiques finaux d'aide à la décision est disponible sur notre documentation interactive :

👉 **[Accéder au Rapport Complet (Lien Read the Docs à insérer ici)](#)**

## 🛠️ Stack Technique

- **Traitement des Données :** `Pandas`, `NumPy`, `Scikit-Learn` .
- **Deep Learning :** `TensorFlow`, `Keras` .
- **Visualisation :** `Matplotlib` , `seaborn` .
- **Déploiement Documentaire :** `MkDocs`, `Material for MkDocs`.

---
*Projet réalisé par **Mohammed Madroumi** dans le cadre du la premiére année du cycle d'ingénieur en 	Intelligence Artificielle et Technologies des Données : Systèmes Industriels (IATDSI) - ENSAM Meknès.*
