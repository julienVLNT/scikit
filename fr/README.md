# A propos

**AUTEUR** : Julien VALENTIN

**DATE**   : Avril 2022 et en cours de rédaction

**LICENCE** : 

Ce dépôt synthétise ce que je sais des langages de programmation et des bonnes pratiques en ce qui concerne la programmation appliquée à la modélisation et à l'algorithmie. En particulier, on explore les langages de programmation `FreeFem`, `Julia`, `MATLAB` ou `Python 3`. Ces langages sont tous des langages de haut niveau permettant de développer des méthodes d'analyse numérique, d'algèbre numérique, de mathématiques appliquées en général. On présente également quelques outils annexes tels que `Gmsh`, `Paraview`... Uniquement des outils libres articulés avec un ou plusieurs langages cités ci-dessus.

Ici se trouve mon [C.V](a_propos/CV_2022-05-22_Julien_Valentin.pdf).

# La bibliographie ...

... se trouve [ici](https://github.com/julienVLNT/scikit/tree/main/bibliographie).

# L'environnement

## L'O.S

Je travaille sur [Windows 11](https://www.microsoft.com/fr-fr/windows?wa=wsignin1.0) avec [Windows Subsysteme Linux v2](https://docs.microsoft.com/fr-fr/windows/wsl/).

## L'I.D.E

Pour développer, j'utilise [Visual Studio Code](https://code.visualstudio.com/) et [Visual Studio](https://visualstudio.microsoft.com/fr/). 

J'utilise les extensions :

- [C/C++](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
- [docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)
- [docs-markdown](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-markdown)
- [french language pack](https://marketplace.visualstudio.com/items?itemName=MS-CEINTL.vscode-language-pack-fr)
- [jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)
- [jupyter notebook renderers](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter-renderers)
- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
- [pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
- [python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [remote-containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
- [vscode-FreeFem](https://marketplace.visualstudio.com/items?itemName=Pierre-Marchand.vscode-freefem)

## L'environnement C / C++

On utilise les outils natifs de l'I.D.E [Visual Studio](). Pour les compilations de DLL à destination de [Nastran](https://www.mscsoftware.com/fr/product/msc-nastran), le logiciel certifie l'usage du compilateur [Intel oneAPI DPC++/C++ Compiler](https://www.intel.com/content/www/us/en/developer/tools/oneapi/dpc-compiler.html#gs.0tnw5g), lequel s'intègre naturellement à Visual Studio. On ajoutera la bibliothèque [PETSc](https://petsc.org/release/).

## L'environnement FEniCs

L'environnement [FEniCs](https://fenicsproject.org/) dispose de plusieurs types d'installation. J'ai choisi l'intégration dans un conteneur [Docker](https://www.docker.com/), cette distribution intègre nativement l'environnement nécessaire à l'usage de FEniCs, son A.P.I Python3 ainsi que l'environnement de développement interactif [Jupyter](https://jupyter.org/), avec l'interface utilisateur Jupyterlab.

## Environnement FreeFem++

On installe l'[interpréteur FreeFem++](https://freefem.org) dans une version compatible avec la parallélisation via [MPI](https://www.open-mpi.org/), [PETSc](https://petsc.org/release/), [SLEPc](https://slepc.upv.es/)... Par exemple la 4.11. Le post-traitement des champs se fera à l'aide de [Paraview](https://www.paraview.org/).

## Environnement Julia

Après installation du [compilateur Julia](https://julialang.org/), on installera les librairies

- [Base.jl](https://docs.julialang.org/en/v1/base/base/)
- [Conda.jl](https://github.com/JuliaPy/Conda.jl)
- [LaTeXStrings.jl](https://docs.juliahub.com/LaTeXStrings/H4HGh/1.2.0/autodocs/)
- [LinearAlgebra.jl](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/)
- [Plots.jl](https://docs.juliaplots.org/stable/)
- [Tensors.jl](https://docs.juliahub.com/Tensors/F7rKl/1.4.3/).

## Environnement Python

On installe le gestionnaire d'environnements et de paquets [Conda](https://docs.conda.io/en/latest/index.html), plus précisément la distribution [Miniconda](https://docs.conda.io/en/latest/miniconda.html), installation minimale autonome. Elle contient un interpréteur [Python](https://www.python.org/).

On pourra installer à l'aide de `conda` les packages

- [bokeh](http://docs.bokeh.org/en/latest/#)
- [fipy](https://www.ctcms.nist.gov/fipy/)
- [jupyterlab](https://jupyterlab.readthedocs.io/en/stable/)
- [matplotlib](https://matplotlib.org/)
- [mpi4py](https://mpi4py.readthedocs.io/en/stable/)
- [numpy](https://numpy.org/)
- [pandas](https://pandas.pydata.org/)
- [petsc4py](https://www.mcs.anl.gov/petsc/petsc4py-current/docs/)
- [plotly](https://plotly.com/)
- [pypde](https://pypde.readthedocs.io/en/latest/)
- [pytorch](https://pytorch.org/)
- [tensorflow](https://www.tensorflow.org/)
- [scikit-learn](https://scikit-learn.org/stable/#)
- [scipy](https://scipy.org/)
- [sympy](https://www.sympy.org/en/index.html)
- [xarray](https://docs.xarray.dev/en/stable/)

Pour l'analyse numérique des équations de conservation, on pourra installer le gestionnaire de paquets [pip](https://pypi.org/project/pip/) et l'utiliser pour obtenir [clawpack](http://www.clawpack.org/).

## Environnement SageMath

On installe l'[interpréteur SageMath](https://sagemath.org).

# Index par langage

## C++ 

### Implémentation et compilation d'une D.L.L

- Une [D.L.L](https://github.com/julienVLNT/scikit/tree/main/fr/compilation/DLL-C++/README.md) qui calcule les termes de Fibonacci (et son client)

## FreeFem++

### Algèbre linéaire

- [Transformations du plan](https://github.com/julienVLNT/scikit/tree/main/fr/algebre/FreeFem/transformations_planes.edp)

### Equations aux dérivées partielles (éléments finis)

- Probleme de [Poisson 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/00_poisson2d.edp) sur le disque unité
- Probleme de [Poisson 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/01_poisson2d_solvers.edp) avec comparaison de quelques solveurs sur le disque unité
- Probleme de [Poisson 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/02_poisson2d_petsc.edp) parallèle (PETSc) sur le disque unité
- Probleme de [Poisson 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/03_poisson2d_cl_mixtes.edp) avec conditions aux limites de Dirichlet / Neumann sur le disque unité
- Impact de la résolution spatiale pour le probleme de [Poisson 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/04_poisson2d_resolution.edp) de Dirichlet non-parallélisé sur le disque unité
- Impact de la résolution spatiale pour le probleme de [Poisson 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/05_poisson2d_resolution.edp) de Dirichlet parallélisé sur le disque unité
- Résolution du problème de [Poisson 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/06_poisson2d_problem.edp) par la définition d'un `problem` et la résolution par l'appel.
- Résolution du problème de [Poisson 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/07_poisson2d_matrice.edp) par la définition du système linéaire associé à un objet `varf`
- Problème de [Chaleur 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/chaleur/FreeFem/00_chaleur2d.edp) avec intégration par Euler Implicite
- Problème de [Chaleur 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/chaleur/FreeFem/01_chaleur2d_petsc.edp) distribué à l'aide de PETSc
- Problème de [Transport](https://github.com/julienVLNT/scikit/tree/main/fredp/transport/transport.edp) par un champ de vecteurs 2D constant d'une fonction scalaire
- Problème de [Transport](https://github.com/julienVLNT/scikit/tree/main/fr/edp/transport/transport_maillage.edp) d'un maillage par un champ de vecteurs 2D constant.
- Problème de [Stokes 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/00_stokes_poiseuille.edp) pour l'écoulement de Poiseuille (conditions mixtes pression / vitesse) dans un canal, implémentation par couplage fort avec éléments **P1**, **P1b**.
- Problème de [Stokes 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/01_stokes_entrainement.edp) pour l'écoulement *lid-driven* en cavité fermée (conditions de vitesse), couplage fort avec éléments **P1**, **P1b**
- Problème de [Stokes 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/02_stokes_cylindre.edp) pour l'écoulement autour d'un obstacle cylindrique (conditions en vitesses / pressions à l'extérieur et vitesse sur le cylindre), couplage fort avec éléments **P1**, **P1b**.
- Problème de [Stokes 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/03_stokes_streamlines.edp) avec recherche de la fonction de flot pour en déduire le vortex $\text{rot}(\psi)$
- Problème de [Stokes 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/04_stokes_uzawa.edp) avec itérations d'Uzawa, conditions en vitesse
- Problème de [Stokes 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/05_stokes_uzawa.edp) avec itérations d'Uzawa, conditions mixtes vitesse / pression.
- Problème de [Navier-Stokes 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/00_navierStokes_taylorGreen.edp) présentation de la solution de Taylor-Green
- Problème de [Navier-Stokes 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/01_navierStokes_chorin.edp) résolution du problème d'évolution pour Navier-Stokes avec conditions aux limites en vitesse par algorithme de projection - correction de Chorin
- Problème de [Navier-Stokes 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/02_navierStokes_chorin.edp) résolution d'un problème de Poiseuille à l'aide du code précédent ; pour l'instant ma solution diverge.
- Problème de [Navier-Stokes 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/03_navierStokesStationnaire_newton.edp) résolution du problème stationnaire pour l'écoulement de Taylor-Green, approximation du problème d'Oseen à l'aide d'une méthode de Newton
- Problème de [Navier-Stokes 2D](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/04_navierStokesStationnaire_uzawaCahouetChabart.edp) : résolution du problème stationnaire par application de l'itération d'Uzawa et conditionnement par Cahouet-Chabart.
- Problème de [Navier-Stokes](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/05_navierStokes_BFD2.edp) : schéma d'ordre 2 en temps pour le problème de Navier-Stokes, solution de Taylor-Green.

### Langage

- [les fonctions et macro](https://github.com/julienVLNT/scikit/tree/main/fr/langages/FreeFem/fespace.edp)
- [le type `fespace`](https://github.com/julienVLNT/scikit/tree/main/fr/langages/FreeFem/fespace.edp)
- [le type `matrix`](https://github.com/julienVLNT/scikit/tree/main/fr/langages/FreeFem/matrix.edp)
- [le type `mesh`](https://github.com/julienVLNT/scikit/tree/main/fr/langages/FreeFem/mesh.edp)
- [le type `string`](https://github.com/julienVLNT/scikit/tree/main/fr/langages/FreeFem/string.edp)
- [les structures de contrôle](https://github.com/julienVLNT/scikit/tree/main/fr/langages/FreeFem/controle.edp)
- [les vecteurs](https://github.com/julienVLNT/scikit/tree/main/fr/langages/FreeFem/array.edp)

### Physiques

- Problème de [Darcy](https://github.com/julienVLNT/scikit/blob/main/fr/physiques/darcy/FreeFem/00_darcy.edp) pour l'écoulement de Poiseuille en milieu poreux dans un matériau homogène isotrope
- Problème de [Darcy](https://github.com/julienVLNT/scikit/blob/main/fr/physiques/darcy/FreeFem/01_darcy_nhani.edp) pour un écoulement en cavité, fluide non-homogène, milieu non-homogène anisotrope
- Problème de [Darcy](https://github.com/julienVLNT/scikit/blob/main/fr/physiques/darcy/FreeFem/02_darcy_evolution.edp) pour l'imprégnation d'un poreux initialement plein d'air qui se remplit de fluide
- Problème de [Darcy](https://github.com/julienVLNT/scikit/blob/main/fr/physiques/darcy/FreeFem/03_darcy_nhani_fort.edp) pour un fluide non-homogène s'écoulant dans un milieu non-homogène anisotrope, implémentation par couplage fort
- Problème d'[élasticité](https://github.com/julienVLNT/scikit/blob/main/fr/physiques/elasticite/FreeFem/00_lame_nhani.edp) pour la déformation d'une pièce non-homogène anisotrope

## Julia

### Algèbre linéaire

- [calcul tensoriel](https://github.com/julienVLNT/scikit/tree/main/fr/algebre/Julia/tenseurs.ipynb)

### Langage

- [le type `Array`](https://github.com/julienVLNT/scikit/tree/main/fr/langage/Julia/Array.ipynb)
- [les fonctions](https://github.com/julienVLNT/scikit/tree/main/fr/langages/Julia/fonctions.ipynb)
- [les structures de contrôle](https://github.com/julienVLNT/scikit/tree/main/fr/langages/Julia/controle.ipynb)

### visualisation de données

- [Plots.jl](https://github.com/julienVLNT/scikit/tree/main/fr/visualisation/Julia/Plots.jl.ipynb)

## SageMath

### Algèbre linéaire

- [module libre de rang fini sur un anneau commutatif](https://github.com/julienVLNT/scikit/tree/main/fr/algebre_lineaire/SageMath/module_libre_de_rang_fini_sur_anneau_commutatif.ipynb)

# Index par thème

## Algèbre

- [FreeFem : transformations du plan](https://github.com/julienVLNT/scikit/tree/main/fr/algebre/FreeFem/transformations_planes.edp)
- [Julia : calcul tensoriel](https://github.com/julienVLNT/scikit/tree/main/fr/algebre/Julia/tenseurs.ipynb)
- [SageMath : modules libres de rang fini sur un anneau commutatif](https://github.com/julienVLNT/scikit/tree/main/fr/algebre/SageMath/module_libre_de_rang_fini_sur_anneau_commutatif.ipynb)

## Equations aux dérivées partielles (éléments finis)

- [FreeFem : Poisson 2D sur le disque unité](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/00_poisson2d.edp)
- [FreeFem : Poisson 2D avec solveur sur le disque unité](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/00_poisson2d_solvers.edp)
- [FreeFem : Poisson 2D parallèle (PETSc) sur le disque unité](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/02_poisson2d_petsc.edp)
- [FreeFem : Poisson 2D avec conditions aux limites de Dirichlet / Neumann](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/03_poisson2d_cl_mixtes.edp)
- [FreeFem : Poisson 2D, impact de la résolution sur le temps calcul (non-parallèle)](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/04_poisson2d_resolution.edp)
- [FreeFem : Poisson 2D, impact de la résolution sur le temps calcul (parallèle)](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/05_poisson2d_resolution.edp)
- [FreeFem : Poisson 2D, impact de l'implémentation `problem` et résolution par appel du problème](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/06_poisson2d_problem.edp)
- [FreeFem : Poisson 2D, construction du système linéaire et résolution du système linéaire](https://github.com/julienVLNT/scikit/tree/main/fr/edp/poisson/FreeFem/07_poisson2d_matrice.edp)
- [FreeFem : Chaleur 2D, intégration par Euler Implicite](https://github.com/julienVLNT/scikit/tree/main/fr/edp/chaleur/FreeFem/00_chaleur2d.edp)
- [FreeFem : Chaleur 2D, intégration par Euler Implicite, parallélisation avec PETSc](https://github.com/julienVLNT/scikit/tree/main/fr/edp/chaleur/FreeFem/01_chaleur2d_petsc.edp)
- [FreeFem : transport par un champ de vecteurs 2D d'une fonction scalaire](https://github.com/julienVLNT/scikit/tree/main/fr/edp/transport/transport.edp)
- [FreeFem : transport par un champ de vecteurs 2D d'un maillage](https://github.com/julienVLNT/scikit/tree/main/fr/edp/transport/transport_maillage.edp)
- [FreeFem : Stokes - Poiseuille](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/00_stokes_poiseuille.edp) par couplage fort, éléments **P1**, **P1b**
- [FreeFem : Stokes - *lid-driven*](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/01_stokes_entrainement.edp) par couplage fort, éléments **P1**, **P1b**
- [FreeFem : Stokes - cylindre](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/02_stokes_cylindre.edp) par couplage fort, éléments **P1**, **P1b**
- [FreeFem : Stokes ](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/03_stokes_streamlines.edp) recherche de la fonction de flot
- [FreeFem : Stokes](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/04_stokes_uzawa.edp) itérations d'Uzawa avec conditions aux limites sur la vitesse
- [FreeFem : Stokes](https://github.com/julienVLNT/scikit/tree/main/fr/edp/stokes/FreeFem/05_stokes_uzawa.edp) itérations d'Uzawa avec conditions aux limites mixtes vitesse / pression
- [FreeFem : Navier-Stokes](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/00_navierStokes_taylorGreen.edp) présentation de la solution de Taylor-Green
- [FreeFem : Navier-Stokes](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/01_navierStokes_chorin.edp) résolution du problème d'évolution pour Navier-Stokes avec conditions aux limites en vitesse par algorithme de projection - correction de Chorin.
- 
- [FreeFem : Navier-Stokes](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/02_navierStokes_chorin.edp) résolution d'un problème de Poiseuille à l'aide du code précédent ; pour l'instant ma solution diverge.
- [FreeFem : Navier-Stokes](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/03_navierStokesStationnaire_newton.edp) : résolution du problème d'Oseen pour l'écoulement de Taylor-Green avec méthode de Newton.
- [FreeFem : Navier-Stokes](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/04_navierStokesStationnaire_uzawaCahouetChabart.edp) : résolution d'un problème stationnaire par itérations d'Uzawa avec préconditionnement de Cahouet-Chabart.
- [FreeFem : Navier-Stokes](https://github.com/julienVLNT/scikit/tree/main/fr/edp/navier-stokes/FreeFem/05_navierStokes_BFD2.edp) : schéma d'ordre 2 en temps pour le problème de Navier-Stokes, solution de Taylor-Green.

## Implémentation et compilation d'une D.L.L

- [C++ : DLL Fibonacci](https://github.com/julienVLNT/scikit/tree/main/fr/compilation/DLL-C++/README.md) et son client

## Physiques

### Darcy

- [FreeFem : problème de Darcy](https://github.com/julienVLNT/scikit/blob/main/fr/physiques/darcy/FreeFem/00_darcy.edp) pour l'écoulement de Poiseuille en cavité, milieu homogène et isotrope
- [FreeFem : problème de Darcy](https://github.com/julienVLNT/scikit/blob/main/fr/physiques/darcy/FreeFem/01_darcy_nhani.edp) pour un écoulement en cavité, fluide non-homogène, milieu non-homogène anisotrope
- [FreeFem : problème de Darcy](https://github.com/julienVLNT/scikit/blob/main/fr/physiques/darcy/FreeFem/02_darcy_evolution.edp) pour l'imprégnation d'un poreux initialement plein d'air qui se remplit de fluide
- [FreeFem : problème de Darcy](https://github.com/julienVLNT/scikit/blob/main/fr/physiques/darcy/FreeFem/03_darcy_nhani_fort.edp) pour un fluide non-homogène dans un milieu non-homogène anisotrope, implémentation par couplage fort

### Elasticité

- [FreeFem : problème de Lamé](https://github.com/julienVLNT/scikit/blob/main/fr/physiques/lame/FreeFem/00_lame_nhani.edp) statique pour la déformation d'une pièce non-homogène et anisotrope


## Visualisation de données

- [Julia : Plots.jl](https://github.com/julienVLNT/scikit/tree/main/fr/visualisation/Julia/Plots.jl.ipynb)