# ATR-assets — les images du JDR « Arx Tenebris Relectis »

Toutes les images de la campagne de JDR sur table dans l'univers d'**Arx Fatalis** : objets, décor, personnages,
cartes, textures, illustrations, et les images de la fiche de personnage Roll20. Uniquement des images et leurs
tables : aucun code, aucune règle, aucun fichier du jeu lui-même.

5 489 fichiers, 948 Mo. La liste complète, avec dimensions et transparence, est dans [`INDEX.csv`](INDEX.csv)
(séparateur `;`, s'ouvre dans Excel).

## Ce qu'il y a

| Dossier | Contenu | Images | Fond | Échelle |
|---|---|---|---|---|
| [`objets/inventaire/`](objets/inventaire) | les icônes d'inventaire du jeu, rangées par catégorie, noms français, taille en cases dans le nom : `Épée longue (1x3).png` | 289 | transparent¹ | 64 px par case |
| [`objets/decor/`](objets/decor) | éléments de décor vus de dessus (coffres, portes, cadavres, mécanismes, objets au sol…), 20 catégories, noms français | 646 | transparent | 200 px par case |
| [`objets/modeles/`](objets/modeles) | **tous** les modèles du jeu vus de dessus, sous leur nom d'origine (`fix_inter`, `items`, `npc`, `system`) | 802 | transparent | 200 px par case |
| [`personnages/`](personnages) | créatures et personnages : `repos`, `combat`, `KO`, `portrait` ; `Variantes créées/` = gardes, PNJ, rats-garous, Mère des Glaces | 429 | transparent | — |
| [`cartes/fonds/`](cartes/fonds) | les 8 niveaux, image complète prête pour une table virtuelle, avec sa fiche `.json` (taille en cases, nombre de murs, portes, lumières) | 8 | plein | 70 px par case |
| [`cartes/zones/`](cartes/zones) | les étages, toits, corniches et ponts qui passent **au-dessus** de la carte, à poser par-dessus ; position dans `LevelN_toits.csv` | 81 | transparent | 72 px par case |
| [`cartes/apercus/`](cartes/apercus) | une vue d'ensemble légère de chaque niveau | 8 | plein | — |
| [`cartes/dungeon-scrawl/`](cartes/dungeon-scrawl) | les cartes du MJ au format Dungeon Scrawl (`.ds`) | — | — | — |
| [`textures/`](textures) | les textures du jeu, telles quelles : `obj3d/` (murs, sols, objets, créatures), `interface/` (livre, curseurs, icônes) | 2 727 | plein² | — |
| [`illustrations/`](illustrations) | croquis, peintures et fonds d'écran du CD bonus | 73 | plein | — |
| [`fiche/`](fiche) | les images de la fiche de personnage Roll20 (livre, interface, objets, runes, sorts) | 397 | selon l'image | — |

¹ Trois icônes sont pleines par nature (elles ont leur propre cadre) : *Saucisse amicale* et les deux *Titres de
propriété*. Toutes les autres images d'objets, de personnages et de zones ont un fond transparent, vérifié fichier
par fichier (colonne `fond_transparent` d'`INDEX.csv`).

² Dans les textures du jeu, le noir pur tient lieu de transparence : c'est la convention du moteur, elles sont
livrées sans y toucher.

Chaque dossier d'objets et de personnages contient sa table (`inventaire.csv`, `decor.csv`, `index.csv`,
`tokens.csv`) : nom français, nom du modèle dans le jeu, catégorie, taille.

## Qualité

Rien n'a été recompressé ni redimensionné : ce sont les fichiers produits par la chaîne de fabrication du projet
`arx-jdr-maps`, copiés tels quels. Deux conversions, sans perte : les fonds de carte sont sortis des fichiers
`.dd2vtt`, et les images `.bmp` du CD bonus sont enregistrées en PNG. Les JPEG du CD bonus sont gardés en JPEG
(les réencoder ne ferait que les abîmer).

## Utiliser une image ailleurs

Chaque fichier a une adresse directe. La colonne `chemin_url` d'`INDEX.csv` donne le chemin déjà encodé (accents,
espaces, parenthèses) :

```
https://raw.githubusercontent.com/Alpharid/ATR-assets/main/<chemin_url>
```

Pour qu'une adresse ne change plus jamais, remplacer `main` par une étiquette (`v1`, `v2`…) : une étiquette pointe
toujours sur la même version des fichiers. Ces adresses ne répondent que si le dépôt est **public**.

La fiche de personnage lit ses images dans `fiche/` : voir `HANDOVER.md`.

## Origine et droits

Arx Fatalis est une œuvre d'**Arkane Studios** (© Arkane Studios / ZeniMax Media). Les images de ce dépôt sont
extraites des données du jeu ou rendues à partir d'elles, pour une campagne de JDR entre amis, sans but commercial.
Aucun droit n'est revendiqué sur elles. À la demande d'un ayant droit, le dépôt sera retiré.

Les variantes de `personnages/Variantes créées/` et quelques objets recolorés sont des recombinaisons de pièces du
jeu, faites pour la campagne ; aucune image n'a été générée par une IA.
