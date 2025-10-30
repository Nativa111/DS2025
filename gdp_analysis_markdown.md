# Rapport d'Analyse Approfondie du PIB
## Comparaison Internationale (2018-2023)

Cherestal Deborah Nativa

![Deborah Nativa Cherestal](![WhatsApp Image 2025-10-30 at 11 50 17](https://github.com/user-attachments/assets/1a60df9d-1939-410d-ba24-a93462ac4deb)
)
![Deborah Nativa Cherestal](https://upload.wikimedia.org/wikipedia/fr/b/bf/ENCG-S.png)
---

## 1. Introduction Générale

### 📊 Objectif de l'analyse

Cette étude vise à analyser et comparer l'évolution du Produit Intérieur Brut (PIB) de cinq économies majeures : États-Unis, Chine, Japon, Allemagne et Inde. L'analyse couvre la période 2018-2023, permettant d'identifier les tendances macroéconomiques, l'impact de la pandémie COVID-19, et les trajectoires de reprise économique.

### 🔬 Méthodologie générale employée

- **Approche quantitative** : Analyse statistique descriptive et comparative
- **Visualisation de données** : Graphiques professionnels avec matplotlib et seaborn
- **Analyse temporelle** : Suivi de l'évolution sur 6 années consécutives
- **Comparaison internationale** : Benchmark entre économies développées et émergentes
- **Outils statistiques** : Calculs de moyennes, écarts-types, taux de croissance et corrélations

### 🌍 Pays sélectionnés et justification

| Pays | Catégorie | Justification |
|------|-----------|---------------|
| 🇺🇸 **États-Unis** | Économie développée | Première économie mondiale, référence du dollar |
| 🇨🇳 **Chine** | Économie émergente | Deuxième économie mondiale, croissance rapide |
| 🇯🇵 **Japon** | Économie développée | Troisième économie mondiale, leader technologique |
| 🇩🇪 **Allemagne** | Économie développée | Locomotive européenne, industrie puissante |
| 🇮🇳 **Inde** | Économie émergente | Plus grande démocratie, démographie favorable |

### ❓ Questions de recherche principales

1. Quelle est l'évolution du PIB nominal des 5 pays entre 2018 et 2023 ?
2. Comment la pandémie COVID-19 a-t-elle impacté les différentes économies ?
3. Quels pays ont connu les taux de croissance les plus élevés ?
4. Quelle est la relation entre PIB total et PIB par habitant ?
5. Peut-on identifier des corrélations entre les performances économiques ?
6. Quelles sont les trajectoires de reprise post-COVID ?

---

## 2. Description des Données

### 📚 Sources des données

- **Source principale** : Banque mondiale (World Development Indicators)
- **Source secondaire** : Fonds Monétaire International (FMI - World Economic Outlook)
- **Période d'analyse** : 2018-2023 (6 années consécutives)
- **Mise à jour** : Octobre 2023
- **Fiabilité** : Données officielles vérifiées et validées

### 📊 Variables analysées

1. **PIB nominal** : Valeur totale en milliards USD (dollars courants)
2. **PIB par habitant** : PIB divisé par la population (USD/habitant)
3. **Taux de croissance annuel** : Variation en pourcentage année par année
4. **PIB cumulé** : Somme du PIB sur la période 2018-2023
5. **Volatilité** : Écart-type pour mesurer la stabilité économique

### 📅 Période couverte

**2018-2023** : Cette période permet de capturer :
- La période pré-COVID (2018-2019)
- Le choc de la pandémie (2020)
- La reprise économique (2021-2023)
- Les tensions géopolitiques récentes

### ⚠️ Qualité et limitations des données

**Points forts** :
- Données officielles de sources reconnues internationalement
- Méthodologie standardisée permettant les comparaisons
- Couverture complète sans valeurs manquantes

**Limitations** :
- Données en dollars courants (non ajustées à l'inflation)
- Fluctuations des taux de change peuvent fausser les comparaisons
- Estimations pour 2023 basées sur données préliminaires
- Économie informelle non entièrement capturée (notamment Inde)
- PIB ne mesure pas le bien-être ou la durabilité

### 📊 Tableau récapitulatif des données

**PIB nominal (en milliards USD)**

| Année | USA | Chine | Japon | Allemagne | Inde |
|-------|-----|-------|-------|-----------|------|
| 2018 | 20,580 | 13,890 | 4,970 | 3,950 | 2,700 |
| 2019 | 21,380 | 14,280 | 5,080 | 3,860 | 2,870 |
| 2020 | 20,930 | 14,720 | 5,050 | 3,850 | 2,670 |
| 2021 | 23,310 | 17,730 | 4,940 | 4,260 | 3,150 |
| 2022 | 25,460 | 17,960 | 4,230 | 4,080 | 3,390 |
| 2023 | 27,360 | 17,890 | 4,210 | 4,120 | 3,730 |

**PIB par habitant (2023 - en USD)**

| Pays | PIB par habitant | Classement |
|------|------------------|------------|
| États-Unis | 81,695 | 1 |
| Allemagne | 49,190 | 2 |
| Japon | 33,815 | 3 |
| Chine | 12,720 | 4 |
| Inde | 2,612 | 5 |

---

## 3. Code Python d'Analyse

### 📦 Section 1 : Importation des bibliothèques nécessaires

```python
# ============================================
# IMPORTATION DES BIBLIOTHÈQUES
# ============================================

# Pandas : manipulation et analyse de données tabulaires
import pandas as pd

# Matplotlib : création de graphiques statiques
import matplotlib.pyplot as plt

# Seaborn : visualisations statistiques avancées
import seaborn as sns

# NumPy : calculs numériques et opérations matricielles
import numpy as np

# Configuration du style des graphiques pour un rendu professionnel
plt.style.use('seaborn-v0_8-darkgrid')  # Style avec grille
sns.set_palette("husl")  # Palette de couleurs harmonieuse

# Configuration de la taille par défaut des figures
plt.rcParams['figure.figsize'] = (12, 6)

# Configuration de la police pour une meilleure lisibilité
plt.rcParams['font.size'] = 11

print("✓ Bibliothèques importées avec succès")
```

**Explication** : Cette section importe toutes les bibliothèques nécessaires pour l'analyse. Pandas permet de manipuler les données sous forme de tableaux, Matplotlib et Seaborn créent les visualisations, et NumPy effectue les calculs mathématiques.

---

### 💾 Section 2 : Chargement et préparation des données

```python
# ============================================
# CHARGEMENT DES DONNÉES
# ============================================

# Création d'un dictionnaire contenant les données du PIB
# Chaque clé représente une variable (année ou pays)
# Les valeurs sont des listes contenant les données annuelles
gdp_data = {
    'Année': [2018, 2019, 2020, 2021, 2022, 2023],
    'USA': [20580, 21380, 20930, 23310, 25460, 27360],
    'Chine': [13890, 14280, 14720, 17730, 17960, 17890],
    'Japon': [4970, 5080, 5050, 4940, 4230, 4210],
    'Allemagne': [3950, 3860, 3850, 4260, 4080, 4120],
    'Inde': [2700, 2870, 2670, 3150, 3390, 3730]
}

# Conversion du dictionnaire en DataFrame pandas
# Un DataFrame est une structure tabulaire bidimensionnelle
df = pd.DataFrame(gdp_data)

# Définir la colonne 'Année' comme index du DataFrame
# Cela facilite l'accès aux données par année
df.set_index('Année', inplace=True)

# Affichage des premières lignes pour vérification
print("\n📊 Aperçu des données :")
print(df.head())

# Affichage des dimensions du dataset
print(f"\n📏 Dimensions : {df.shape[0]} années × {df.shape[1]} pays")
```

**Explication** : Cette section charge les données brutes dans un DataFrame pandas. Le DataFrame est une structure de données tabulaire qui facilite les manipulations. L'index est défini sur les années pour faciliter les accès temporels.

---

### 🧹 Section 3 : Nettoyage et transformation des données

```python
# ============================================
# NETTOYAGE DES DONNÉES
# ============================================

# Vérification des valeurs manquantes dans chaque colonne
# .isnull() retourne True pour les valeurs manquantes
# .sum() compte le nombre de True par colonne
print("\n🔍 Vérification des valeurs manquantes :")
valeurs_manquantes = df.isnull().sum()
print(valeurs_manquantes)

# Vérification si des valeurs manquantes existent
if valeurs_manquantes.sum() == 0:
    print("✓ Aucune valeur manquante détectée")
else:
    print("⚠️ Attention : valeurs manquantes détectées")
    # Stratégie de traitement : interpolation linéaire
    df.interpolate(method='linear', inplace=True)

# Vérification des types de données
print("\n📋 Types de données :")
print(df.dtypes)

# Vérification des valeurs négatives (anomalie potentielle)
valeurs_negatives = (df < 0).sum().sum()
if valeurs_negatives > 0:
    print(f"⚠️ {valeurs_negatives} valeurs négatives détectées")
else:
    print("✓ Aucune valeur négative (normal pour le PIB)")

# Création d'une copie de sauvegarde pour préserver les données originales
df_original = df.copy()

print("\n✓ Nettoyage des données terminé")
```

**Explication** : Le nettoyage vérifie la qualité des données : valeurs manquantes, types incorrects, anomalies. Dans notre cas, les données sont propres, mais ce code serait essentiel avec des données réelles potentiellement incomplètes.

---

### 📈 Section 4 : Analyse statistique descriptive

```python
# ============================================
# STATISTIQUES DESCRIPTIVES
# ============================================

# Calcul des statistiques descriptives complètes
# describe() calcule : count, mean, std, min, 25%, 50%, 75%, max
print("\n📊 STATISTIQUES DESCRIPTIVES COMPLÈTES")
print("="*60)
statistiques = df.describe()
print(statistiques.round(2))

# Calcul de la moyenne du PIB par pays (2018-2023)
print("\n💰 PIB MOYEN 2018-2023 (Milliards USD)")
print("="*60)
pib_moyen = df.mean().sort_values(ascending=False)
for pays, valeur in pib_moyen.items():
    print(f"{pays:12s} : {valeur:>10,.0f} Mds USD")

# Calcul de la médiane (valeur centrale)
print("\n📍 PIB MÉDIAN 2018-2023")
pib_median = df.median().sort_values(ascending=False)
print(pib_median.round(0))

# Calcul de l'écart-type (mesure de la volatilité)
print("\n📊 ÉCART-TYPE (Volatilité économique)")
print("="*60)
ecart_type = df.std().sort_values(ascending=False)
for pays, valeur in ecart_type.items():
    print(f"{pays:12s} : {valeur:>10,.0f} Mds USD")

# Calcul du coefficient de variation (volatilité relative)
# CV = (écart-type / moyenne) × 100
print("\n📈 COEFFICIENT DE VARIATION (%)")
print("="*60)
cv = (df.std() / df.mean() * 100).sort_values(ascending=False)
for pays, valeur in cv.items():
    print(f"{pays:12s} : {valeur:>8,.2f} %")

# PIB total cumulé sur la période
print("\n💵 PIB CUMULÉ 2018-2023")
pib_cumule = df.sum().sort_values(ascending=False)
for pays, valeur in pib_cumule.items():
    print(f"{pays:12s} : {valeur:>10,.0f} Mds USD")
```

**Explication** : Cette section calcule toutes les statistiques descriptives essentielles. La moyenne donne une valeur centrale, l'écart-type mesure la volatilité, et le coefficient de variation permet de comparer la stabilité relative entre pays de tailles différentes.

---

### 📊 Section 5 : Calcul des taux de croissance

```python
# ============================================
# CALCUL DES TAUX DE CROISSANCE
# ============================================

# Calcul du taux de croissance annuel en pourcentage
# Formule : ((Valeur_N / Valeur_N-1) - 1) × 100
# .pct_change() calcule le changement en pourcentage par rapport à la ligne précédente
taux_croissance = df.pct_change() * 100

print("\n📈 TAUX DE CROISSANCE ANNUEL (%)")
print("="*70)
print(taux_croissance.round(2))

# Calcul du taux de croissance moyen par pays
print("\n📊 TAUX DE CROISSANCE MOYEN 2019-2023 (%)")
print("="*60)
croissance_moyenne = taux_croissance.mean().sort_values(ascending=False)
for pays, valeur in croissance_moyenne.items():
    print(f"{pays:12s} : {valeur:>8,.2f} %")

# Identification de l'année de croissance maximale par pays
print("\n🚀 ANNÉE DE CROISSANCE MAXIMALE PAR PAYS")
print("="*60)
for pays in df.columns:
    annee_max = taux_croissance[pays].idxmax()
    valeur_max = taux_croissance[pays].max()
    print(f"{pays:12s} : {annee_max} ({valeur_max:,.2f}%)")

# Identification de l'année de croissance minimale (récession)
print("\n📉 ANNÉE DE CROISSANCE MINIMALE (RÉCESSION)")
print("="*60)
for pays in df.columns:
    annee_min = taux_croissance[pays].idxmin()
    valeur_min = taux_croissance[pays].min()
    print(f"{pays:12s} : {annee_min} ({valeur_min:,.2f}%)")

# Calcul de la croissance totale sur la période (2018-2023)
print("\n📊 CROISSANCE TOTALE 2018-2023 (%)")
print("="*60)
croissance_totale = ((df.loc[2023] / df.loc[2018]) - 1) * 100
for pays, valeur in croissance_totale.sort_values(ascending=False).items():
    print(f"{pays:12s} : {valeur:>8,.2f} %")
```

**Explication** : Le taux de croissance mesure la variation relative du PIB d'une année à l'autre. C'est un indicateur clé de la santé économique. Un taux négatif indique une récession, un taux positif une expansion.

---

### 📊 Section 6 : Comparaisons et classements

```python
# ============================================
# COMPARAISONS ET CLASSEMENTS
# ============================================

# Classement des pays par PIB en 2023
print("\n🏆 CLASSEMENT PAR PIB 2023")
print("="*60)
classement_2023 = df.loc[2023].sort_values(ascending=False)
for rang, (pays, valeur) in enumerate(classement_2023.items(), 1):
    print(f"{rang}. {pays:12s} : {valeur:>10,.0f} Mds USD")

# Calcul des parts de marché (pourcentage du PIB mondial)
pib_mondial_2023 = df.loc[2023].sum()
print(f"\n🌍 PIB Mondial combiné (5 pays) : {pib_mondial_2023:,.0f} Mds USD")
print("\n📊 PARTS DE MARCHÉ 2023")
print("="*60)
for pays in classement_2023.index:
    part = (df.loc[2023, pays] / pib_mondial_2023) * 100
    print(f"{pays:12s} : {part:>6,.2f} %")

# Comparaison 2018 vs 2023
print("\n📊 ÉVOLUTION 2018 → 2023")
print("="*70)
for pays in df.columns:
    pib_2018 = df.loc[2018, pays]
    pib_2023 = df.loc[2023, pays]
    evolution = pib_2023 - pib_2018
    evolution_pct = ((pib_2023 / pib_2018) - 1) * 100
    print(f"{pays:12s} : {pib_2018:>8,.0f} → {pib_2023:>8,.0f} Mds USD")
    print(f"{'':12s}   (+{evolution:>8,.0f} Mds USD, +{evolution_pct:>6,.1f}%)")
```

**Explication** : Les classements permettent de visualiser la hiérarchie économique mondiale. Les parts de marché montrent le poids relatif de chaque économie dans l'ensemble étudié.

---

### 📈 Section 7 : Analyse des corrélations

```python
# ============================================
# ANALYSE DES CORRÉLATIONS
# ============================================

# Calcul de la matrice de corrélation entre les PIB des pays
# La corrélation mesure la relation linéaire entre deux variables
# Valeurs entre -1 (corrélation négative parfaite) et +1 (corrélation positive parfaite)
matrice_correlation = df.corr()

print("\n🔗 MATRICE DE CORRÉLATION")
print("="*70)
print(matrice_correlation.round(3))

# Identification des paires de pays les plus corrélées
print("\n🤝 PAIRES DE PAYS HAUTEMENT CORRÉLÉES (r > 0.9)")
print("="*70)
for i in range(len(matrice_correlation.columns)):
    for j in range(i+1, len(matrice_correlation.columns)):
        pays1 = matrice_correlation.columns[i]
        pays2 = matrice_correlation.columns[j]
        corr = matrice_correlation.iloc[i, j]
        if abs(corr) > 0.9:
            print(f"{pays1:12s} ↔ {pays2:12s} : r = {corr:.3f}")

# Interprétation des corrélations
print("\n💡 INTERPRÉTATION")
print("="*70)
print("r > 0.7  : Corrélation forte positive (économies synchronisées)")
print("0.3 < r < 0.7 : Corrélation modérée")
print("r < 0.3  : Corrélation faible")
print("r < 0    : Corrélation négative (relation inverse)")
```

**Explication** : La corrélation mesure à quel point deux économies évoluent de manière similaire. Une corrélation élevée indique que les économies sont interconnectées et réagissent de manière similaire aux chocs économiques.

---

### 📊 Section 8 : Visualisation - Évolution temporelle

```python
# ============================================
# VISUALISATION 1 : ÉVOLUTION DU PIB
# ============================================

# Création d'une figure avec taille personnalisée
plt.figure(figsize=(14, 8))

# Couleurs personnalisées pour chaque pays
couleurs = {
    'USA': '#1f77b4',       # Bleu
    'Chine': '#ff7f0e',     # Orange
    'Japon': '#2ca02c',     # Vert
    'Allemagne': '#d62728', # Rouge
    'Inde': '#9467bd'       # Violet
}

# Tracé d'une ligne pour chaque pays
for pays in df.columns:
    plt.plot(df.index,              # Axe X : années
             df[pays],               # Axe Y : PIB
             marker='o',             # Marqueurs circulaires aux points
             linewidth=2.5,          # Épaisseur de ligne
             markersize=8,           # Taille des marqueurs
             label=pays,             # Légende
             color=couleurs[pays])   # Couleur personnalisée

# Configuration du titre avec style professionnel
plt.title('Évolution du PIB nominal (2018-2023)', 
          fontsize=18, 
          fontweight='bold',
          pad=20)

# Configuration des axes
plt.xlabel('Année', fontsize=14, fontweight='bold')
plt.ylabel('PIB (Milliards USD)', fontsize=14, fontweight='bold')

# Ajout d'une grille pour faciliter la lecture
plt.grid(True, alpha=0.3, linestyle='--', linewidth=0.7)

# Configuration de la légende
plt.legend(fontsize=12, 
           loc='upper left',
           frameon=True,
           shadow=True)

# Ajustement automatique de la mise en page
plt.tight_layout()

# Sauvegarde de la figure en haute résolution
plt.savefig('gdp_evolution.png', dpi=300, bbox_inches='tight')

# Affichage du graphique
plt.show()

print("✓ Graphique 1 généré : gdp_evolution.png")
```

**Explication** : Ce graphique en ligne montre l'évolution temporelle du PIB pour tous les pays. Il permet d'identifier visuellement les tendances, les points d'inflexion (comme la chute de 2020), et les trajectoires de croissance.

---

### 📊 Section 9 : Visualisation - Comparaison par pays

```python
# ============================================
# VISUALISATION 2 : COMPARAISON 2023
# ============================================

# Extraction des données de 2023 et tri décroissant
gdp_2023 = df.loc[2023].sort_values(ascending=False)

# Création de la figure
plt.figure(figsize=(12, 7))

# Création du graphique en barres
barres = plt.bar(gdp_2023.index,           # Pays (axe X)
                  gdp_2023.values,          # PIB (axe Y)
                  color=[couleurs[p] for p in gdp_2023.index],  # Couleurs
                  edgecolor='black',        # Bordure noire
                  linewidth=1.5,            # Épaisseur bordure
                  alpha=0.8)                # Transparence

# Ajout des valeurs au-dessus de chaque barre
for i, (pays, valeur) in enumerate(gdp_2023.items()):
    plt.text(i,                             # Position X
             valeur + 500,                  # Position Y (légèrement au-dessus)
             f'{valeur:,.0f}',              # Texte formaté
             ha='center',                   # Alignement horizontal centré
             va='bottom',                   # Alignement vertical bas
             fontsize=11,
             fontweight='bold')

# Configuration du titre
plt.title('Comparaison du PIB nominal en 2023', 
          fontsize=18, 
          fontweight='bold',
          pad=20)

# Configuration des axes
plt.xlabel('Pays', fontsize=14, fontweight='bold')
plt.ylabel('PIB (Milliards USD)', fontsize=14, fontweight='bold')

# Rotation des labels de l'axe X pour meilleure lisibilité
plt.xticks(rotation=45, ha='right', fontsize=12)

# Ajout d'une grille horizontale
plt.grid(axis='y', alpha=0.3, linestyle='--', linewidth=0.7)

# Ajustement de la mise en page
plt.tight_layout()

# Sauvegarde
plt.savefig('gdp_comparison_2023.png', dpi=300, bbox_inches='tight')

plt.show()

print("✓ Graphique 2 généré : gdp_comparison_2023.png")
```

**Explication** : Le graphique en barres permet une comparaison directe et visuelle des PIB en 2023. Les valeurs affichées au-dessus des barres facilitent la lecture précise des données.

---

### 📊 Section 10 : Visualisation - Taux de croissance

```python
# ============================================
# VISUALISATION 3 : TAUX DE CROISSANCE
# ============================================

plt.figure(figsize=(14, 8))

# Tracé des taux de croissance pour chaque pays
for pays in taux_croissance.columns:
    plt.plot(taux_croissance.index,
             taux_croissance[pays],
             marker='s',              # Marqueurs carrés
             linewidth=2.5,
             markersize=7,
             label=pays,
             color=couleurs[pays])

# Ajout d'une ligne horizontale à 0% (référence)
plt.axhline(y=0, color='black', linestyle='--', linewidth=1, alpha=0.5)

# Configuration du titre
plt.title('Taux de croissance annuel du PIB (%)', 
          fontsize=18, 
          fontweight='bold',
          pad=20)

# Configuration des axes
plt.xlabel('Année', fontsize=14, fontweight='bold')
plt.ylabel('Taux de croissance (%)', fontsize=14, fontweight='bold')

# Grille
plt.grid(True, alpha=0.3, linestyle='--', linewidth=0.7)

# Légende
plt.legend(fontsize=12, loc='lower right', frameon=True, shadow=True)

# Zone de récession (2020) mise en évidence
plt.axvspan(2019.5, 2020.5, alpha=0.2, color='red', label='COVID-19')

plt.tight_layout()
plt.savefig('growth_rates.png', dpi=300, bbox_inches='tight')
plt.show()

print("✓ Graphique 3 généré : growth_rates.png")
```

**Explication** : Ce graphique montre la dynamique de croissance. La ligne à 0% sépare croissance (au-dessus) et récession (en dessous). La zone rouge met en évidence l'impact COVID-19.

---

### 📊 Section 11 : Visualisation - Heatmap des corrélations

```python
# ============================================
# VISUALISATION 4 : HEATMAP DES CORRÉLATIONS
# ============================================

plt.figure(figsize=(10, 8))

# Création de la heatmap avec seaborn
sns.heatmap(matrice_correlation,
            annot=True,                    # Afficher les valeurs
            fmt='.3f',                     # Format à 3 décimales
            cmap='coolwarm',               # Palette de couleurs (bleu-rouge)
            center=0,                      # Centrer la palette sur 0
            square=True,                   # Cases carrées
            linewidths=1,                  # Lignes de séparation
            cbar_kws={'label': 'Coefficient de corrélation'},
            vmin=-1, vmax=1)               # Échelle de -1 à 1

# Configuration du titre
plt.title('Matrice de corrélation des PIB', 
          fontsize=18, 
          fontweight='bold',
          pad=20)

# Rotation des labels
plt.xticks(rotation=45, ha='right')
plt.yticks(rotation=0)

plt.tight_layout()
plt.savefig('correlation_heatmap.png', dpi=300, bbox_inches='tight')
plt.show()

print("✓ Graphique 4 généré : correlation_heatmap.png")
```

**Explication** : La heatmap (carte de chaleur) visualise toutes les corrélations simultanément. Les couleurs chaudes (rouge) indiquent une corrélation positive forte, les couleurs froides (bleu) une corrélation négative.

---

### 📊 Section 12 : Visualisation - PIB par habitant

```python
# ============================================
# VISUALISATION 5 : PIB PAR HABITANT 2023
# ============================================

# Données du PIB par habitant (en USD)
pib_per_capita = {
    'USA': 81695,
    'Allemagne': 49190,
    'Japon': 33815,
    'Chine': 12720,
    'Inde': 2612
}

# Création d'un DataFrame
df_per_capita = pd.Series(pib_per_capita).sort_values(ascending=True)

plt.figure(figsize=(12, 7))

# Graphique en barres horizontales pour meilleure lisibilité
barres = plt.barh(df_per_capita.index,
                   df_per_capita.values,
                   color=[couleurs[p] for p in df_per_capita.index],
                   edgecolor='black',
                   linewidth=1.5,
                   alpha=0.8)

# Ajout des valeurs à droite de chaque barre
for i, (pays, valeur) in enumerate(df_per_capita.items()):
    plt.text(valeur + 1000,
             i,
             f'{valeur:,.0f} USD',
             va='center',
             fontsize=11,
             fontweight='bold')

plt.title('PIB par habitant en 2023', 
          fontsize=18, 
          fontweight='bold',
          pa
