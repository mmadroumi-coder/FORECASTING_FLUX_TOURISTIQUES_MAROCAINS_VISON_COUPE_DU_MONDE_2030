# Chapitre 1 : Stratégie de la Donnée et Ingénierie (Feature Engineering)

La qualité d'un modèle d'Intelligence Artificielle dépend intrinsèquement de la qualité des données qu'il ingère (*Garbage In, Garbage Out*). Pour anticiper le choc touristique de 2030, la première étape scientifique a consisté à consolider, nettoyer et enrichir les données historiques du tourisme marocain.

## 1. Origine et Granularité du Dataset
Les données sources proviennent des registres officiels (Observatoire du Tourisme Marocain / Ministère du Tourisme) : [observatoire](https://observatoiredutourisme.ma/).
Afin de capter la forte saisonnalité du secteur, nous avons opté pour une **granularité mensuelle** s'étalant sur plus d'une décennie (2010 - 2024).

Le dataset se concentre sur deux dimensions géographiques :
* **Niveau Macro :** Les Arrivées aux Postes Frontières (APF), mesurant l'attractivité globale du pays.
* **Niveau Micro (Les Métropoles) :** Le volume de Nuitées pour les pôles majeurs (Marrakech, Agadir, Casablanca, Tanger, Fès, Rabat).
* **La Contrainte Physique :** Pour chaque ville, nous avons extrait l'évolution de la **Capacité Hôtelière** (le nombre de lits disponibles), qui servira de plafond (Offre) lors de notre Phase 3.

## 2. Feature Engineering : Comprendre l'Incompréhensible
Une série temporelle brute (une simple courbe de Nuitées) ne donne pas assez de contexte à un réseau de neurones. Nous avons dû créer de toutes pièces des variables explicatives (exogènes) pour justifier mathématiquement les anomalies du passé et anticiper celles du futur.

### A. La Variable "Pandémie" (Masquage de la crise)
Le Covid-19 a provoqué une chute artificielle et brutale des flux (fermeture des frontières). Si l'IA apprend sur ces données brutes, elle pensera que le tourisme peut s'effondrer naturellement.
* **Solution d'ingénierie :** Création d'une variable binaire `Pandemie` (1 pendant les confinements , 0 sinon). Le modèle apprend ainsi à associer cette chute à une anomalie externe et non à une tendance économique.

### B. La Variable "Sport" (Le socle de l'hybridation)
Pour préparer le modèle au choc de la Coupe du Monde 2030, nous avons introduit un marqueur temporel pour les événements sportifs historiques (ex: CAN 2025).
* **Justification :** Cela permet de créer des "poids synaptiques" liant le sport à l'augmentation du tourisme, même si ces événements passés n'ont pas l'ampleur de 2030 , on peut augmenter l'intensit.

### C. Les Balises Temporelles (Saisonnalité & Tendance)
Pour éviter que l'IA ne perde ses repères lors des prévisions à très long terme :
* `Mois` : Indique cycliquement la saisonnalité (ex: les pics estivaux d'Agadir).
* `Index_Temps` : Une fonction linéaire croissante forçant le modèle à intégrer le concept de croissance structurelle (Trend) sur le long terme.
* `Remarque` : ces colonnes ont ètè ajoutèes et utilisèes lors de la phase du deeplearning a l'aide de la bibliotheque numpy. 
* 
## 3. Transformation Mathématique (Min-Max Scaling)
Avant l'ingestion par les réseaux de neurones, toutes les variables ont été projetées dans un espace vectoriel normalisé compris entre $[0, 1]$ via l'algorithme `MinMaxScaler`.
* **Pourquoi cette étape est-elle vitale ?** Les modèles RNN utilisent des fonctions d'activation (comme *Tanh*) qui saturent avec de grands nombres (ex: 500 000 touristes). La normalisation garantit une convergence mathématique stable lors de la descente de gradient, évitant l'explosion des poids.
