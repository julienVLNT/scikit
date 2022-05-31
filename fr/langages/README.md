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
    - [`C++`](#c-1)
    - [`FreeFem++`](#freefem-1)
  - [Relations d'ordre sur les entiers](#relations-dordre-sur-les-entiers)
  - [Opérateurs sur les entiers](#opérateurs-sur-les-entiers)
  - [Remarques](#remarques-1)
    - [`FreeFem++`](#freefem-2)
    - [`Julia`](#julia)
    - [`Python3`](#python3-1)
- [Les nombres décimaux, $\mathbb{D}$](#les-nombres-décimaux-mathbbd)
- [Les nombres rationnels, $\mathbb{Q}$](#les-nombres-rationnels-mathbbq)
- [Les nombres réels, $\mathbb{R}$](#les-nombres-réels-mathbbr)
- [Les nombres complexes, $\mathbb{C}$](#les-nombres-complexes-mathbbc)
- [Les constantes](#les-constantes)
- [Les vecteurs](#les-vecteurs)
  - [`FreeFem++`](#freefem-3)
  - [`Julia`](#julia-1)
  - [`Python3/Numpy`](#python3numpy)
- [Les matrices](#les-matrices)
    - [`FreeFem++`](#freefem-4)
    - [`Julia`](#julia-2)
    - [`Python3/Numpy`](#python3numpy-1)
- [Les tenseurs](#les-tenseurs)
  - [`Julia/Tensors.jl`](#juliatensorsjl)
  - [`Python3/Numpy`](#python3numpy-2)
  - [`Tensorflow/Python3`](#tensorflowpython3)
- [Algèbre creuse](#algèbre-creuse)
  - [`FreeFem++`](#freefem-5)
  - [`Julia`](#julia-3)
  - [`Python3/Scipy`](#python3scipy)
- [Les fonctions (et macro ou lambda expressions...)](#les-fonctions-et-macro-ou-lambda-expressions)
  - [`FreeFem++`](#freefem-6)
  - [`Julia`](#julia-4)
  - [`Python3`](#python3-2)
- [Les fonctions numériques spéciales](#les-fonctions-numériques-spéciales)
  - [Exponentielle et logarithmes](#exponentielle-et-logarithmes)
  - [Trigonométrie](#trigonométrie)
  - [Trigonométrie hyperbolique](#trigonométrie-hyperbolique)
  - [Fonctions de Bessel](#fonctions-de-bessel)
  - [Fonction $\Gamma$ et variantes](#fonction-gamma-et-variantes)
  - [Fonctions erreur et variantes](#fonctions-erreur-et-variantes)
- [Les maillages](#les-maillages)
  - [`FreeFem++`](#freefem-7)
    - [Un rectangle en deux dimensions](#un-rectangle-en-deux-dimensions)
    - [Maillage d'une surface fermée par un contour paramétré](#maillage-dune-surface-fermée-par-un-contour-paramétré)
    - [Mailler un domaine privé d'un sous-domaine](#mailler-un-domaine-privé-dun-sous-domaine)
    - [Un rectangle en trois dimensions](#un-rectangle-en-trois-dimensions)
    - [Remarque](#remarque)
- [Les espaces d'interpolation](#les-espaces-dinterpolation)
  - [`FreeFem++`](#freefem-8)
- [Les formulations variationnelles](#les-formulations-variationnelles)
  - [Implémentation des formes $a(\cdot, \cdot)$ et $l(\cdot)$](#implémentation-des-formes-acdot-cdot-et-lcdot)
    - [`FEniCs/Python3`](#fenicspython3)
    - [`FreeFem++`](#freefem-9)
    - [`Rheolef`](#rheolef)
  - [implémentation de $F(u, v) = 0$](#implémentation-de-fu-v--0)
    - [`FEniCs/Python3`](#fenicspython3-1)
    - [`FreeFem++`](#freefem-10)
  - [Les conditions aux limites de Dirichlet et de Neumann](#les-conditions-aux-limites-de-dirichlet-et-de-neumann)
    - [`FEniCs/Python3`](#fenicspython3-2)
    - [`FreeFem++`](#freefem-11)
  - [Conditions aux limites de Dirichlet faible](#conditions-aux-limites-de-dirichlet-faible)
  - [Conditions aux limites de Robin](#conditions-aux-limites-de-robin)
  - [Remarques](#remarques-2)
    - [`FreeFem++` : `problem` et `solve`](#freefem--problem-et-solve)
- [Les structures algébriques abstraites avec `SageMath`](#les-structures-algébriques-abstraites-avec-sagemath)

# Les booléens

| **Booléen**   | **Symbole**    | `C++`      | `FreeFem++` | `Julia`    | `Python3` |
|:--------------|:---------------|-----------:|------------:|-----------:|----------:|
| type ou objet | X              | `bool`     | `bool`      | `Bool`     | `bool`    |
| vrai          | 1              | `true`     | `true`      | `true`     | `True`    |
| faux          | 0              | `false`    | `false`     | `false`    | `False`   |
| non           | $\neg$         | `!a`       | `!a`        | `!a`       | `not(a)`  |
| et            | $\wedge$       | `a && b`   | `a && b`    | `a && b`   | `a and b` |
| ou            | $\vee$         | `a \|\| b` | `a \|\| b`  | `a \|\| b` | `a or b`  |

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

### `C++`

Les nombres entiers relatifs, entiers *signés*, se déclarent sous un des types suivants

| **Type**               | **représentés sur $n$ bits** | **minimum**                      | **maximum**                 |
|:-----------------------|-----------------------------:|---------------------------------:|----------------------------:|
| `signed char`          | $n = 8$                      | $-128$                           | $127$                       |
| `signed short int`     | $n = 16$                     | $-32,768$                        | $32,767$                    |
| `signed long int`      | $n = 32$                     | $-2,147,483,647 - 1$             | $2,147,483,647$             |
| `signed long long int` | $n = 64$                     | $-9,223,372,036,854,775,807 - 1$ | $9,223,372,036,854,775,807$ |

Le type `int` par défaut dépend de la machine sur lequel se situe le compilateur. Les limites de chaques types sont des constantes de la librairie standard `limits`. Elles se nomment `CHAR_MIN`, `CHAR_MAX`, `SHRT_MIN`, `SHRT_MAX`, `INT_MIN`, `INT_MAX`, `LONG_MIN`, `LONG_MAX`, `LLONG_MIN`, `LLONG_MAX`. 

Pour déclarer un entier en `C++`,

```cpp
int a;
int b(1);     // "constructor initialization"
int c{2};     // "uniform initialization"
int d=3;
```

### `FreeFem++`

Le type utilisé par `FreeFem++` pour représenter les entiers est équivalent au type `long` en `C++`. Pour déclarer un entier, on utilise 

```cpp
int m;
```

auquel cas il se voit affecté la valeur $0$. 

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

| **Opérateur**    | **Symbole** | `C++`     | `FreeFem++` | `Julia`  | `Python3` | `SageMath`      |
|:-----------------|:------------|----------:|------------:|---------:|----------:|----------------:|
| addition         | X           | `m += n ` | `m += n`    | `m += n` | `m += n`  | `m += n`        |
| soustraction     | X           | `m -= n`  | `m -= n`    | `m -= n` | `m -= n`  | `m -= n`        |
| multiplication   | X           | `m *= n`  | `m *= n`    | `m *= n` | `m *= n`  | `m *= n`        |
| division         | X           | ?         | `m /= n`    | X        | `m //= n` | `m //= n`       |
| modulo           | X           | ?         | X           | `m %= n` | `m %= n`  | `m %= n`        |
| exponentiation   | X           | ?         | X           | `m ^= n` | `m **= n` | `m^=n`, `m**=n` |

## Remarques

### `FreeFem++`

En `FreeFem++`, les affectations des résultats de `m % n` et `m ^ n` sous leur forme `m %= n` et `m ^ n` donnent des erreurs à la compilation. 

### `Julia`

En `Julia`, l'affectation du résultat pour la division donne systématiquement des nombres réels. C'est pourquoi on note un X dans la case correspondante.

### `Python3`

Le couple quotient et reste pour la division euclidienne s'obtient à l'aide de la fonction `divmod(m, n)`. L'élévation de `m` à la puissance `n` s'obtient à l'aide de `pow(m, n)`.

# Les nombres décimaux, $\mathbb{D}$

# Les nombres rationnels, $\mathbb{Q}$

# Les nombres réels, $\mathbb{R}$

# Les nombres complexes, $\mathbb{C}$

# Les constantes

| **Constante mathématique** | **Symbole** | `FreeFem++` | `Julia`   | `Python3/Scipy` | `SageMath`     |
|:---------------------------|:------------|------------:|----------:|----------------:|---------------:|
| Zéro                       | $0$         | `0`         | `0`       | `0`             | `0`            |
| Un                         | $1$         | `1`         | `1`       | `1`             | `1`            |
| Imaginaire pur             | $i$         | `1i`        | `1im`     | `1j`            |                |
| Pi                         | $\pi$       | `pi`        | `π`       | X               | `pi`           |
| e                          | $e$         | X           | `ℯ`       | X               | `e`            |
| logarithme de 2            | $\ln(2)$    | X           | X         | X               | `log2`         |
| nombre d'or                | $\varphi$   | X           | `φ`       | X               | `golden_ratio` |
| constante d'Euler          |             | X           | `γ`       | X               | `euler_gamma`  |
| constante de Catalan       |             | X           | `catalan` | X               | `catalan`      |
| constante de Khinchin      |             | X           | X         | X               | `khinchin`     |

| **Constante physique** | **Symbole** |
|:-----------------------|:------------|
|                        |             |

# Les vecteurs

Dans cette section, on s'intéresse aux vecteurs construits sur le corps des nombres réels. L'extension aux $\mathbb{C}$-espaces vectoriels est plutôt aisée.

## `FreeFem++`

On note ici les principaux attributs, les principales méthodes associées à la représentation des vecteurs. On rappelle également la syntaxe des opérations usuelles. La fiche est écrite pour les vecteurs construits sur $\mathbb{R]$, on peut aisément construire des vecteurs de nombres complexes à l'aide de `complex[int]`.

```cpp
// Déclaration et affectation
real[int] v(d);                    // déclare un vecteur de taille d et affecte à ses composantes la valeur 0
real[int] v = 1.0;                 // déclare un vecteur de taille 1, et affecte à son unique composante la valeur 1

real[int] v(d);                    // déclare un vecteur de taille d et affecte à toutes ses composantes la valeur -1 
v = -1;

real[int] v = [1.0, -1.0, 3.0];    // déclare un vecteur de taille 3 et affecte à ses composantes les valeurs 1, -1 et 3
real[int] v(m : n);                // déclare un vecteur de taille (n-m) et affecte à ses composantes les valeurs m, m+1, m+2, ..., m+n
real[int] v = m : n;               // déclare un vecteur de taille (n-m) et affecte à ses composantes les valeurs m, m+1, m+2, ..., m+n
real[int] v(m : k : n);            // déclare un vecteur de taille (n/k-m) et affecte à ses composantes les valeurs m, m+k, m+2k, ..., m+n/k*k

// Sélection dans les vecteurs
v(m)                               // sélection de la valeur en m
v[m]                               // sélection de la valeur en m
v(m : m+n)                         // sélection des n valeurs entre les indices m et m+n inclus
v[m : m+n]                         // sélection des n valeurs entre les indices m et m+n inclus
v(m : m+n : l)                     // sélection des int(n/l) valeurs entre les indices m et m+n inclus, par pas de l (m, m+l, m+2l ...)
v[m : m+n : l]                     // sélection des int(n/l) valeurs entre les indices m et m+n inclus, par pas de l (m, m+l, m+2l ...)

// Sélection par quantile
v.quantile(r)                      // sélectionne la composante v[r * v.n], 0 < r < 1

// Taille d'un vecteur
v.n

// Valeurs particulières et leur indice
v.imax                             // indice de la composante maximale de v
v.max                              // valeur maximale de v
v.imin                             // indice de la composante minimale de v
v.min                              // valeur minimale de v
v.sum                              // somme des valeurs des composantes de v

// Algèbre
u + v                              // addition de deux vecteurs
u - v                              // différence de deux vecteurs

r * v                              // multiplication par un scalaire [real r];

u' * v                             // produit scalaire de deux vecteurs

u * v'                             // multiplication extérieur (ou tensoriel) de deux vecteurs

u .* v                             // multiplication terme à terme

// Normes
v.l1                               // norme 1
v.l2                               // norme 2 (euclidienne)
v.linfty                           // norme max

// Trier les valeurs d'un vecteur
v.sort
```

Les vecteurs peuvent également être indexés par des objets de type `string`. 

## `Julia`

```julia

```

## `Python3/Numpy`

En `Python3`, les vecteurs sont implémentés par l'objet `numpy.ndarray` de la librairie `Numpy`. En fait, cet objet est un conteneur très général, un vecteur a en particulier un nombre de dimension égal à $1$.

```Python
import numpy as np

# Déclaration et affectation
v = np.array([x, y, z])            # déclare un vecteur de taille 3 et ses composantes sont affectées à x, y et z (des réels)
v = np.empty(d)                    # déclare un vecteur de taille d dont les composantes sont aléatoires
v = np.zeros(d)                    # déclare un vecteur de taille d dont les composantes valent 0
v = np.ones(d)                     # déclare un vecteur de taille d dont les composantes valent 1
v = np.empty_like(u)               # déclare un vecteur de même taille que v dont les composantes sont aléatoires
v = np.zeros_like(u)               # déclare un vecteur de même taille que v dont les composantes reçoivent 0
v = np.ones_like(u)                # déclare un vecteur de même taille que v dont les composantes reçoivent 1

# Attributs
len(v)                             # nombre de composantes
v.dtype                            # type de donné utilisé pour stocker les composantes de v
v.nbytes                           # nombre d'octets nécessaires au stockage de v, dépend du dtype
v.ndims                            # nombre d'axes du ndarray, toujours 1 pour un vecteur, ou nombre d'indices
v.shape                            # tuple des nombres de composantes par axe (tuple d'un entier pour un vecteur)

# Sélection dans les vecteurs
v[m]                               # sélection de la m-ème composante (m commence à 0)
v[m : m+n]                         # sélection des n composantes entre les indices m (inclus) et m+n (exclu)
v[m : m+n : l]                     # sélection des n/l composantes entre les indices m (inclus) et m+n (exclu) par pas de l

# Valeurs particulières et leur indice
np.abs(v)                          # vecteur dont les composantes sont les valeurs absolues des composantes de v
np.argmax(v)                       # indice de la valeur maximale de v
np.max(v)                          # valeur maximale de v
np.argmin(v)                       # indice de la plus petite composante de v
np.min(v)                          # valeur minimale de v
np.argwhere(v<0)                   # vecteur des indices pour lesquels v_i < 0
np.where(v<0)                      # vecteur colonne des indices tels que v[i] < 0
np.sum(v)                          # somme des composantes de v
np.prod(v)                         # produit des composantes de v
np.mean(v)                         # moyenne arithmétique des composantes de v
np.std(v)                          # standard-deviation des composantes de v

# Algèbre
+v                                 # identité
-v                                 # inverse

u + v                              # addition
u - v                              # différence

r * v                              # multiplication par un scalaire

u @ v                              # produit scalaire
u.T @ v                            # produit scalaire
u @ v.T                            # produit scalaire
u.dot(v)                           # produit scalaire
np.dot(u, v)                       # produit scalaire
np.einsum('i, i -> ', u, v)        # produit scalaire
np.inner(u, v)                     # produit scalaire
np.tensordot(u, v, axes=1)         # produit scalaire

np.einseum('i, j -> ij', u, v)     # produit extérieur
np.outer(u, v)                     # produit extérieur
np.tensordot(u, v, axis=0)         # produit extérieur

u * v                              # multiplication terme à terme
np.einsum('i, i -> i', u, v)       # multiplication terme à terme
u / v                              # division terme à terme

np.kron(u, v)                      # produit de Kronecker de u et v

# Normes
np.linalg.norm(v, 1)               # norme "1"
np.linalg.norm(v)                  # norme "2" (euclidienne)
np.linalg.norm(v, np.inf)          # norme infinie
np.linalg.norm(v, r)               # norme r

# Tests booléens
u is v                             # test d'identité 
np.all(u > 0)                      # True si u_i > 0 pour tout i
np.allclose(u, v, atol, rtol)      # True si |u_i - v_i| < atol pour tout i
np.any(u > 0)                      # True si u_i > 0 pour au moins un i

u == v                             # vecteur booléen dont la composante i est True si |u_i - v_i| < 1e-16 (pour float64)
u <= v                             # vecteur booléen dont la composante i est True si u_i <= v_i
u <  v                             # vecteur booléen dont la composante i est True si u_i < v_i
u >= v                             # vecteur booléen dont la composante i est True si u_i >= v_i
u >  v                             # vecteur booléen dont la composante i est True si u_i > v_i
np.isclose(u, v, rtol, atol)       # vecteur booléen dont les composantes sont True si |u_i - v_i| < atol False sinon

# Concaténations
w = np.concatenate([u, v], axis=0) # concaténation en ligne
w = np.concatenate((u, v), axis=0) # concaténation en ligne
w = np.hstack([u, v])              # concaténation en ligne
w = np.hstack((u, v))              # concaténation en ligne
w = np.concatenate([u, v], axis=1) # concaténation en colonne
w = np.concatenate((u, v), axis=1) # concaténation en colonne
w = np.vstack([u, v])              # concaténation en colonne
w = np.vstack((u, v))              # concaténation en colonne
```

# Les matrices

### `FreeFem++`

Les matrices denses ne sont pas implémentées dans ce langage. Les objets `real[int, int]` sont des vecteurs de vecteurs mais les opérations standards ne sont pas implémentées pour ces objets. On regardera l'objet `matrix` dans la section sur les [matrices creuses](#algèbre-creuse).

```cpp

```

### `Julia`

```julia

```

### `Python3/Numpy`

Les matrices denses sont encore implémentées à l'aide de l'objet `numpy.ndarray`, on les identifie aux instances telles que l'attribut `ndims` est égale à $2$.

```python
import numpy as np

# Déclaration et affectation
A = np.array([[a11, a12], [a21, a22]])# déclare une matrice de taille 2x2 et ses composantes sont affectées à a11, a12, a21, a22 (des réels)
A = np.empty((m,n))                # déclare une matrice de taille m x n dont les composantes sont aléatoires
A = np.zeros((m,n))                # déclare une matrice de taille m x n dont les composantes valent 0
A = np.ones((m,n))                 # déclare une matrice de taille m x n dont les composantes valent 1
A = np.empty_like(B)               # déclare une matrice de même taille que B dont les composantes sont aléatoires
A = np.zeros_like(B)               # déclare une matrice de même taille que B dont les composantes reçoivent 0
A = np.ones_like(B)                # déclare une matrice de même taille que B dont les composantes reçoivent 1

# Attributs
len(A)                             # nombre de lignes dans A (m)
len(A[0])                          # nombre de colonnes dans A (n)
A.dtype                            # type de donné utilisé pour stocker les composantes de v
A.nbytes                           # nombre d'octets nécessaires au stockage de v, dépend du dtype
A.ndims                            # nombre d'axes du ndarray, toujours 2 pour une matrice, ou nombre d'indices
A.shape                            # tuple des nombres de composantes par axe (tuple de deux entiers pour une matrice)

# Sélection
A[m, n]                            # sélection de la m-ème composante (m commence à 0)
A[m, :]                            # sélection de la m-ième ligne
A[:, n]                            # sélection de la n-ième colonne
A[m : m+n, j]                      # sélection des n composantes entre les indices m (inclus) et m+n (exclu)
A[m : m+n : l, j]                  # sélection des n/l composantes sur la colonne j
A[i, m : m+n : l]                  # sélection des n/l composantes sur la ligne j

# Algèbre
+A                                 # identité
-A                                 # opposée

A + B                              # addition
A - B                              # soustraction

r * A                              # multiplication par un scalaire r

np.einsum('ij, ij ->', A, B)       # produit scalaire
np.tensordot(A, B)                 # produit scalaire
np.tensordot(A, B, axes=2)         # produit scalaire

A @ v                              # action d'une matrice sur un vecteur
A.dot(v)                           # action d'une matrice sur un vecteur
np.dot(A, v)                       # action d'une matrice sur un vecteur
np.einsum('ij, j -> i', A, v)      # action d'une matrice sur un vecteur
np.tensordot(A, v, axes=1)         # action d'une matrice sur un vecteur

A @ B                              # produit matriciel
A.dot(B)                           # produit matriciel
np.dot(A, B)                       # produit matriciel
np.einsum('ij, jk -> ik', A, B)    # produit matriciel
np.matmul(A, B)                    # produit matriciel
np.tensordot(A, B, axes=1)         # produit matriciel
np.linalg.multi_dot([A, B, C])     # composition de produits matriciels ( (A @ B) @ C)

A @ B.T                            # produit intérieur
np.inner(A, B)                     # produit intérieur

np.kron(A, B)                      # produit extérieur
np.outer(A, B)                     # produit extérieur

np.einsum('ij, kl -> ijkl', A, B)  # produit tensoriel
np.tensordot(A, B, axes=0)         # produit tensoriel
```

# Les tenseurs

## `Julia/Tensors.jl`

```julia

```

## `Python3/Numpy`

```python

```

## `Tensorflow/Python3`

```python

```

# Algèbre creuse

## `FreeFem++`

```cpp

```

## `Julia`

```julia

```

## `Python3/Scipy`

```python

```

# Les fonctions (et macro ou lambda expressions...)

## `FreeFem++`

Le langage `FreeFem++` contient les identificateurs globaux `x`, `y` et `z` pour désigner les variables d'espace. On peut aussi paramétrer une fonction par la méthode standard en `C++`.

```cpp
// Fonction des variables d'espace à valeurs réelles
func f = sqrt(x^2 + y^2 + z^2);

// Fonction des variables d'espace à valeurs réelles paramétrée par t
func real f(real t){
    return t * (1 - sqrt(x^2 + y^2 + z^2));
}

// Fonction des variables d'espace à valeurs vectorielles (réelles)
func real[int] f() {
    real[int] v(d);
    return v;
}

// Fonction des variables d'espaces à valeurs matricielles
func matrix f(){
    matrix A(m, n);
    return A;
}
```

## `Julia`

```julia
# Déclaration, affectation
(x -> 0)                           # déclaration de la fonction anonyme x |--> 0
f(t,x,y) = t*(1-sqrt(x^2+y^2))     # déclaration de la fonction f sur une ligne

@doc """
Calcule le carré du nombre réel ``x``.
"""
function f(x::Float64)::Float64
     return x^2
end

function g(args...)
    for arg in args
        println(arg)
    end
end

function h(x, y, op=+)
    op(x, y)
end

function i(x, y; op)
    if op == nothing
        x + y
    else
        op(x, y)
    end
end

# Evaluation
(t,x,y -> t * (1-sqrt(x^2+y^2)))(0)# évaluation d'une fonction anonyme de plusieurs variables
f(-1)                              # évaluation de la fonction f
```

Le langage est fortement typé : bien que la fonction carrée est définie sur $\mathbb{C}$, la définition de `f` impose que l'argument soit du type `Float64`, donc l'évaluation `f(1i)` lève une erreur. Dans la définition de `g`, on autorise un nombre variable d'arguments. `g(0)` ou `g('a', 1, -2i)` sont valides. Dans la définition de `h`, l'argument `op` est optionnel. Dans la définition de `i`, l'argument `op` est un mot-clef (on fait attention au point-virgule plutôt que la virgule).

## `Python3`

On commence par les `<function <lambda>` du langage `Python3`. Elles se déclarent en une ligne, très adaptées aux expressions très simples ou pour l'usage à la volée, sans déclaration, par exemple en paramètre d'une autre fonction.

```python
# Déclaration
lambda x : 0                       # déclaration de la fonction anonyme x |--> 0
f = lambda x, y : x + y            # fonction de plusieurs variables à valeurs scalaires
f = lambda x, y : {x, y, (x+y)**2} # fonction de plusieurs variables à valeurs multiples (set)
f = lambda x, y : (x, y, (x+y)**2) # fonction de plusieurs variables à valeurs multiples (tuple)
f = lambda x, y : [x, y, (x+y)**2] # fonction de plusieurs variables à valeurs multiples (liste)
f = lambda x : 0 if x < 0 else x   # fonction définie par une condition ("rectified linear" ici)

# Evaluation
f(-1)
```

La seconde manière de définir des fonctions est l'utilisation de la fonction `def`. La fonction carré s'écrit simplement

```python
def carre(x):
    return x**2
```

En pratique, on lui préférera la définition *complète* suivante

```python
def carre(x: float) -> float:
    
    """ Calcul le carré du nombre x.
    PARAMETRES:
    -----------
    x : float, valeur de l'argument

    RETOURS:
    --------
    x**2 : float 

    EXEMPLES:
    ---------
    >>> carre(-1)
    1 """

    return x**2
```

On note que x: float n'est qu'une indication, de même que -> float. Le programme s'exécute malgré la violation de ces "règles", qui n'en sont donc pas ; par exemple, carre(1j) renvoie -1, ce qui est mathématiquement juste, mais du point de vue de la documentation ne va pas. La seule contrainte est que l'opérateur ** soit défini pour l'argument prescrit. Ainsi déclarée, appeler la fonction help(carre) renvoie la chaîne de caractère proposée ainsi que le squelette de la fonction.

# Les fonctions numériques spéciales

## Exponentielle et logarithmes

| **Fonction**                                      | `FreeFem++` | `Julia` | `Python/Numpy` |
|---------------------------------------------------|------------:|--------:|---------------:|
| $e$                                               | `exp`       |  | `numpy.exp`    |
| $\ln$                                             | `ln`        | | `numpy.log`    |
| $\ln_2$                                           | X           | | `numpy.log2`   |
| $\log$                                            | `log10`     | | `numpy.log10`  |

## Trigonométrie

| **Fonction**                                      | `FreeFem++`          |
|---------------------------------------------------|-----------------------:|
| $\cos$                                            | `cos`                  |
| $\arccos$                                         | `acos`                 |
| $\sin$                                            | `sin`                  |
| $\arcsin$                                         | `asin`                 |
| $\tan$                                            | `tan`                  |
| $\arctan$                                         | `atan`                 |

## Trigonométrie hyperbolique

| **Fonction**     | `FreeFem++` |
|------------------|------------:|
| $\cosh$          | `cosh`      |
| $\text{arccosh}$ | `acosh`     |
| $\sinh$          | `sinh`      |
| $\text{arcsinh}$ | `asinh`     |
| $\tanh$          | `tanh`      |
| $\text{arctanh}$ | `atanh`     |

## Fonctions de Bessel

Les fonctions de Bessel sont des solutions canoniques de l'équation différentielle ordinaire

$$ x^2 \dfrac{d^2y}{dx^2}(x) + x \dfrac{dy}{dx}(x) + (x^2 - \alpha^2) y(x) = 0 $$

où $\alpha \in \mathbb{C}$. Les fonctions de Bessel se distinguent en deux espèces, la première espèce comportant les solutions définies en $0$ et de seconde espèce qui ne le sont pas mais qui y admettent une limite infinie.

> **Définition**
> Fonctions de Bessel de première espèce d'ordre entier $\alpha = n \in \mathbb{N}$
> $$ J_n(x) := \sum_{p=0}^{\infty} \dfrac{(-1)^p}{p! (n+p)!} \left( \dfrac{x}{2} \right)^{2p+n} $$

> **Définition**
> Fonctions de Bessel de deuxième espèce d'ordre entier $\alpha = n \in \mathbb{N}$
> $$ Y_n(x) := \lim_{\lambda \rightarrow n} \dfrac{J_\lambda(x) \cos(\lambda \pi) - J_{-\lambda}(x)}{\sin(\lambda \pi)} $$

| **Fonction**                        | `FreeFem++` |
|-------------------------------------|------------:|
| $1^{\text{ère}}$ espèce d'ordre $0$ | `j0`        |
| $1^{\text{ère}}$ espèce d'ordre $1$ | `j1`        |
| $1^{\text{ère}}$ espèce d'ordre $n$ | `jn(n, x)`  |
| $2^{\text{ème}}$ espèce d'ordre $0$ | `y0`        |
| $2^{\text{ème}}$ espèce d'ordre $1$ | `y1`        |
| $2^{\text{ème}}$ espèce d'ordre $n$ | `yn(n, x)`  |

## Fonction $\Gamma$ et variantes

La fonction $\Gamma$ est une généralisation de la fonction factorielle définie sur $\mathbb{N}$ aux nombres complexes. Elle vérifie la relation fonctionnelle $\Gamma(z+1) = z \Gamma(z)$.

> **Définition** $\forall z \in \mathbb{C} \setminus -\mathbb{N}$
> $$ \Gamma(z) := \int_{0}^{+\infty} t^{z-1} e^{-t} dt $$

Elle converge absolument sur le demi-plan $\{ \mathcal{Re}(z) > 0 \}$ et elle se prolonge de manière unique en une fonction méromorphe sur $\mathbb{C} \setminus -\mathbb{N}$, $-\mathbb{N}$ étant des pôles pour le prolongement.

| **Fonction**      | `FreeFem++` |
|:------------------|------------:|
| $\Gamma$          | `tgamma`    |
| $\ln(\|\Gamma\|)$ | `lgamma`    |

## Fonctions erreur et variantes

> **Définition** La fonction erreur `erf` est la fonction entière
> $$ \text{erf}(x) := \dfrac{2}{\sqrt{\pi}} \int_0^x e^{-t^2}dt $$

> **Définition** La fonction $\text{erfc}$ est définie par
> $$ \text{erfc}(x) := 1 - \text{erf}(x) $$

> **Définition** La fonction $\text{erfcx}$ est 
> $$ \text{erfcx}(x) := e^{x^2} \text{erfc}(x) $$

> **Définition** La fonction $\text{logerfc}$ est
> $$ \text{logerfc}(x) := \ln(\text{erfc})(x) $$

> **Définition** La fonction $\text{logerfcx}$ est
> $$ \text{logerfcx}(x) := \ln(erfcx)(x) $$

> **Définition** La fonction $\text{erfi}$ est 
> $$ \text{erfi}(x) := -i \text{erf}(ix) $$

> **Définition** La fonction $\text{dawson}$ est
> $$ \text{dawson}(x) := \dfrac{\sqrt{\pi}}{2} e^{-x^2} \text{erfi}(x) $$

| **Fonction**       | `FreeFem++` | `Julia/SpecialFunctions.jl` |
|:-------------------|------------:|----------------------------:|
| $\text{erf}$       | `erf`       | `erf`                       | 
| $\text{erfc}$      | `erfc`      | `erfc`                      |
| $\text{erfcx}$     | X           | `erfcx`                     |
| $\text{logerfc}$   | X           | `logerfc`                   | 
| $\text{logerfcx}$  | X           | `logerfcx`                  |
| $\text{erfi}$      | X           | `erfi`                      |
| $\text{dawson}$    | X           | `dawson`                    |
| $\text{erf}^{-1}$  | X           | `erfinv`                    |
| $\text{erfc}^{-1}$ | X           | `erfcinv`                   |    

# Les maillages

## `FreeFem++`

Le langage intègre le logiciel `bamg` pour créer ses maillages. On dispose de nombreuses manière pour produire des maillages déstructurés depuis les scripts.

### Un rectangle en deux dimensions

On peut mailler le rectangle $[a, a+l] \times [b, b+h]$ avec le script suivant.

```cpp
real a = 1.0;    // absisse du coin inférieur gauche
real b = 1.0;    // ordonnée du coin inférieur gauche
real l = 1.0;    // longueur du rectangle
real h = 1.0;    // largeur du rectangle

int nelx = 10;    // nombre d'éléments sur un bord horizontal
int nely = 10;    // nombre d'éléments sur un bord vertical

/*
    Flags : paramètre de construction des arêtes
        0 : (x-y) constante
        1 : alternance de (x-y) et (x+y) constantes (Union Jack)
        2 : (x+y) constante
        3 : (x-y) constante sauf pour deux angles où (x+y) constante
        4 : (x+y) constante sauf pour deux angles où (x-y) constante
*/
int fla = 1;
int[int] lab = [1, 2, 3, 4];    // commence par le bord inférieur puis rotation dans le sens trigonométrique
int reg = 1;                    // label du rectangle, utile pour les indicatrices

mesh th = square(nelx, nely, [a + l*x, b + h*y], flags=fla, label=lab, region=reg);
```

### Maillage d'une surface fermée par un contour paramétré

On prend pour exemple le disque de rayon $r = 1$ centré en le point $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$.

```cpp
real r = 2.0;                // rayon du cercle
real[int] c = [1.0, 1.0];    // coordonnées du centre du cercle

int nelC = 128;    // nombre d'éléments sur le cercle

int labC = 1;    // label du bord du cercle


border C(t=0, 1){
    x = c[0] + r*cos(2*pi*t);
    y = c[1] + r*sin(2*pi*t);
    label = labC;
}

mesh th = buildmesh(C(nelC));
```

Dans le cas où le contour est une concaténation de chemins, il faut parcourir ce chemin de sorte à respecter l'orientation. Par exemple, reprenons le maillage du rectangle précédent en définissant son contour.

```cpp
real l = 5.0;    // longueur du rectangle
real h = 1.0;    // hauteur du rectangle

int nely = 5;           // nombre d'éléments sur un bord vertical
int nelx = l/h*nely;    // nombre d'éléments sur un bord horizontal

border ab(t=0, 1){    // bord inférieur du rectangle
    x = t*l;
    y = 0;
}

border bc(t=0, 1){    // bord droit du rectangle
    x = l;
    y = t*h;
}

border cd(t=0, 1){    // bord supérieur du rectangle
    x = (1-t)*l;
    y = h;
}

border da(t=0, 1){    // bord gauche du rectangle
    x = 0;
    y = (1-t)*h;
}

mesh th = buildmesh(ab(nelx) + bc(nely) + cd(nelx) + da(nely));
```

### Mailler un domaine privé d'un sous-domaine

On prend l'exemple du disque de rayon $r_1 = 3$ centré en $0$ auquel on retire le disque centré en $\begin{bmatrix} 1 \\ 1 \end{bmatrix}$ de rayon $r_0 = 1$.

```cpp
real x0 = 1.0;
real y0 = 1.0;
real r0 = 1.0;

real r1 = 3.0;

int nel  = 64;

border C(t=0, 1){
    x = r1 * cos(2*pi*t);
    y = r1 * sin(2*pi*t);
}

border c(t=0, 1){
    x = x0 + r0*cos(2*pi*t);
    y = y0 + r0*sin(2*pi*t);
}

mesh th = buildmesh(C(nel) + c(-nel/3));
```

### Un rectangle en trois dimensions

De même, on maille le rectangle $[a, a+L] \times [b, b+l] \times [c, c+h]$ à l'aide du script

```cpp
load "msh3"

real a = 1.0;    // absisse
real b = 1.0;    // ordonnée
real c = 1.0;    // cote 
real L = 1.0;    // longueur du rectangle
real l = 1.0;    // largeur du rectangle
real h = 1.0;    // profondeur du rectangle

int nelx = 10;    // nombre d'éléments sur un bord horizontal
int nely = 10;    // nombre d'éléments sur un bord vertical
int nelz = 10;    // nombre d'éléments sur un bord en profondeur

/*
    Flags : paramètre de construction des arêtes
        0 : (x-y) constante
        1 : alternance de (x-y) et (x+y) constantes (Union Jack)
        2 : (x+y) constante
        3 : (x-y) constante sauf pour deux angles où (x+y) constante
        4 : (x+y) constante sauf pour deux angles où (x-y) constante
*/
int fla = 1;
int[int] lab = [1, 2, 3, 4, 5, 6];    // commence par le bord inférieur puis rotation dans le sens trigonométrique
int reg = 1;                          // label du rectangle, utile identifier le domaine

mesh3 th = cube(nelx, nely, nelz, [a + L*x, b + l*y, c + h*z], flags=fla, label=lab, region=reg);
```

### Remarque

Les maillages peuvent être affichés par la fonction `plot()`

```cpp
plot(th, cmm="Maillage Th");
```

mais aussi par `medit()`

```cpp
load "medit"
medit("Maillage", th);
```

# Les espaces d'interpolation

## `FreeFem++`



# Les formulations variationnelles

En général, une équation aux dérivées partielles peut s'étudier sous une forme variationnelle équivalente. Cette forme sera alors discrétisée à l'aide de la méthode de Galerkin et on aboutira à un système linéaire discret portant sur les degrés de libertés de l'interpolée de la solution dans un espace de dimension finie adapté.

Dans les langages spécialisés pour les éléments finis, il est possible de déclarer ces formes en tant que type (ou objet) et de les manipuler. Par exemple, considérons 

$$
\underbrace{\int_\Omega \nabla u^T \nabla v d\mathbf{x}}_{a(u, v)} - \int_{\partial \Omega} \partial_{\vec{n}} u \cdot v d\gamma = \underbrace{\int_{\Omega} f \cdot v d\mathbf{x}}_{l(v)}
$$

## Implémentation des formes $a(\cdot, \cdot)$ et $l(\cdot)$

### `FEniCs/Python3`

```python
from dolfinx.fem import form
from ufl import dx, grad, inner

eq  = inner(grad(u), grad(v)) * dx
eq += inner(f, v) * dx

a = form(lhs(eq))
l = form(rhs(eq))
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

## implémentation de $F(u, v) = 0$

On propose un autre exemple, non-linéaire. Soit à résoudre sur une région du plan $\Omega$ le système d'Oseen homogène

$$
\left\{
\begin{array}{rl}
\text{div}(\mathbf{u}) & = 0 \\
\left( \mathbf{u} \cdot \nabla \right) \mathbf{u} - \Delta \mathbf{u} + \nabla p & = 0 
\end{array}
\right.
$$

$$ \Longrightarrow \underbrace{\int_\Omega \left[ \left( (\mathbf{u} \cdot \nabla)\mathbf{u} \right)^T \cdot \mathbf{v} + \nabla \mathbf{u} : \nabla \mathbf{v} + p \text{div}(\mathbf{v}) - q \text{div}(\mathbf{u}) \right] d\mathbf{x} }_{F(u,v)} = 0 $$

où $\mathbf{u}, \mathbf{v} : \Omega \rightarrow \mathbb{R}^2$ ; $p, q : \Omega \rightarrow \mathbb{R}$.

### `FEniCs/Python3`

Une première implémentation est proposée avec `u` une instance de `V` un objet `dolfinx.fem.FunctionSpace` dont les éléments sont à valeurs vectorielles tandis que `Q` est un espace de fonctions à valeurs scalaires.

```python
from dolfinx.fem import form
from ufl import div, dx, inner, nabla_grad

eq  = inner( dot(u, nabla_grad(u)), v )*dx
eq += inner( nabla_grad(u), nabla_grad(v) )
eq -= p * div(v)
eq -= q * div(u)

F = form(lhs(F))
```

On aurait pu proposer un triplet de fonctions scalaires et implémenter plutôt, avec les variables `(ux, uy, p)` et `(vx, vy, q)`, le problème

```python
# TO DO
```

### `FreeFem++`

On décompose l'inconnue qui est un champ de vecteurs en les deux fonctions scalaires que sont ses coordonnées, ainsi $\mathbf{u} = \begin{pmatrix} u^x \\ u^y \end{pmatrix}$ et on traite les trois inconnues simultanément.

```cpp
varf F([ux, uy, p], [vx, vy, q])
    = int2d(th)( ( ux*dx(ux) + uy*dy(ux) )*vx
               + ( ux*dx(uy) + uy*dy(uy) )*vy 
               + ( dx(ux)*dx(vx) + dy(ux)*dy(vx) + dx(uy)*dx(vy) + dy(uy)*dy(vy) ) 
               - ( p * (dx(vx) + dy(vy)) )
               - ( q * (dx(ux) + dy(uy)) )
    );
```

Les deux premières lignes de l'intégrale représentent le terme $(\mathbf{u} \cdot \nabla)\mathbf{u}^T \mathbf{v}$, la troisième ligne représente la contraction totale $$ \nabla \mathbf{u} : \nabla \mathbf{v} = \sum_{i, j} \partial_i u^j \times \partial_i v^j $$ et enfin les quatrième et cinquième lignes représentent respectivement les expressions $- p \text{div}(\mathbf{v})$ et $- q \text{div}(\mathbf{u})$

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

# Les structures algébriques abstraites avec `SageMath`