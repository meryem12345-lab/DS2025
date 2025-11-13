# Rapport d'Analyse Approfondie du PIB
## Comparaison Internationale des Principales Économies Mondiales (2020-2024)

---

## 1. Introduction et Contexte

### 1.1 Objectif de l'analyse

Ce rapport vise à analyser de manière approfondie l'évolution du Produit Intérieur Brut (PIB) de huit économies majeures représentant différentes régions du monde. L'objectif est de comprendre les dynamiques économiques, d'identifier les tendances de croissance et d'établir des comparaisons significatives entre les performances économiques de ces pays sur la période 2020-2024.

### 1.2 Méthodologie générale employée

L'analyse repose sur une approche quantitative combinant :
- **Analyse descriptive** : Calcul de statistiques centrales et de dispersion
- **Analyse comparative** : Comparaison transversale entre pays
- **Analyse temporelle** : Étude de l'évolution sur 5 ans
- **Visualisation de données** : Représentations graphiques multiples pour faciliter l'interprétation

### 1.3 Pays sélectionnés et période d'analyse

**Pays sélectionnés** (représentant 65% du PIB mondial) :
1. 🇺🇸 **États-Unis** - Première économie mondiale
2. 🇨🇳 **Chine** - Deuxième économie mondiale
3. 🇩🇪 **Allemagne** - Première économie européenne
4. 🇯🇵 **Japon** - Troisième économie développée
5. 🇬🇧 **Royaume-Uni** - Économie post-Brexit
6. 🇫🇷 **France** - Cinquième économie de la zone euro
7. 🇮🇳 **Inde** - Économie émergente à forte croissance
8. 🇧🇷 **Brésil** - Plus grande économie d'Amérique du Sud

**Période d'analyse** : 2020-2024 (5 ans)

Cette période est particulièrement intéressante car elle englobe :
- L'impact de la pandémie COVID-19 (2020-2021)
- La phase de reprise économique (2022)
- Les tensions géopolitiques et inflationnistes (2023-2024)

### 1.4 Questions de recherche principales

1. Quelle a été l'évolution du PIB nominal de ces pays entre 2020 et 2024 ?
2. Quels pays ont connu la croissance la plus forte et pourquoi ?
3. Comment le PIB par habitant diffère-t-il entre ces économies ?
4. Quelles corrélations peut-on observer entre les performances économiques ?
5. Quels enseignements peut-on tirer pour anticiper les tendances futures ?

---

## 2. Présentation des Données

### 2.1 Source des données

**Source principale** : Banque mondiale (World Bank Open Data)
- Base de données : Indicateurs du développement dans le monde (WDI)
- Accès : https://donnees.banquemondiale.org
- Indicateurs utilisés : NY.GDP.MKTP.CD, NY.GDP.PCAP.CD, NY.GDP.MKTP.KD.ZG

**Sources complémentaires** :
- Fonds Monétaire International (FMI) - World Economic Outlook Database
- OCDE - Comptes nationaux

### 2.2 Variables analysées

| Variable | Description | Unité | Code WDI |
|----------|-------------|-------|----------|
| **PIB nominal** | Produit Intérieur Brut en dollars courants | Milliards USD | NY.GDP.MKTP.CD |
| **PIB par habitant** | PIB divisé par la population | USD/habitant | NY.GDP.PCAP.CD |
| **Taux de croissance** | Variation annuelle du PIB réel | % annuel | NY.GDP.MKTP.KD.ZG |
| **Population** | Population totale du pays | Millions d'habitants | SP.POP.TOTL |

### 2.3 Période couverte

- **Période principale** : 2020-2024
- **Fréquence** : Annuelle
- **Dernière mise à jour** : Novembre 2024

### 2.4 Qualité et limitations des données

**Points forts** :
- ✅ Données officielles provenant d'institutions reconnues
- ✅ Méthodologie standardisée (Système de Comptabilité Nationale)
- ✅ Couverture géographique exhaustive
- ✅ Séries temporelles cohérentes

**Limitations identifiées** :
- ⚠️ Données 2024 : estimations préliminaires (susceptibles de révision)
- ⚠️ Conversion en USD : sensible aux variations de taux de change
- ⚠️ PIB ne mesure pas le bien-être, les inégalités ou la durabilité
- ⚠️ Économie informelle non capturée dans certains pays émergents
- ⚠️ Comparaisons internationales complexifiées par les différences de méthodologie

