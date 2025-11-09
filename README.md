# Analyse Géologique Minière — Visualisations & Prototype
Auteur : Mamadou DIAKHABY — Data Engineer | Pipelines ETL/ELT

Petit prototype Python pour la visualisation géologique/minière : log de forage, carte de teneurs (interpolation), rose des fractures, corrélation géochimique Cu-Au, profil topographique et histogramme des teneurs.

> Données simulées et partiellement réelles — script pédagogique / prototype. Pour des usages production (krigeage, reporting officiel), brancher un jeu de données réel et utiliser des outils géostatistiques (pykrige, gstools).

# Fonctionnalités
- Visualisations : log géophysique, carte d'interpolation 2D, rose des fractures, scatter Cu-Au avec R², profil topographique, distribution des teneurs.
- Calculs résumés : moyenne/mediane teneurs, tonnage au-dessus du seuil, corrélation Cu-Au, direction moyenne des fractures.
- Prototype facilement extensible : modularisation recommandée, options d'export des figures, paramétrage via config.

## Pré-requis
- Python 3.9+
- Packages :
  - numpy
  - pandas
  - matplotlib
  - scipy
  - seaborn

Exemple 'requirements.txt' :

numpy>=1.22
pandas>=1.4
matplotlib>=3.5
scipy>=1.8
seaborn>=0.12

# Installation
  bash
# cloner le repo
git clone https://github.com/Diakhaby-data/Projet_minier.git
cd Projet_minier

# créer un environnement virtuel (recommandé)
python -m venv .venv
source .venv/bin/activate    # Linux / macOS
.venv\Scripts\activate       # Windows

# installer dépendances
pip install -r requirements.txt

# Utilisation
# Exécution simple (prototype)

python plot_prototype.py

* `plot_prototype.py` génère la figure 2x3 et affiche `plt.show()`.
* Pour exécution sans affichage (CI / serveur), modifier le script pour sauvegarder l'image :

plt.savefig('report.png', dpi=300, bbox_inches='tight')

# Paramétrage conseillé
* Déplacer les paramètres en haut du script ou lire depuis `config.yml` :
   * `SEED`, `FIGSIZE`, `SEUIL_COUPURE`, `N_BINS`, chemins d'entrée/sortie.

# Suggestions d'amélioration (roadmap)
1. Modulariser le code en fonctions et ajouter tests unitaires (`pytest`).
2. Brancher un jeu de données réel (CSV / DB) et standardiser les colonnes attendues.
3. Remplacer `griddata` par un vrai krigeage (`pykrige`) pour estimation + incertitude.
4. Ajouter un notebook Jupyter interactif (`notebooks/demo.ipynb`) pour exploration.
5. Intégrer export automatique des rapports (PNG / PDF) et génération d'un petit dashboard (Dash / Panel).

# Structure de projet recommandée

Projet_minier/
├─ data/                # jeux de données d'exemple (gitignore si volumineux)
├─ notebooks/           # notebooks d'exploration
├─ src/
│  ├─ plotting.py       # fonctions de plotting
│  ├─ processing.py     # fonctions de traitement / interpolation
│  └─ main.py           # script orchestration CLI
├─ requirements.txt
├─ README.md
└─ .gitignore
```

# Contact
* Auteur : Mamadou DIAKHABY — Data Engineer
   * GitHub : `https://github.com/Diakhaby-data`
   * Email : diakhaby14@gmail.com
