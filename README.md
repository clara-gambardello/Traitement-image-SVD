# Traitement d'image par décomposition en valeurs singulières (SVD)

Projet d'analyse des données - Compression et reconstruction d'image en niveaux de gris grâce à la décomposition en valeurs singulières (SVD).

## Le projet

Une image peut être vue comme une matrice `A` (n lignes × m colonnes), où chaque coefficient représente l'intensité d'un pixel en niveau de gris (0 = noir, 255 = blanc). L'objectif est de reconstruire une image visuellement très proche de l'originale, mais représentée par une matrice de dimensions bien inférieures, en ne conservant qu'une partie des valeurs singulières de la SVD.

### Étapes

1. **Import de l'image couleur** avec le package `png` (`readPNG`) et affichage avec `grid`
2. **Conversion en niveaux de gris** par combinaison linéaire pondérée des composantes rouge, vert et bleu (pondérations 0.2126 / 0.7152 / 0.0722, issues de la norme de luminance perçue)
3. **Calcul de la SVD** de la matrice image avec la fonction `svd()` de R, donnant `A = U Σ V^T`
4. **Reconstruction progressive** de l'image en ne gardant que les *k* premières valeurs singulières (les plus grandes), pour différentes valeurs de *k* (3, 20, 50, 100, 200...), via une boucle affichant chaque résultat
5. **Correction des valeurs de pixels** hors de l'intervalle [0, 1] (dues aux arrondis numériques) avec `pmin`/`pmax`, la fonction `grid.raster` n'acceptant que des valeurs dans cet intervalle

## Résultat

Après plusieurs essais, une reconstruction visuellement satisfaisante est obtenue en ne conservant que **195 valeurs singulières sur les 3024 initiales**, ce qui représente l'image originale avec une matrice de dimensions largement réduites tout en conservant les détails visibles à l'œil nu.

## Structure du projet

* `Projet_Gambardello.Rmd` : script R Markdown avec l'ensemble du code et des explications
* `Projet_Gambardello.pdf` : rapport compilé (résultats et images générées)
* `Projet_Sujet.pdf` : énoncé du projet

## Lancer l'analyse

1. Cloner le projet ou télécharger les fichiers
2. Installer les packages nécessaires

```r
install.packages(c("png", "grid"))
```

3. Placer une image `Image.png` dans le même dossier que le script
4. Ouvrir `Projet_Gambardello.Rmd` dans RStudio et compiler (Knit)

## Auteur

Clara GAMBARDELLO
Master 1 Modélisation Statistique - Projet Analyse des données (2024)