### 2.5 Tableau récapitulatif des données (2024)

| Pays | PIB 2024 (Mds USD) | PIB/hab (USD) | Croissance 2024 (%) | Population (M) |
|------|-------------------|---------------|---------------------|----------------|
| 🇺🇸 États-Unis | 28 782 | 85 380 | 2.8 | 337 |
| 🇨🇳 Chine | 18 532 | 13 140 | 4.9 | 1 411 |
| 🇩🇪 Allemagne | 4 660 | 55 640 | -0.2 | 84 |
| 🇯🇵 Japon | 4 291 | 34 230 | 0.7 | 125 |
| 🇬🇧 Royaume-Uni | 3 340 | 49 070 | 1.1 | 68 |
| 🇫🇷 France | 3 130 | 47 360 | 1.1 | 66 |
| 🇮🇳 Inde | 3 890 | 2 730 | 6.5 | 1 425 |
| 🇧🇷 Brésil | 2 331 | 10 850 | 3.0 | 215 |

*Source : Banque mondiale, 2024 (estimations)*

---

## 3. Préparation et Traitement des Données

### 3.1 Importation des bibliothèques

```python
# Bibliothèques pour la manipulation de données
import pandas as pd  # Manipulation et analyse de données tabulaires
import numpy as np   # Calculs numériques et opérations sur tableaux

# Bibliothèques pour la visualisation
import matplotlib.pyplot as plt  # Création de graphiques statiques
import seaborn as sns           # Visualisations statistiques avancées

# Configuration de l'affichage
import warnings
warnings.filterwarnings('ignore')  # Masquer les avertissements non critiques

# Configuration des styles de graphiques
plt.style.use('seaborn-v0_8-darkgrid')  # Style professionnel
sns.set_palette("husl")                  # Palette de couleurs harmonieuse

# Configuration de l'affichage des figures
plt.rcParams['figure.figsize'] = (14, 8)    # Taille par défaut des figures
plt.rcParams['font.size'] = 11              # Taille de police
plt.rcParams['axes.labelsize'] = 12         # Taille des labels d'axes
plt.rcParams['axes.titlesize'] = 14         # Taille des titres
plt.rcParams['xtick.labelsize'] = 10        # Taille des labels x
plt.rcParams['ytick.labelsize'] = 10        # Taille des labels y
plt.rcParams['legend.fontsize'] = 10        # Taille de la légende
plt.rcParams['figure.titlesize'] = 16       # Taille du titre de figure

# Affichage complet des DataFrames
pd.set_option('display.max_columns', None)   # Afficher toutes les colonnes
pd.set_option('display.width', None)         # Largeur illimitée
pd.set_option('display.precision', 2)        # 2 décimales
```

**Explication** : Ces bibliothèques constituent la base de toute analyse de données en Python. Pandas permet de manipuler des données sous forme de tableaux, NumPy effectue des calculs numériques, et Matplotlib/Seaborn créent des visualisations professionnelles.

---

### 3.2 Création du jeu de données

```python
# Création d'un dictionnaire contenant les données PIB (en milliards USD)
# Source : Banque mondiale, 2024
gdp_data = {
    'Pays': ['États-Unis', 'Chine', 'Allemagne', 'Japon', 'Royaume-Uni', 
             'France', 'Inde', 'Brésil'],
    
    # PIB nominal 2020 (impact COVID-19)
    '2020': [20937, 14723, 3846, 5048, 2708, 2630, 2671, 1449],
    
    # PIB nominal 2021 (début de reprise)
    '2021': [23315, 17734, 4223, 4937, 3108, 2958, 3173, 1609],
    
    # PIB nominal 2022 (reprise post-COVID)
    '2022': [25464, 17963, 4072, 4231, 3070, 2783, 3385, 1920],
    
    # PIB nominal 2023 (stabilisation)
    '2023': [27361, 17886, 4456, 4213, 3340, 3049, 3730, 2174],
    
    # PIB nominal 2024 (estimations)
    '2024': [28782, 18532, 4660, 4291, 3340, 3130, 3890, 2331]
}

# Conversion en DataFrame pandas pour faciliter la manipulation
df = pd.DataFrame(gdp_data)

# Affichage du DataFrame
print("=== Données PIB Brutes (Milliards USD) ===")
print(df)
print("\n")
```

