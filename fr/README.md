# Scikit

**AUTEUR** : Julien VALENTIN

**DATE**   : Avril 2022 et en cours de rédaction

**LICENCE** : 

Ce dépôt synthétise ce que je sais des langages de programmation et des bonnes pratiques en ce qui concerne la programmation appliquée à la modélisation et à l'algorithmie. En particulier, on explore les langages de programmation `FreeFem`, `Julia`, `MATLAB` ou `Python3.x`. Ces langages sont tous des langages de haut niveau permettant de développer des méthodes d'analyse numérique, d'algèbre numérique, de mathématiques appliquées en général. On présente également quelques outils annexes tels que `Gmsh`, `Paraview`... Uniquement des outils libres articulés avec un ou plusieurs langages cités ci-dessus.

# L'environnement

## Environnement FreeFem++

On installe l'[interpréteur FreeFem++](https://freefem.org) dans une version compatible avec la parallélisation via MPI, PETSc, SLEPSc... Par exemple la 4.11. Le post-traitement des champs se fera à l'aide de [Paraview](https://www.paraview.org/).

## Environnement Julia

Après installation du [compilateur Julia](https://julialang.org/), on installera les librairies

- [Base.jl](https://docs.julialang.org/en/v1/base/base/)
- [Conda.jl](https://github.com/JuliaPy/Conda.jl)
- [LaTeXStrings.jl](https://docs.juliahub.com/LaTeXStrings/H4HGh/1.2.0/autodocs/)
- [LinearAlgebra.jl](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/)
- [Plots.jl](https://docs.juliaplots.org/stable/)
- [Tensors.jl](https://docs.juliahub.com/Tensors/F7rKl/1.4.3/).

## Environnement SageMath

On installe l'[interpréteur SageMath](https://sagemath.org).

# Index par langage

## FreeFem++

### Equations aux dérivées partielles (éléments finis)

- Probleme de [Poisson 2D](edp\poisson\FreeFem\00_poisson2d.edp) sur le disque unité
- Probleme de [Poisson 2D avec solveur](edp\poisson\FreeFem\01_poisson2d_solvers.edp) sur le disque unité
- Probleme de [Poisson 2D parallèle (PETSc)](edp\poisson\FreeFem\02_poisson2d_petsc.edp) sur le disque unité
- Probleme de [Poisson 2D avec conditions aux limites de Dirichlet / Neumann](edp\poisson\FreeFem\03_poisson2d_cl_mixtes.edp) sur le disque unité
- Impact de la résolution spatiale pour le probleme de [Poisson 2D de Dirichlet non-parallélisé](edp\poisson\FreeFem\04_poisson2d_resolution.edp) sur le disque unité
- Impact de la résolution spatiale pour le probleme de [Poisson 2D de Dirichlet parallélisé](edp\poisson\FreeFem\05_poisson2d_resolution.edp) sur le disque unité
- Probleme de [Poisson 2D](edp\poisson\FreeFem\06_poisson2d_optimisation.edp) dans sa forme de probleme d'optimisation
- Probleme de [Chaleur 2D avec intégration par Euler Implicite](edp\chaleur\FreeFem\00_chaleur2d.edp)
- Problème de [Transport](edp\transport\transport.edp) par un champ de vecteurs 2D constant d'une fonction scalaire
- Problème de [Transport](edp\transport\transport_maillage.edp) d'un maillage par un champ de vecteurs 2D constant.

### Langage

- [les fonctions et macro](langages/FreeFem/fespace.edp)
- [le type `fespace`](langages/FreeFem/fespace.edp)
- [le type `matrix`](langages/FreeFem/matrix.edp)
- [le type `mesh`](langages/FreeFem/mesh.edp)
- [le type `string`](langages/FreeFem/string.edp)
- [les structures de contrôle](langages/FreeFem/controle.edp)
- [les vecteurs](langages/FreeFem/array.edp)

## Julia

### Algèbre linéaire

- [calcul tensoriel](algebre_lineaire/Julia/tenseurs.ipynb)

### Langage

- [le type `Array`](langage/Julia/Array.ipynb)
- [les fonctions](langages/Julia/fonctions.ipynb)
- [les structures de contrôle](langages/Julia/controle.ipynb)

### visualisation de données

- [Plots.jl](visualisation/Julia/Plots.jl.ipynb)

## SageMath

### Algèbre linéaire

- [module libre de rang fini sur un anneau commutatif](algebre_lineaire/SageMath/module_libre_de_rang_fini_sur_anneau_commutatif.ipynb)

# Index par thème

## Algèbre linéaire

- [Julia : calcul tensoriel](algebre_lineaire/Julia/tenseurs.ipynb)
- [SageMath : modules libres de rang fini sur un anneau commutatif](algebre_lineaire/SageMath/module_libre_de_rang_fini_sur_anneau_commutatif.ipynb)

## Equations aux dérivées partielles (éléments finis)

- [FreeFem : Poisson 2D sur le disque unité](edp\poisson\FreeFem\00_poisson2d.edp)
- [FreeFem : Poisson 2D avec solveur sur le disque unité](edp\poisson\FreeFem\00_poisson2d_solvers.edp)
- [FreeFem : Poisson 2D parallèle (PETSc) sur le disque unité](edp\poisson\FreeFem\02_poisson2d_petsc.edp)
- [FreeFem : Poisson 2D avec conditions aux limites de Dirichlet / Neumann](edp\poisson\FreeFem\03_poisson2d_cl_mixtes.edp)
- [FreeFem : Poisson 2D, impact de la résolution sur le temps calcul (non-parallèle)](edp\poisson\FreeFem\04_poisson2d_resolution.edp)
- [FreeFem : Poisson 2D, impact de la résolution sur le temps calcul (parallèle)](edp\poisson\FreeFem\05_poisson2d_resolution.edp)
- [FreeFem : Chaleur 2D, intégration par Euler Implicite](edp\chaleur\FreeFem\00_chaleur2d.edp)
- [FreeFem : transport par un champ de vecteurs 2D d'une fonction scalaire](edp\transport\transport.edp)

## Visualisation de données

- [Julia : Plots.jl](visualisation/Julia/Plots.jl.ipynb)