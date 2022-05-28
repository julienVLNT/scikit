# Introduction <!-- omit in toc -->

Ce document est là pour porter un regard croisé sur la représentation de structures de données usuelles en mathématiques appliquées au travers de différents langages de programmation.

- [Les chaînes de caractères](#les-chaînes-de-caractères)
- [Les ensembles](#les-ensembles)
- [Les booléens](#les-booléens)
- [Les entiers naturels, $\mathbb{N}$](#les-entiers-naturels-mathbbn)
- [Les entiers relatifs, $\mathbb{Z}$](#les-entiers-relatifs-mathbbz)
- [Les décimaux, $\mathbb{D}$](#les-décimaux-mathbbd)
- [Les nombres rationnels, $\mathbb{Q}$](#les-nombres-rationnels-mathbbq)
- [Les nombres réels, $\mathbb{R}$](#les-nombres-réels-mathbbr)
- [Les nombres complexes, $\mathbb{C}$](#les-nombres-complexes-mathbbc)
- [Les constantes classiques](#les-constantes-classiques)
- [Les vecteurs](#les-vecteurs)
- [Les matrices denses](#les-matrices-denses)
- [Les matrices creuses](#les-matrices-creuses)
- [Les tenseurs](#les-tenseurs)
- [Les fonctions numériques](#les-fonctions-numériques)
- [Les fonctions numériques spéciales](#les-fonctions-numériques-spéciales)
  - [Exponentielle et logarithmes](#exponentielle-et-logarithmes)
  - [Trigonométrie](#trigonométrie)
  - [Trigonométrie hyperbolique](#trigonométrie-hyperbolique)
  - [Fonctions de Bessel de premier et de deuxième type](#fonctions-de-bessel-de-premier-et-de-deuxième-type)
  - [Fonction $\Gamma$ et variantes](#fonction-gamma-et-variantes)
  - [Fonction erreur](#fonction-erreur)
- [Les maillages en dimension $d$](#les-maillages-en-dimension-d)
    - [`FEniCs/Python3`](#fenicspython3)
    - [`FreeFem++`](#freefem)
    - [`Python3/Numpy`](#python3numpy)
    - [`Rheolef`](#rheolef)
- [Les espaces d'interpolation](#les-espaces-dinterpolation)
    - [`FEniCs/Python3`](#fenicspython3-1)
    - [`FreeFem++`](#freefem-1)
    - [`Rheolef`](#rheolef-1)
- [Les formulations variationnelles](#les-formulations-variationnelles)
  - [Implémentation des formes $a(\cdot, \cdot)$ et $l(\cdot)$](#implémentation-des-formes-acdot-cdot-et-lcdot)
    - [`FEniCs/Python3`](#fenicspython3-2)
    - [`FreeFem++`](#freefem-2)
    - [`Rheolef`](#rheolef-2)
  - [La question des conditions aux limites](#la-question-des-conditions-aux-limites)
- [Les structures algébriques abstraites](#les-structures-algébriques-abstraites)

# Les chaînes de caractères

# Les ensembles

# Les booléens

# Les entiers naturels, $\mathbb{N}$

# Les entiers relatifs, $\mathbb{Z}$

# Les décimaux, $\mathbb{D}$

# Les nombres rationnels, $\mathbb{Q}$

# Les nombres réels, $\mathbb{R}$

# Les nombres complexes, $\mathbb{C}$

# Les constantes classiques

# Les vecteurs

# Les matrices denses

# Les matrices creuses

# Les tenseurs

# Les fonctions numériques

# Les fonctions numériques spéciales

| **Fonction**                                      | **FreeFem++**          |
|:--------------------------------------------------|-----------------------:|
| $x \mapsto x^2$                                   | `square`               |
| $(x,y) \mapsto x^y$                               | `pow`                  |  
| $x \mapsto \sqrt{x}$                              | `sqrt`                 |
| $x \mapsto \|x\|$                                 | `abs`                  |

## Exponentielle et logarithmes

| **Fonction**                                      | **FreeFem++**          |
|---------------------------------------------------|-----------------------:|
| $e$                                               | `exp`                  |
| $\ln$                                             | `ln`                   |
| $\log : x \mapsto \frac{\ln(x)}{\ln(10)}$         | `log10`                |

## Trigonométrie

| **Fonction**                                      | **FreeFem++**          |
|---------------------------------------------------|-----------------------:|
| $\cos$                                            | `cos`                  |
| $\arccos$                                         | `acos`                 |
| $\sin$                                            | `sin`                  |
| $\arcsin$                                         | `asin`                 |
| $\tan$                                            | `tan`                  |
| $\arctan$                                         | `atan`                 |

## Trigonométrie hyperbolique

| **Fonction**                                      | **FreeFem++**          |
|---------------------------------------------------|-----------------------:|
| $\cosh$                                           | `cosh`                 |
| $\text{arccosh}$                                  | `acosh`                |
| $\sinh$                                           | `sinh`                 |
| $\text{arcsinh}$                                  | `asinh`                |
| $\tanh$                                           | `tanh`                 |
| $\text{arctanh}$                                  | `atanh`                |

## Fonctions de Bessel de premier et de deuxième type

| **Fonction**                                      | **FreeFem++**          |
|---------------------------------------------------|-----------------------:|
| type $1$ d'ordre $0$                              | `j0`                   |
| type $1$ d'ordre $1$                              | `j1`                   |
| type $1$ d'ordre $n$                              | `jn(n, x)`             |
| type $2$ d'ordre $0$                              | `y0`                   |
| type $2$ d'ordre $1$                              | `y1`                   |
| type $2$ d'ordre $n$                              | `yn(n, x)`             |

## Fonction $\Gamma$ et variantes

| **Fonction**                                      | **FreeFem++**          |
|---------------------------------------------------|-----------------------:|
| $\Gamma$                                          | `tgamma`               |
| $\ln(\|\Gamma\|)$                                 | `lgamma`               |

## Fonction erreur

| **Fonction**                                      | **FreeFem++**          |
|---------------------------------------------------|-----------------------:|
| Erreur $\text{erf}$                               | `erf`                  |
| $1-\text{erf}$                                    | `erfc`                 |

# Les maillages en dimension $d$

### `FEniCs/Python3`



### `FreeFem++`

### `Python3/Numpy`

La librairie `Numpy` de `Python3` permet de construire des maillages structurés en dimension $d$ quelconque. Une première manière d'obtenir ces maillages 

### `Rheolef`

# Les espaces d'interpolation

### `FEniCs/Python3`


### `FreeFem++`


### `Rheolef`


# Les formulations variationnelles

En général, une équation aux dérivées partielles peut s'étudier sous une forme variationnelle équivalente. Cette forme sera alors discrétisée à l'aide de la méthode de Galerkin et on aboutira à un système linéaire discret portant sur les degrés de libertés de l'interpolée de la solution dans un espace de dimension finie adapté.

Dans les langages spécialisés pour les éléments finis, il est possible de déclarer ces formes en tant que type (ou objet) et de les manipuler. Par exemple, considérons

$$ - \int_\Omega \Delta u \cdot v d\mathbf{x} = \int_\Omega f \cdot v d\mathbf{x} \Longleftrightarrow \underbrace{\int_\Omega \nabla u^T \nabla v d\mathbf{x}}_{a(u, v)} - \int_{\partial \Omega} \partial_{\vec{n}} u \cdot v d\gamma = \underbrace{\int_{\Omega} f \cdot v d\mathbf{x}}_{l(v)} $$

## Implémentation des formes $a(\cdot, \cdot)$ et $l(\cdot)$

### `FEniCs/Python3`

```python
from ufl import dx, grad, inner

a = inner(grad(u), grad(v)) * dx
l = inner(f, v) * dx
```

L'intégrale sur le domaine est implicite, bien que marquée par le produit par `dx` - pour une intégrale surfacique, on utilise `ds`, c.f la section suivante ; on n'implémente que l'intégrande.

### `FreeFem++`

La déclaration d'une forme variationnelle par le mot-clef `varf` n'impose pas de déclarer au préalable les champs éléments finis notés comme arguments. A ce stade, ils ne sont que des symboles abstraits.

```cpp
varf a(u, v) = int2d(th)( dx(u)*dx(v) + dy(u)*dy(v) );
varf l(unused, v) = int2d(th)( f*v );
```

Contrairement à l'écriture dans `FEniCs/Python`, on spécifie explicitement que l'intégrale se prend sur le maillage `th` représentant $\Omega$.

### `Rheolef`

```cpp
form a = integrate( dot( grad_h(u), grad_h(v) ) );
field l = integrate( f(d)*v );
```

Contrairement aux deux langages précédents, les deux formes ne partagent pas le même type (au sens large). Ici, le second membre est de type `field`, réservé pour les champs - ou fonctions - éléments finis.

## La question des conditions aux limites



# Les structures algébriques abstraites