**Explication** : Nous créons un tableau structuré contenant les données de PIB nominal pour 8 pays sur 5 ans. Les valeurs sont exprimées en milliards de dollars courants, ce qui permet des comparaisons directes.

---

### 3.3 Ajout des données démographiques et PIB par habitant

```python
# Dictionnaire des populations (en millions d'habitants)
# Source : Banque mondiale, 2024
populations_2024 = {
    'États-Unis': 337,
    'Chine': 1411,
    'Allemagne': 84,
    'Japon': 125,
    'Royaume-Uni': 68,
    'France': 66,
    'Inde': 1425,
    'Brésil': 215
}

# Ajout de la colonne population au DataFrame
df['Population_2024'] = df['Pays'].map(populations_2024)

# Calcul du PIB par habitant 2024
# Formule : (PIB en milliards * 1000) / Population en millions = PIB/hab en milliers
df['PIB_par_habitant_2024'] = (df['2024'] * 1000) / df['Population_2024']

# Conversion en entier pour lisibilité
df['PIB_par_habitant_2024'] = df['PIB_par_habitant_2024'].astype(int)

print("=== Données avec Population et PIB par Habitant ===")
print(df[['Pays', '2024', 'Population_2024', 'PIB_par_habitant_2024']])
print("\n")
```

**Explication** : Le PIB par habitant est un indicateur crucial qui rapporte la richesse produite à la taille de la population. Il donne une meilleure indication du niveau de vie moyen qu'un PIB brut.

---

### 3.4 Transformation des données pour l'analyse temporelle

```python
# Création d'une version "longue" du DataFrame pour faciliter les visualisations temporelles
# On transforme les colonnes d'années en lignes

# Sélection des colonnes d'années
annees = ['2020', '2021', '2022', '2023', '2024']

# Transformation du format large au format long
df_long = df.melt(
    id_vars=['Pays'],           # Colonne à conserver
    value_vars=annees,          # Colonnes à transformer
    var_name='Année',           # Nom de la nouvelle colonne pour les années
    value_name='PIB'            # Nom de la nouvelle colonne pour les valeurs
)

# Conversion de la colonne Année en type entier
df_long['Année'] = df_long['Année'].astype(int)

# Tri par pays et année
df_long = df_long.sort_values(['Pays', 'Année']).reset_index(drop=True)

print("=== Données au Format Long (premières lignes) ===")
print(df_long.head(10))
print(f"\nNombre total d'observations : {len(df_long)}")
print("\n")
```

**Explication** : La transformation "melt" convertit les données d'un format large (années en colonnes) à un format long (années en lignes). Ce format est optimal pour créer des graphiques temporels avec des bibliothèques comme Seaborn.

---

### 3.5 Calcul des taux de croissance

```python
# Calcul des taux de croissance annuels pour chaque pays
# Formule : ((PIB année N / PIB année N-1) - 1) * 100

# Création d'un nouveau DataFrame pour les taux de croissance
croissance = pd.DataFrame()
croissance['Pays'] = df['Pays']

# Calcul de la croissance pour chaque période
for i in range(len(annees) - 1):
    annee_actuelle = annees[i + 1]
    annee_precedente = annees[i]
    nom_colonne = f'Croissance_{annee_precedente}-{annee_actuelle}'
    
    # Formule de croissance : ((valeur_n / valeur_n-1) - 1) * 100
    croissance[nom_colonne] = ((df[annee_actuelle] / df[annee_precedente]) - 1) * 100
    
    # Arrondir à 2 décimales
    croissance[nom_colonne] = croissance[nom_colonne].round(2)

print("=== Taux de Croissance Annuels (%) ===")
print(croissance)
print("\n")

# Calcul de la croissance moyenne sur la période
croissance['Croissance_Moyenne'] = croissance.iloc[:, 1:].mean(axis=1).round(2)

print("=== Croissance Moyenne 2020-2024 ===")
print(croissance[['Pays', 'Croissance_Moyenne']].sort_values('Croissance_Moyenne', ascending=False))
print("\n")
```

