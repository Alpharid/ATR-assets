# Passation — ATR-assets

Pour la personne, ou l'IA, qui reprend ce dépôt. `README.md` décrit le contenu ; ce fichier dit comment il est
fabriqué et à quoi il sert.

## 1. Ce que c'est

Le rangement, en un seul endroit, de **toutes les images** du JDR « Arx Tenebris Relectis » (univers d'Arx Fatalis),
pour deux usages :

1. servir les images de la **fiche de personnage** Roll20 (dossier `fiche/`), à la place du dépôt public de
   Chafik où elles côtoient les données secrètes de la fiche ;
2. avoir les cartes, objets, personnages et textures sous la main pour les héberger ailleurs que sur Roll20.

Ce dépôt ne contient **aucun code**. Il est le produit de deux autres projets de Farid (`Alpharid`) :

| Projet | Dépôt | Ce qu'il fournit ici |
|---|---|---|
| cartes et assets | `Alpharid/arx-jdr-maps` (privé) | `objets/`, `personnages/`, `cartes/`, `textures/` — rendus à partir des fichiers du jeu |
| fiche de personnage | `Alpharid/Projet_JDR-ATR` (privé), d'après `C-Chafik/arx-jdr-sheet` | `fiche/` — copie exacte de son dossier `assets/` |
| dossier du MJ | `Tenebris Relectis ASSETS\` sur le PC de Farid | `illustrations/` (CD bonus), `cartes/dungeon-scrawl/` |

## 2. État au 02/10/2026

- Première version : 5 489 fichiers, 948 Mo, 11 dossiers. Tout a été vérifié à la construction : aucun fichier
  au-dessus de 100 Mo, toutes les images d'objets, de personnages et de zones ont un fond transparent sauf trois
  icônes pleines par nature.
- **Dépôt privé.** Farid l'avait demandé public ; prévenu que ces images appartiennent à Arkane Studios et qu'un
  dépôt public peut faire l'objet d'une demande de retrait, il a décidé le 02/10/2026 de le **laisser privé** et de
  reprendre le sujet plus tard. Ne pas changer la visibilité sans qu'il le redemande.
- Tant qu'il est privé, la fiche continue de lire ses images chez Chafik. Une fois public :
  dans `Projet_JDR-ATR`, construire avec
  `ARX_ASSET_BASE=https://raw.githubusercontent.com/Alpharid/ATR-assets/main/fiche python build.py`, puis recoller
  `sheet.css` dans Roll20.

Reste à faire : la publication, le jour où Farid la redemande (poser alors une étiquette `v1`) ; ajouter les 79 icônes
d'inventaire manquantes quand elles seront rendues (objets que le jeu affiche avec un « ? »).

## 3. Reconstruire

Rien ne se modifie à la main ici. Tout vient d'un script du projet des cartes :

```
cd "C:\JDR - Arx Tenebris Relectis"
.venv\Scripts\python.exe scripts\build_assets_repo.py        # reconstruit ATR-assets\ et INDEX.csv
```

Il efface et recopie les dossiers `fiche`, `objets`, `personnages`, `cartes`, `textures`, `illustrations` ; il ne
touche ni à `.git` ni aux fichiers `.md`. Il affiche un contrôle : images détourées qui seraient opaques, fichiers
trop lourds pour GitHub. Ensuite : `git add -A`, commit, push.

Pour changer une image, changer sa **source** (le rendu dans le projet des cartes, ou `assets/` dans la fiche),
puis relancer le script.

## 4. Organisation

```
fiche/            même arborescence que assets/ de la fiche : book/ ui/ items/ runes/ spells/ presets/
objets/
  inventaire/     <catégorie>/<Nom français (LxH)>.png  + inventaire.csv
  decor/          <catégorie>/<Nom français (LxH)>.png  + decor.csv
  modeles/        fix_inter/ items/ npc/ system/ <nom_du_jeu>.png  + index.csv
personnages/      <catégorie>/<Nom> - repos|combat|KO|portrait.png  + tokens.csv
cartes/
  fonds/          NiveauN.png (70 px par case) + NiveauN.json
  zones/          LevelN_toit_K.png + LevelN_toits.csv (position en cases)
  apercus/        LevelN_apercu.png
  dungeon-scrawl/ les .ds du MJ
textures/         obj3d/ interface/ + index.csv
illustrations/    croquis/ croquis-scribbles/ peintures/ fonds-d-ecran/
INDEX.csv         une ligne par fichier : chemin ; octets ; largeur ; hauteur ; fond_transparent ; chemin_url
```

Les numéros de zones (`toit_K`) sont ceux que le MJ cite : ne pas les renuméroter.

## 5. Pièges

- **GitHub refuse un fichier de plus de 100 Mo** et prévient au-dessus de 50 Mo : les 8 fonds de carte font 48 à
  86 Mo. Si un niveau grossit, le script le signale.
- Pousser près de 1 Go d'un coup échoue facilement : pousser dossier par dossier (un commit par dossier, un push par
  commit).
- Les noms de fichiers contiennent des accents, des espaces et des parenthèses : dans une adresse, utiliser la
  colonne `chemin_url`.
- Ne jamais y mettre les fichiers du jeu lui-même (`.pak`, exécutables, ISO, vidéos) ni les données de la fiche
  (`presets.json` et ses recettes de sorts secrets).
- `raw.githubusercontent.com` garde les fichiers en cache quelques minutes ; pour la fiche Roll20, c'est le numéro
  `ASSET_VERSION` de `build.py` qui force le rechargement.

## 6. Historique

| Date | Quoi |
|---|---|
| 02/10/2026 | création : script `build_assets_repo.py`, première version complète ; Farid choisit de garder le dépôt privé pour l'instant |
