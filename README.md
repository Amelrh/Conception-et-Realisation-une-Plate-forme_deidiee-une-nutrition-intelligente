<img width="554" height="36" alt="image" src="https://github.com/user-attachments/assets/6bd0199c-3b99-4ee4-8640-e2b710a7a31b" /># 🥗 Nutrio — Plateforme de Nutrition Intelligente

> Mémoire de Licence — Filière Informatique, Spécialité ISIL  
> Université des Sciences et de la Technologie Houari Boumediene (USTHB)  
> Faculté d'Informatique — Département Systèmes d'Informatiques  
> Année universitaire 2024–2025

---

## 📋 Description

**Nutrio** est une application mobile multiplateforme dédiée au suivi nutritionnel personnalisé et à la gestion de la santé. Elle intègre un modèle d'intelligence artificielle (MobileNet fine-tuné) pour la **reconnaissance automatique des aliments** à partir d'images, couplé à un système complet de suivi de l'activité physique, de l'hydratation, du poids et de l'IMC.

L'application répond à une problématique concrète : la majorité des solutions existantes (MyFitnessPal, FoodVisor, Lifesum…) manquent de diversité culinaire locale (notamment les plats algériens traditionnels) et réservent leurs fonctionnalités avancées aux abonnements payants. Nutrio propose une alternative complète, gratuite et adaptée au contexte algérien.

---

## ✨ Fonctionnalités principales

- 📸 **Scan d'aliments par IA** — Reconnaissance d'image via MobileNet (95 classes, >9100 images)
- 📊 **Suivi nutritionnel** — Calories, glucides, protéines, lipides, cholestérol, sodium, minéraux
- 🏃 **Suivi d'activité physique** — Calories brûlées, activités personnalisées
- 👣 **Compteur de pas** — Historique et objectifs quotidiens
- 💧 **Suivi d'hydratation** — Objectifs et rappels
- ⚖️ **Suivi du poids & IMC** — Courbes d'évolution
- 🍽️ **Plan alimentaire personnalisé** — Généré selon les objectifs de l'utilisateur
- 📈 **Rapports de santé** — Visualisation graphique, téléchargement et envoi au médecin par email
- 🔔 **Notifications** — Rappels repas, hydratation, activité

---

## 🧠 Modèle IA — Reconnaissance d'aliments

| Paramètre | Valeur |
|-----------|--------|
| Architecture de base | MobileNet (pré-entraîné ImageNet) |
| Nombre de classes | 95 (aliments et plats, dont plats algériens) |
| Dataset | >9 100 images JPG RGB (FoodX-251, Food-101, Fruits-262 + collecte locale) |
| Augmentation des données | Rotation 30°, flip horizontal, zoom aléatoire, cisaillement |
| Couches ajoutées | Average Pooling → Dropout (20%) → Dense Softmax (95 neurones) |
| Framework | TensorFlow / Keras |
| Accuracy finale | **76%** sur données de validation |

### Comparaison avec les travaux similaires

| Travail | Modèle | Dataset | Accuracy |
|---------|--------|---------|----------|
| Ródenas et al. (2022) | CSWin-L | FoodX-251 | 79.90% |
| Şengür et al. (2019) | VGG16 + AlexNet | Food-101 | 79.86% |
| Wang et al. (2021) — TWIST | ResNet50 | Food-101 | 89.30% |
| **Nutrio (2025)** | **MobileNet fine-tuné** | **Dataset custom (95 classes)** | **76%** |

---

## 🛠️ Stack technique

### Frontend (Mobile)
- **Flutter** — Développement multiplateforme Android/iOS

### Backend
- **Node.js** — Serveur API REST
- **MongoDB** — Base de données NoSQL orientée documents

### IA / Machine Learning
- **Python** — Langage principal
- **TensorFlow / Keras** — Entraînement et déploiement du modèle CNN
- **JupyterLab** — Environnement de développement interactif
- **NumPy / Pandas** — Manipulation de données
- **Matplotlib / Seaborn** — Visualisation
- **Scikit-Learn** — Métriques d'évaluation

---

## 🏗️ Architecture du système

```
┌─────────────────────────────────────────┐
│           Application Flutter           │
│  (Authentification, Scan, Tracker,      │
│   Rapports, Activités, Notifications)   │
└────────────────┬────────────────────────┘
                 │ REST API
┌────────────────▼────────────────────────┐
│            Serveur Node.js              │
│         (Logique métier, Auth)          │
└──────┬─────────────────────┬────────────┘
       │                     │
┌──────▼──────┐     ┌────────▼────────┐
│   MongoDB   │     │  Modèle MobileNet│
│  (Données   │     │  (Inférence IA  │
│utilisateurs)│     │  reconnaissance) │
└─────────────┘     └─────────────────┘
```

---

## 📐 Conception UML

Le projet inclut les diagrammes suivants :

- **Diagramme de cas d'utilisation global** — Toutes les interactions utilisateur
- **Diagramme de cas d'utilisation** — Gérer le profil (détail)
- **Diagramme de classes** — 7 entités : Utilisateur, Repas, Aliment, SuiviPoids, Hydratation, ActivitePhysique, RapportSante, Notification
- **Diagrammes de séquence** — Authentification, Créer un compte, Scanner et identifier un aliment
- **Diagrammes d'activité** — Authentification, Créer un compte

---

## 📱 Interfaces de l'application

| Interface | Description |
|-----------|-------------|
| Onboarding / Inscription | Création de compte (email, Google, Apple, Facebook) + configuration profil (nom, poids, objectifs) |
| Plan personnalisé | Génération automatique des objectifs caloriques et macronutriments |
| Accueil | Dashboard journalier (calories, macros, repas par type) |
| Scanner | Reconnaissance d'aliments par caméra + détails nutritionnels ajustables |
| Tracker | Suivi eau, pas, poids, IMC — avec historique |
| Rapports / Insights | Graphiques hebdomadaires/mensuels, envoi email au médecin |

---

## 📊 Résultats du modèle

- **Accuracy validation :** ~76%
- **Loss validation :** convergence stable après ~15 époques
- **Matrice de confusion :** diagonale dominante confirmant la bonne discrimination entre les 95 classes

---

## 🔮 Perspectives d'amélioration

- Élargissement du dataset (plus de plats algériens et maghrébins)
- Amélioration de l'accuracy (EfficientNet, Vision Transformers)
- Intégration d'objets connectés (balance, bracelet fitness)
- Fonctionnalités de recommandation personnalisée par IA
- Synchronisation cloud pour sauvegarde multi-appareils
- Support multilingue (arabe, français, anglais)

---

## 📚 Références principales

- Szeliski, R. *Computer Vision: Algorithms and Applications*, Springer, 2022
- Şengür et al. *Food Image Classification with Deep Features*, IEEE IDAP, 2019
- Wang et al. *Self-Supervised Learning by Estimating Twin Class Distributions (TWIST)*, 2021
- Ródenas et al. *Learning Multi-Subset of Classes for Fine-Grained Food Recognition*, 2022

---

##  Licence

Projet académique — USTHB, Faculté d'Informatique, 2025
Tous droits réservés aux auteurs.