**Explication** : Le taux de croissance mesure la variation relative du PIB d'une année à l'autre. C'est un indicateur clé de la dynamique économique d'un pays.

---

## 4. Analyse Statistique Approfondie

### 4.1 Statistiques descriptives globales

```python
# Calcul des statistiques descriptives pour le PIB 2024
stats_2024 = df['2024'].describe()

print("=== Statistiques Descriptives - PIB 2024 (Milliards USD) ===")
print(f"Nombre de pays analysés : {stats_2024['count']:.0f}")
print(f"PIB moyen : {stats_2024['mean']:,.0f} Mds USD")
print(f"Écart-type : {stats_2024['std']:,.0f} Mds USD")
print(f"PIB minimum : {stats_2024['min']:,.0f} Mds USD ({df[df['2024'] == stats_2024['min']]['Pays'].values[0]})")
print(f"PIB médian : {stats_2024['50%']:,.0f} Mds USD")
print(f"PIB maximum : {stats_2024['max']:,.0f} Mds USD ({df[df['2024'] == stats_2024['max']]['Pays'].values[0]})")
print(f"\nCoefficient de variation : {(stats_2024['std'] / stats_2024['mean'] * 100):.1f}%")
print("  → Forte dispersion, économies très hétérogènes")
print("\n")

# Statistiques pour le PIB par habitant
stats_pib_hab = df['PIB_par_habitant_2024'].describe()

print("=== Statistiques Descriptives - PIB par Habitant 2024 (USD) ===")
print(f"PIB/hab moyen : {stats_pib_hab['mean']:,.0f} USD")
print(f"Écart-type : {stats_pib_hab['std']:,.0f} USD")
print(f"PIB/hab minimum : {stats_pib_hab['min']:,.0f} USD ({df[df['PIB_par_habitant_2024'] == stats_pib_hab['min']]['Pays'].values[0]})")
print(f"PIB/hab médian : {stats_pib_hab['50%']:,.0f} USD")
print(f"PIB/hab maximum : {stats_pib_hab['max']:,.0f} USD ({df[df['PIB_par_habitant_2024'] == stats_pib_hab['max']]['Pays'].values[0]})")
print(f"\nRapport Max/Min : {stats_pib_hab['max'] / stats_pib_hab['min']:.1f}x")
print("  → Les États-Unis ont un PIB/hab 31x supérieur à l'Inde")
print("\n")
```

**Explication** : Les statistiques descriptives donnent une vue d'ensemble de la distribution des données. L'écart-type élevé indique une grande disparité entre les économies analysées.

---

### 4.2 Analyse comparative entre pays

```python
# Création d'un tableau de comparaison multi-critères
comparaison = pd.DataFrame({
    'Pays': df['Pays'],
    'PIB_2024': df['2024'],
    'PIB_2020': df['2020'],
    'Évolution_Absolue': df['2024'] - df['2020'],
    'Évolution_Relative_%': ((df['2024'] / df['2020']) - 1) * 100,
    'PIB_par_habitant': df['PIB_par_habitant_2024'],
    'Population_M': df['Population_2024']
})

# Arrondir les valeurs pour lisibilité
comparaison['Évolution_Relative_%'] = comparaison['Évolution_Relative_%'].round(1)
comparaison['PIB_2024'] = comparaison['PIB_2024'].round(0)
comparaison['Évolution_Absolue'] = comparaison['Évolution_Absolue'].round(0)

# Tri par PIB 2024 décroissant
comparaison = comparaison.sort_values('PIB_2024', ascending=False)

print("=== Tableau Comparatif Complet (2020-2024) ===")
print(comparaison.to_string(index=False))
print("\n")

# Identification des leaders
print("=== Analyse des Leaders ===")
print(f"🥇 Plus grand PIB : {comparaison.iloc[0]['Pays']} ({comparaison.iloc[0]['PIB_2024']:,.0f} Mds USD)")
print(f"🥈 Deuxième PIB : {comparaison.iloc[1]['Pays']} ({comparaison.iloc[1]['PIB_2024']:,.0f} Mds USD)")
print(f"🥉 Troisième PIB : {comparaison.iloc[2]['Pays']} ({comparaison.iloc[2]['PIB_2024']:,.0f} Mds USD)")

# Plus forte croissance
idx_croissance = comparaison['Évolution_Relative_%'].idxmax()
print(f"\n📈 Plus forte croissance 2020-2024 : {comparaison.loc[idx_croissance, 'Pays']} "
      f"({comparaison.loc[idx_croissance, 'Évolution_Relative_%']}%)")

# PIB par habitant le plus élevé
idx_pib_hab = comparaison['PIB_par_habitant'].idxmax()
print(f"💰 PIB/habitant le plus élevé : {comparaison.loc[idx_pib_hab, 'Pays']} "
      f"({comparaison.loc[idx_pib_hab, 'PIB_par_habitant']:,} USD)")
print("\n")
```

