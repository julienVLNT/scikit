# Introduction <!-- omit in toc -->

Ce document est là pour porter un regard croisé sur la représentation de structures de données usuelles en mathématiques appliquées au travers de différents langages de programmation.

- [Les booléens](#les-booléens)
  - [Egalité de booléens](#egalité-de-booléens)
  - [Remarques](#remarques)
    - [Opération logique != opération bit-à-bit](#opération-logique--opération-bit-à-bit)
    - [`C`](#c)
    - [`FreeFem++`](#freefem)
    - [`Python3`](#python3)
    - [`SageMath`](#sagemath)
- [Les entiers relatifs, $\mathbb{Z}$](#les-entiers-relatifs-mathbbz)
  - [Types ou objets représentant les entiers](#types-ou-objets-représentant-les-entiers)
    - [`FreeFem++`](#freefem-1)
  - [Relations d'ordre sur les entiers](#relations-dordre-sur-les-entiers)
  - [Opérateurs sur les entiers](#opérateurs-sur-les-entiers)
- [Les nombres décimaux, $\mathbb{D}$](#les-nombres-décimaux-mathbbd)
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
  - [`FreeFem++`](#freefem-2)
- [Les espaces d'interpolation](#les-espaces-dinterpolation)
- [Les formulations variationnelles](#les-formulations-variationnelles)
  - [Implémentation des formes $a(\cdot, \cdot)$ et $l(\cdot)$](#implémentation-des-formes-acdot-cdot-et-lcdot)
    - [`FEniCs/Python3`](#fenicspython3)
    - [`FreeFem++`](#freefem-3)
    - [`Rheolef`](#rheolef)
  - [Les conditions aux limites de Dirichlet et de Neumann](#les-conditions-aux-limites-de-dirichlet-et-de-neumann)
    - [`FEniCs/Python3`](#fenicspython3-1)
    - [`FreeFem++`](#freefem-4)
  - [Conditions aux limites de Dirichlet faible](#conditions-aux-limites-de-dirichlet-faible)
  - [Conditions aux limites de Robin](#conditions-aux-limites-de-robin)
  - [Remarques](#remarques-1)
    - [`FreeFem++` : `problem` et `solve`](#freefem--problem-et-solve)
- [Les structures algébriques abstraites](#les-structures-algébriques-abstraites)

# Les booléens

| **Booléen**   | **Symbole**    | `C++`        | `FreeFem++`   | `Julia`      | `Python3`   |
|:--------------|:---------------|-------------:|--------------:|-------------:|------------:|
| type ou objet | X              | `bool`       | `bool`        | `Bool`       | `bool`      |
| vrai          | 1              | `true`       | `true`        | `true`       | `True`      |
| faux          | 0              | `false`      | `false`       | `false`      | `False`     |
| non           | $\neg b$       | `!b`         | `!b`          | `!b`         | `not(b)`    |
| et            | $b1 \wedge b2$ | `b1 && b2`   | `b1 && b2`    | `b1 && b2`   | `b1 and b2` |
| ou            | $b1 \vee b2$   | `b1 \|\| b2` | `b1 \|\| b2`  | `b1 \|\| b2` | `b1 or b2`  |

## Egalité de booléens

Dans tous les langages cités ci-dessus, l'opérateur binaire `==` teste l'égalité entre deux booléens.

## Remarques

### Opération logique != opération bit-à-bit

Il faut différencier les opérations sur les booléens vus comme types des opérations logiques effectuées sur chaque bit de la représentation binaire d'un objet ou d'un type.

### `C`

Le type booléen n'est pas intrinsèquement implémenté dans le langage `C`, on peut les manipuler en tant que type grâce à la librairie `stdbool` ou définir un type *à la main* basé sur les entiers non-signés par exemple. Sinon on les manipule selon l'association `vrai` ~ `1`, `faux` ~ `0`.

### `FreeFem++`

Il est courant de trouver dans les codes la représentation entière du type booléen, avec `true` ~ `1` et `false` ~ `0`.

### `Python3`

Il y a énormément de manières de définir le **faux** : les objets `None` et `False`, certes, mais aussi le `0` de tous les types numériques ou les collections vides : `''`, `()`, `[]`, `set()`, `range(0)` ...

### `SageMath`

Les objets `bool` de `SageMath` correspondent exactement au modèle introduit par `Python3`.

# Les entiers relatifs, $\mathbb{Z}$

## Types ou objets représentant les entiers



### `FreeFem++`

Le type utilisé par `FreeFem++` pour représenter les entiers est équivalent au type `long` en `C++`. Pour déclarer un entier, on utilise 

```cpp
int m;
```

auquel cas il est initialisé à $0$. On peut aussi lui affecter une valeur à la déclaration

```cpp
int m = 1;
```

## Relations d'ordre sur les entiers

Les opérateurs représentant les relations d'ordre renvoient un booléen. 

| **Test logique**   | **Symbole** | `C++`    | `FreeFem++` | `Julia`  | `Python3` | `SageMath` |
|:-------------------|:------------|---------:|------------:|---------:|----------:|-----------:|
| Test d'égalité     | $=$         | `m == n` | `m == n`    | `m == n` | `m == n`  | `m == n`   |
| Test de différence | $\neq$      | `m != n` | `m != n`    | `m != n` | `m != n`  | `m != n`   |
| Inférieur ou égal  | $\leq$      | `m <= n` | `m <= n`    | `m <= n` | `m <= n`  | `m <= n`   |
| Inférieur strict   | $<$         | `m < n`  | `m < n`     | `m < n`  | `m < n`   | `m < n`    |
| Supérieur ou égal  | $\geq$      | `m >= n` | `m >= n`    | `m >= n` | `m >= n`  | `m >= n`   |
| Supérieur strict   | $>$         | `m > n`  | `m > n`     | `m > n`  | `m > n`   | `m > n`    |

## Opérateurs sur les entiers

On ne cite ici que les opérations internes de $\mathbb{Z}$ i.e dont les résultats sont des entiers.

| **Opérateur**    | **Symbole** | `C++` | `FreeFem++` | `Julia`  | `Python3` | `SageMath`    |
|:-----------------|:------------|------:|------------:|---------:|----------:|--------------:|
| identité         | $+$         | `+m`  | `+m`        | `+m`     | `+m`      | `+m`          |
| opposé           | $-$         | `-m`  | `-m`        | `-m`     | `-m`      | `-m`          |
| successeur       | X           | `m++` | `m++`       | X        | X         | X             |
| successeur (2)   | X           | `++m` | `++m`       | X        | X         | X             |
| prédecesseur     | X           | `m--` | `m--`       | X        | X         | X             |
| prédecesseur (2) | X           | `--m` | `--m`       | X        | X         | X             |

Les opérateurs successeur et prédecesseur sont des affectations : lorsqu'on invoque `m++`, l'entier `m` est évalué puis on lui affecte la valeur `m+1`. Dans `++m`, `m` reçoit la valeur `m+1` puis est évalué.

| **Opérateur**    | **Symbole** | `C++` | `FreeFem++` | `Julia`  | `Python3` | `SageMath`    |
|:-----------------|:------------|------:|------------:|---------:|----------:|--------------:|
| addition         | $+$         | `m+n` | `m+n`       | `m+n`    | `m+n`     | `m+n`         |
| soustraction     | $-$         | `m-n` | `m-n`       | `m-n`    | `m-n`     | `m-n`         |
| multiplication   | $\times$    | `m*n` | `m*n`       | `m*n`    | `m*n`     | `m*n`         |
| division         | $\div$      | ?     | `m/n`       | `m ÷ n`  | `m//n`    | `m//n`        |
| modulo           | $\equiv$    | ?     | `m % n`     | `m % n`  | `m % n`   | `m % n`       |
| exponentiation   | X           | ?     | `m^n`       | `m^n`    | `m**n`    | `m^n`, `m**n` |

Il est parfois possible d'affecter au premier opérande le résultat de l'opération. 

| **Opérateur**    | **Symbole** | `C++`     | `FreeFem++` | `Julia`  | `Python3` | `SageMath`    |
|:-----------------|:------------|----------:|------------:|---------:|----------:|--------------:|
| addition         | X           | `m += n ` | `m += n`    | `m += n` | `m += n`  | `m+n`         |
| soustraction     | X           | `m -= n`  | `m -= n`    | `m -= n` | `m -= n`  | `m-n`         |
| multiplication   | X           | `m *= n`  | `m *= n`    | `m *= n` | `m *= n`  | `m*n`         |
| division         | X           | ?         | `m /= n`    | X        | `m //= n` | `m//n`        |
| modulo           | X           | ?         | X           | `m %= n` | `m %= n`  | `m % n`       |
| exponentiation   | X           | ?         | X           | `m ^= n` | `m **= n` | `m^n`, `m**n` |

En `FreeFem++`, les affectations des résultats de `m %= n` et `m ^= n` donnent des erreurs à la compilation. En `Julia`, l'affectation du résultat pour la division donne systématiquement des nombres réels. C'est pourquoi on note un X dans la case correspondante.

# Les nombres décimaux, $\mathbb{D}$

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

## Exponentielle et logarithmes

| **Fonction**                                      | **FreeFem++**          |
|---------------------------------------------------|-----------------------:|
| $e$                                               | `exp`                  |
| $\ln$                                             | `ln`                   |
| $\log$                                            | `log10`                |

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
| $\text{erf}$                                      | `erf`                  |
| $1-\text{erf}$                                    | `erfc`                 |

# Les maillages en dimension $d$

## `FreeFem++`

`FreeFem++` intègre des fonctions permettant de construire des maillages déstructurés. On notera le maillage $\mathcal{T}_h$ associé à un domaine $\Omega$ par l'identificateur `th`. Le type `mesh` permet de représenter $\mathcal{T}_h$.

# Les espaces d'interpolation

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

Contrairement aux deux langages `FEniCs` ou `FreeFem++`, les deux formes ne partagent pas le même type (au sens large). Ici, le second membre est de type `field`, réservé pour les champs - ou fonctions - éléments finis.

## Les conditions aux limites de Dirichlet et de Neumann

Supposons que $\partial \Omega = \Gamma_D \cup \Gamma_N$, union disjointe. On impose une condition de Dirichlet $u \equiv g$ sur $\Gamma_D$ et une condition de Neumann $\partial_{\vec{n}}u \equiv h$ sur $\Gamma_N$.

### `FEniCs/Python3`

La condition de Dirichlet sur `u` s'écrit

```python
from dolfinx.fem import dirichletbc, Function, locate_dofs_geometrical
from numpy import isclose, logical_or

def boundary_D(x):
    "Détection du bord Dirichlet"
    return logical_or(np.isclose(x[0], 0), np.isclose(x[0],1))

gh = Function(V)
gh.interpolate(g)

bcd = dirichletbc(gh, locate_dofs_geometrical(V, boundary_D))
```

Ici, `g` est une fonction numérique implémentée en `Python` et `V` est un objet `dolfinx.fem.FunctionSpace`, un espace d'interpolation par éléments finis. On note qu'on construit "à la main" une fonction qui décrit la proximité entre un point et le bord : un point appartient au bord à une précision près, celle de `numpy.isclose()`. Une condition de type Neumann s'écrit

```python
from ufl import SpatialCoordinate

x = SpatialCoordinate(mesh)

def h(x):
    "Expression de la fonction h"
    return h(x)

bcn = h * v * ds
```

La fonction numérique `h` utilise la variable `x` construite à l'aide de `SpatialCoordinate` et `FEniCs` construit alors la mesure surfacique `ds`. Etant donné que $v$ est nulle sur $\partial \Omega_D$, intégrer sur $\partial \Omega$ en entier n'a pas de conséquence.

### `FreeFem++`

La condition de Dirichlet sur `u` s'écrit

```cpp
varf dirichlet(u, unused) = on(D, u=g);
```

où $D$ est un entier, le label associé au bord de Dirichlet. La condition de Neumann s'écrit

```cpp
varf neumann(unused, v) = int1d(th, N)( h*v );
```

et $N$ est encore un entier, le label du bord portant la condition de Neumann.

## Conditions aux limites de Dirichlet faible

## Conditions aux limites de Robin

## Remarques

### `FreeFem++` : `problem` et `solve`

> Lorsqu'on ne souhaite pas travailler explicitement sur le système linéaire construit à partir de $a(\cdot, \cdot)$ et de $l(\cdot)$, on peut utiliser le mot-clef `problem` comme dans
> ```cpp
> problem Poisson(u, v) = int2d(th)( dx(u)*dx(v) + dy(u)*dy(v) ) - int1d(th, N)( h*v ) - int2d(th)( f*v ) + on(D, u=g);
> ```
> L'instruction `Poisson;` calcule la solution du problème variationnel et modifie `u` de sorte que ses degrés de libertés soient la solution du système linéaire associé à `Poisson`. Ce système dépend de la base d'interpolation choisie, il est donc nécessaire que `u` soit déclarée comme fonction élément fini avant la déclaration du problème. On note également qu'on est obligé de renseigner les conditions aux limites. C'est utile lorsqu'on appelle plusieurs fois la résolution du problème, comme dans un problème d'évolution.
> ```cpp
> solve Poisson(u, v) = int2d(th)( dx(u)*dx(v) + dy(u)*dy(v) ) - int1d(th, N)( h*v ) - int2d(th)( f*v ) + on(D, u=g);
> ```
> L'instruction `solve Poisson(u, v) = ` résoud dès sa déclaration le problème en modifiant les degrés de liberté de `u`. Comme pour `problem`, `u` doit être déclarée comme fonction élément fini avant la déclaration du problème. Ces trois méthodes sont dans l'ordre décroissant de leur performance.

# Les structures algébriques abstraites