**Explication** : Cette analyse comparative permet d'identifier les pays leaders sur différents critères et de comprendre les dynamiques de croissance sur la période 2020-2024.

---

### 4.3 Analyse de la concentration économique

```python
# Calcul du PIB total mondial (pour l'échantillon)
pib_total = df['2024'].sum()

# Calcul des parts de marché
df['Part_PIB_%'] = (df['2024'] / pib_total * 100).round(1)

# Tri par part décroissante
parts = df[['Pays', 'Part_PIB_%']].sort_values('Part_PIB_%', ascending=False)

print("=== Concentration Économique - Parts du PIB Total ===")
print(parts.to_string(index=False))
print(f"\nPIB total (échantillon) : {pib_total:,.0f} Mds USD")

# Calcul de l'indice de concentration (Herfindahl)
indice_herfindahl = (df['Part_PIB_%'] ** 2).sum()
print(f"\nIndice Herfindahl-Hirschman : {indice_herfindahl:.0f}")
print("  → HHI > 1800 = Concentration élevée (domination USA + Chine)")

# Calcul des parts cumulées
parts['Part_Cumulative_%'] = parts['Part_PIB_%'].cumsum()
print("\n=== Concentration Cumulée ===")
for i in range(min(3, len(parts))):
    pays_top = parts.iloc[:i+1]['Pays'].tolist()
    part_cum = parts.iloc[i]['Part_Cumulative_%']
    print(f"Top {i+1} pays ({', '.join(pays_top)}) : {part_cum:.1f}%")
print("\n")
```

**Explication** : L'analyse de concentration révèle le degré de domination de certaines économies. Un indice de Herfindahl élevé indique une forte concentration, ce qui est le cas ici avec les États-Unis et la Chine représentant près de 65% du PIB de l'échantillon.

---

### 4.4 Analyse de corrélation

```python
# Préparation des données pour l'analyse de corrélation
df_corr = df[['2020', '2021', '2022', '2023', '2024', 'Population_2024', 'PIB_par_habitant_2024']].copy()

# Calcul de la matrice de corrélation
matrice_correlation = df_corr.corr()

print("=== Matrice de Corrélation ===")
print(matrice_correlation.round(2))
print("\n")

# Analyse des corrélations les plus fortes
print("=== Corrélations Clés ===")
print(f"PIB 2024 vs Population : {matrice_correlation.loc['2024', 'Population_2024']:.3f}")
print("  → Corrélation positive modérée : population importante ne garantit pas un PIB élevé")
print(f"\nPIB 2024 vs PIB/habitant : {matrice_correlation.loc['2024', 'PIB_par_habitant_2024']:.3f}")
print("  → Corrélation faible : les grands PIB ne sont pas forcément les plus riches par habitant")
print(f"\nPIB 2020 vs PIB 2024 : {matrice_correlation.loc['2020', '2024']:.3f}")
print("  → Corrélation très forte : stabilité des positions économiques relatives")
print("\n")
```

**Explication** : L'analyse de corrélation permet d'identifier les relations entre variables. Une corrélation élevée entre PIB 2020 et 2024 montre que le classement économique mondial est relativement stable.

---

### 4.5 Calcul de la croissance cumulée

```python
# Calcul de la croissance cumulée sur la période 2020-2024
df['Croissance_Cumulee_%'] = ((df['2024'] / df['2020']) - 1) * 100

# Calcul du Taux de Croissance Annuel Moyen (TCAM)
# Formule : ((Valeur_finale / Valeur_initiale)^(1/nombre_années)) - 1
nombre_annees = 4  # 2020 à 2024 = 4 périodes
df['TCAM_%'] = ((df['2024'] / df['2020']) ** (1/nombre_annees) - 1) * 100

# Création du tableau récapitulatif
synthese_croissance = df[['Pays', '2020', '2024', 'Croissance_Cumulee_%', 'TCAM_%']].copy()
synthese_croissance = synthese_croissance.sort_values('TCAM_%', ascending=False)

# Arrondir les valeurs
synthese_croissance['Croissance_Cumulee_%'] = synthese_croissance['Croissance_Cumulee_%'].round(1)
synthese_croissance['TCAM_%'] = synthese_croissance['TCAM_%'].round(2)

print("=== Synthèse de la Croissance 2020-2024 ===")
print(synthese_croissance.to_string(index=False))
print("\n")

# Identification des performances
print("=== Performances Économiques ===")
print("\n🚀 Croissance Forte (TCAM > 5%) :")
for _, row in synthese_croissance[synthese_croissance['TCAM_%'] > 5].iterrows():
    print(f"   • {row['Pays']}: +{row['TCAM_%']:.2f}% par an (Économie émergente dynamique)")

print("\n📊 Croissance Modérée (TCAM 2-5%) :")
for _, row in synthese_croissance[(synthese_croissance['TCAM_%'] >= 2) & (synthese_croissance['TCAM_%'] <= 5)].iterrows():
    print(f"   • {row['Pays']}: +{row['TCAM_%']:.2f}% par an")

print("\n⚠️ Croissance Faible (TCAM < 2%) :")
for _, row in synthese_croissance[synthese_croissance['TCAM_%'] < 2].iterrows():
    print(f"   • {row['Pays']}: +{row['TCAM_%']:.2f}% par an (Économie mature)")
print("\n")
```

**Explication** : Le Taux de Croissance Annuel Moyen (TCAM) lisse les variations annuelles pour donner une vision globale de la performance sur la période. Il permet de comparer objectivement la dynamique de croissance entre pays malgré leurs tailles différentes.

---

## 5. Visualisations et Graphiques

### 5.1 Graphique en ligne - Évolution temporelle du PIB

```python
# Création de la figure avec une taille appropriée
plt.figure(figsize=(16, 9))

# Boucle pour tracer chaque pays
for pays in df['Pays']:
    # Extraction des données pour le pays
    donnees_pays = df[df['Pays'] == pays][annees].values[0]
    
    # Traçage de la courbe avec marqueurs
    plt.plot(annees, donnees_pays, marker='o', linewidth=2.5, 
             markersize=8, label=pays, alpha=0.8)

# Configuration du graphique
plt.title('Évolution du PIB Nominal par Pays (2020-2024)', 
          fontsize=18, fontweight='bold', pad=20)
plt.xlabel('Année', fontsize=14, fontweight='bold')
plt.ylabel('PIB (Milliards USD)', fontsize=14, fontweight='bold')

# Grille pour faciliter la lecture
plt.grid(True, alpha=0.3, linestyle='--', linewidth=0.7)

# Légende positionnée de manière optimale
plt.legend(loc='upper left', frameon=True, shadow=True, 
           fancybox=True, fontsize=11)

# Format des axes
plt.xticks(annees, fontsize=12)
plt.yticks(fontsize=12)

# Ajout d'annotations pour les valeurs 2024
for pays in df['Pays']:
    valeur_2024 = df[df['Pays'] == pays]['2024'].values[0]
    plt.annotate(f'{valeur_2024:.0f}', 
                xy=('2024', valeur_2024),
                xytext=(5, 0), textcoords='offset points',
                fontsize=9, alpha=0.7)

# Ajustement automatique de la mise en page
plt.tight_layout()
plt.show()

print("✓ Graphique 1 : Évolution temporelle généré avec succès")
print("\n")
```

**Interprétation** : Ce graphique révèle plusieurs tendances clés :
- **Stabilité des leaders** : Les États-Unis et la Chine maintiennent leur domination
- **Impact COVID-19** : Rupture visible en 2020 pour plusieurs pays
- **Trajectoires divergentes** : Inde et