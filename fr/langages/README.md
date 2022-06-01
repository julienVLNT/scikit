# Introduction <!-- omit in toc -->

Ce document est là pour porter un regard croisé sur la représentation de structures de données usuelles en mathématiques appliquées au travers de différents langages de programmation.

- [Les booléens](#les-booléens)
- [Les entiers relatifs](#les-entiers-relatifs)
- [Les nombres décimaux](#les-nombres-décimaux)
- [Les nombres rationnels](#les-nombres-rationnels)
- [Les nombres réels](#les-nombres-réels)
- [Les nombres complexes](#les-nombres-complexes)
- [Synthèse sur les types numériques](#synthèse-sur-les-types-numériques)
- [Les constantes](#les-constantes)
- [Les vecteurs](#les-vecteurs)
- [Les matrices](#les-matrices)
- [Les tenseurs](#les-tenseurs)
- [Objets pour l'algèbre linéaire creuse](#objets-pour-lalgèbre-linéaire-creuse)
- [Synthèse de l'algèbre linéaire](#synthèse-de-lalgèbre-linéaire)
- [Les fonctions (et macro ou lambda expressions...)](#les-fonctions-et-macro-ou-lambda-expressions)
- [Les fonctions numériques spéciales](#les-fonctions-numériques-spéciales)
- [Les maillages](#les-maillages)
- [Attributs et méthodes pour les maillages](#attributs-et-méthodes-pour-les-maillages)
- [L'interpolation : espaces et champs](#linterpolation--espaces-et-champs)
- [Implémentation des formes linéaires et résolution](#implémentation-des-formes-linéaires-et-résolution)
  - [`FreeFem++`](#freefem)
- [Les conditions aux limites dans les éléments finis](#les-conditions-aux-limites-dans-les-éléments-finis)

# Les booléens 

| **Booléen**   | **Symbole**    | `C++`      | `FreeFem++` | `Julia`    | `Python3` |
|:--------------|:---------------|-----------:|------------:|-----------:|----------:|
| type ou objet | X              | `bool`     | `bool`      | `Bool`     | `bool`    |
| vrai          | 1              | `true`     | `true`      | `true`     | `True`    |
| faux          | 0              | `false`    | `false`     | `false`    | `False`   |
| non           | $\neg$         | `!a`       | `!a`        | `!a`       | `not(a)`  |
| et            | $\wedge$       | `a && b`   | `a && b`    | `a && b`   | `a and b` |
| ou            | $\vee$         | `a \|\| b` | `a \|\| b`  | `a \|\| b` | `a or b`  |

## Egalité de booléens <!-- omit in toc -->

Dans tous les langages cités ci-dessus, l'opérateur binaire `==` teste l'égalité entre deux booléens.

## Remarques <!-- omit in toc -->

### Opération logique != opération bit-à-bit <!-- omit in toc -->

Il faut différencier les opérations sur les booléens vus comme types des opérations logiques effectuées sur chaque bit de la représentation binaire d'un objet ou d'un type.

### `C` <!-- omit in toc -->

Le type booléen n'est pas intrinsèquement implémenté dans le langage `C`, on peut les manipuler en tant que type grâce à la librairie `stdbool` ou définir un type *à la main* basé sur les entiers non-signés par exemple. Sinon on les manipule selon l'association `vrai` ~ `1`, `faux` ~ `0`.

### `FreeFem++` <!-- omit in toc -->

Il est courant de trouver dans les codes la représentation entière du type booléen, avec `true` ~ `1` et `false` ~ `0`.

### `Python3` <!-- omit in toc -->

Il y a énormément de manières de définir le **faux** : les objets `None` et `False`, certes, mais aussi le `0` de tous les types numériques ou les collections vides : `''`, `()`, `[]`, `set()`, `range(0)` ...

### `SageMath` <!-- omit in toc -->

Les objets `bool` de `SageMath` correspondent exactement au modèle introduit par `Python3`.

# Les entiers relatifs

## Types ou objets représentant les entiers <!-- omit in toc -->

### `C++` <!-- omit in toc -->

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

### `FreeFem++` <!-- omit in toc -->

Le type utilisé par `FreeFem++` pour représenter les entiers est équivalent au type `long` en `C++`. Pour déclarer un entier, on utilise 

```cpp
int m;
```

auquel cas il se voit affecté la valeur $0$. 

## Relations d'ordre sur les entiers <!-- omit in toc -->

Les opérateurs représentant les relations d'ordre renvoient un booléen. 

| **Test logique**   | **Symbole** | `C++`    | `FreeFem++` | `Julia`  | `Python3` | `SageMath` |
|:-------------------|:------------|---------:|------------:|---------:|----------:|-----------:|
| Test d'égalité     | $=$         | `m == n` | `m == n`    | `m == n` | `m == n`  | `m == n`   |
| Test de différence | $\neq$      | `m != n` | `m != n`    | `m != n` | `m != n`  | `m != n`   |
| Inférieur ou égal  | $\leq$      | `m <= n` | `m <= n`    | `m <= n` | `m <= n`  | `m <= n`   |
| Inférieur strict   | $<$         | `m < n`  | `m < n`     | `m < n`  | `m < n`   | `m < n`    |
| Supérieur ou égal  | $\geq$      | `m >= n` | `m >= n`    | `m >= n` | `m >= n`  | `m >= n`   |
| Supérieur strict   | $>$         | `m > n`  | `m > n`     | `m > n`  | `m > n`   | `m > n`    |

## Opérateurs sur les entiers <!-- omit in toc -->

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

## Remarques <!-- omit in toc -->

### `FreeFem++` <!-- omit in toc -->

En `FreeFem++`, les affectations des résultats de `m % n` et `m ^ n` sous leur forme `m %= n` et `m ^= n` donnent des erreurs à la compilation. 

### `Julia` <!-- omit in toc -->

En `Julia`, l'affectation du résultat pour la division donne systématiquement des nombres réels. C'est pourquoi on note un X dans la case correspondante.

### `Python3` <!-- omit in toc -->

Le couple quotient et reste pour la division euclidienne s'obtient à l'aide de la fonction `divmod(m, n)`. L'élévation de `m` à la puissance `n` s'obtient à l'aide de `pow(m, n)`.

# Les nombres décimaux

## `Python3/Decimal` <!-- omit in toc -->

```python
d = decimal.Decimal()              # déclaration et affectation à Decimal('0')
d = decimal.Decimal('1.23456')     # déclaration et affectation à Decimal('1.23456')
d = decimal.Decimal('3.1415')      # déclaration et affectation

+d                                 # identité
-d                                 # opposé
abs(d)                             # valeur absolue

d1 + d2                            # addition
d1 - d2                            # soustraction
d1 * d2                            # multiplication
d1 / d2                            # division réelle
d1 // d2                           # quotient de la division euclidienne étendue
d1 % d2                            # reste de la division euclidienne étendue
d1 ** d2                           # exponentiation

d1 == d2                           # test d'égalité
d1 <= d2                           # test inférieur ou égal à
d1 < d2                            # test strictement inférieur à
d1 >= d2                           # test supérieur ou égal à
d1 > d2                            # test strictement supérieur à

d.exp()                            # composition par l'exponentielle
d.ln()                             # composition par le logarithme naturel
d.log10()                          # composition par le logarithme de base 10
d.logb()                           # exposant ajusté de l'argument
d.sqrt()                           # composition par la racine carrée

decimal.getcontext()               # paramètres globaux du module decimal
decimal.getcontext().prec = 3      # édition d'un paramètre de l'objet Context
```

# Les nombres rationnels

## `Python3/Fraction` <!-- omit in toc -->

```python
import fractions
p = fractions.Fraction()           # déclaration et affectation à Fraction(0, 1)
p = fractions.Fraction(2,3)        # déclaration et affectation à Fraction(2,3) i.e 2/3

+p                                 # identité
-p                                 # opposé
abs(p)                             # valeur absolue

r + s                              # addition
r - s                              # soustraction
r * s                              # multiplication interne
r / s                              # division rationnelle
r // s                             # quotient de la division euclidienne étendue
r % s                              # reste de la division euclidienne étendue
r ** s                             # exponentiation

r == s                             # test d'égalité
r <= s                             # test inférieur ou égal à
r < s                              # test strictement inférieur à
r >= s                             # test supérieur ou égal à
r > s                              # test strictement supérieur à
```

# Les nombres réels

## `Python3` <!-- omit in toc -->

```python
x = float()                        # déclaration et affectation à 0.0
x = float(1.1)                     # déclaration et affectation à 1.1
x = float(2*3.1)                   # déclaration et affectation à 6.2
x = -1.                            # déclaration et affectation à -1.0
x, y = 1.4, 3.1                    # déclaration et affectation multiple

+x                                 # identité
-x                                 # opposé
abs(x)                             # valeur absolue

x + y                              # addition
x - y                              # soustraction
x * y                              # multiplication
x / y                              # division réelle
x // y                             # quotient de la division euclidienne étendue
x % y                              # reste de la division euclidienne étendue
x ** y                             # exponentiation

x is y                             # test d'identité
x == y                             # test d'égalité
x <= y                             # test inférieur ou égal à
x < y                              # test strictement inférieur à
x >= y                             # test supérieur ou égal à
x > y                              # test strictement supérieur à
x.is_integer()                     # test d'appartenance à l'ensemble des entiers
```

# Les nombres complexes

## `Python3` <!-- omit in toc -->

```python
z = complex()                      # déclaration et affectation à 0 complexe
z = complex(1.+1.j)                # déclaration et affectation à 1 + i
z = complex(1.+1j)                 # déclaration et affectation à 1 + i
z = complex(1+1.j)                 # déclaration et affectation à 1 + i
z = complex(1+1j)                  # déclaration et affectation à 1 + i
z = 1 + 3j                         # déclaration et affectation à 1 + 3i
w, z = 1+1j, 1.-1j                 # déclaration et affectation multiple

+z                                 # identité
-z                                 # opposé
abs(z)                             # module
z.real                             # partie réelle
z.imag                             # partie imaginaire
z.conjugate()                      # complexe conjugué

w + z                              # addition
w - z                              # soustraction
w * z                              # multiplication
w / z                              # division complexe
w ** z                             # exponentiation

w is z                             # test d'identité
w == z                             # test d'égalité
```

# Synthèse sur les types numériques

# Les constantes

| **Constante mathématique** | **Symbole** | `FreeFem++` | `Julia`   | `Python3/Scipy` | `SageMath`     |
|:---------------------------|:------------|------------:|----------:|----------------:|---------------:|
| Zéro                       | $0$         | `0`         | `0`       | `0`             | `0`            |
| Un                         | $1$         | `1`         | `1`       | `1`             | `1`            |
| Imaginaire pur             | $i$         | `1i`        | `1im`     | `1j`            | `1j`           |
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

## `FreeFem++` <!-- omit in toc -->

On note ici les principaux attributs, les principales méthodes associées à la représentation des vecteurs. On rappelle également la syntaxe des opérations usuelles. La fiche est écrite pour les vecteurs construits sur $\mathbb{R}$, on peut aisément construire des vecteurs de nombres complexes à l'aide de `complex[int]`.

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

## `Julia` <!-- omit in toc -->

```julia

```

## `Python3/Numpy` <!-- omit in toc -->

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

### `FreeFem++` <!-- omit in toc -->

Les matrices denses ne sont pas implémentées dans ce langage. Les objets `real[int, int]` sont des vecteurs de vecteurs mais les opérations standards ne sont pas implémentées pour ces objets. On regardera l'objet `matrix` dans la section sur les [matrices creuses](#algèbre-creuse).

```cpp

```

### `Julia` <!-- omit in toc -->

```julia

```

### `Python3/Numpy` <!-- omit in toc -->

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

## Généralités... <!-- omit in toc -->



## `Julia/Tensors.jl` <!-- omit in toc -->

La librairie `Tensors.jl` a pour but d'assembler et de manipuler uniquement les tenseurs usuels qu'on trouve en physique et en ingénierie. On traite les tenseurs, symétriques ou non, de rang $2$ ou $4$ construits sur les espaces $\mathbb{R}^2$ ou $\mathbb{R}^3$.

```julia

```

## `Python3/Numpy` <!-- omit in toc -->

```python

```

## `SageMath` <!-- omit in toc -->

```python

```

## `Tensorflow/Python3` <!-- omit in toc -->

```python

```

# Objets pour l'algèbre linéaire creuse

## `FreeFem++` <!-- omit in toc -->

```cpp

```

## `Julia` <!-- omit in toc -->

```julia

```

## `Python3/Scipy.sparse` <!-- omit in toc -->

```python

```

# Synthèse de l'algèbre linéaire



# Les fonctions (et macro ou lambda expressions...)

## `FreeFem++` <!-- omit in toc -->

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

## `Julia` <!-- omit in toc -->

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

## `Python3` <!-- omit in toc -->

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

## `FreeFem++` <!-- omit in toc -->

De nombreuses fonctions spéciales sont implémentées dans le langage. On les trouve listées dans la documentation.

## `Julia` <!-- omit in toc -->

La librairie `Julia/SpecialFunctions.jl` contient un certain nombre de fonctions spéciales

## `Python3` <!-- omit in toc -->

De très nombreuses fonctions spéciales sont implémentées en langage Python dans les différentes librairies de calcul scientifique. `Numpy` contient une excellente base de ces fonctions, `Scipy` en contient également, les librairies de statistiques...

# Les maillages

## `FreeFem++` <!-- omit in toc -->

Le langage intègre le logiciel `bamg` pour créer ses maillages. On dispose de nombreuses manière pour produire des maillages déstructurés depuis les scripts.

### Maillage d'un élément à une dimension plongé dans l'espace <!-- omit in toc -->

```cpp
load "msh3"

int nel = 128;

func torex = cos(2*pi*y)*cos(2*pi*x);
func torey = cos(2*pi*y)*sin(2*pi*x);
func torez = sin(2*pi*y);

meshL th = segment(nel, [torex, torey, torez], removeduplicate=true);
```

### Un rectangle en deux dimensions <!-- omit in toc -->

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

### Maillage d'une surface fermée par un contour paramétré <!-- omit in toc -->

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
real a = 1.0;    // absisse du point inférieur gauche
real b = 1.0;    // ordonnee du point inférieur gauche

real l = 5.0;    // longueur du rectangle
real h = 1.0;    // hauteur du rectangle

int nely = 5;           // nombre d'éléments sur un bord vertical
int nelx = l/h*nely;    // nombre d'éléments sur un bord horizontal

border ab(t=0, 1){    // bord inférieur du rectangle
    x = a + t*l;
    y = b;
}

border bc(t=0, 1){    // bord droit du rectangle
    x = a + l;
    y = b + t*h;
}

border cd(t=0, 1){    // bord supérieur du rectangle
    x = a + (1-t)*l;
    y = b + h;
}

border da(t=0, 1){    // bord gauche du rectangle
    x = a;
    y = b + (1-t)*h;
}

mesh th = buildmesh(ab(nelx) + bc(nely) + cd(nelx) + da(nely));
```

### Mailler un domaine privé d'un sous-domaine <!-- omit in toc -->

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

### Maillage d'une surface plongée dans l'espace <!-- omit in toc -->

On prend l'exemple de la sphère de rayon $1$.

```cpp
load "msh3"

int nel = 32;

func torex = cos(2*pi*y)*cos(2*pi*x);
func torey = cos(2*pi*y)*sin(2*pi*x);
func torez = sin(2*pi*y);

meshS th = square3(nel, nel, [torex, torey, torez]);
```

### Un rectangle en trois dimensions <!-- omit in toc -->

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

### Maillage par *isolines* et application au maillage issu d'une photographie <!-- omit in toc -->

```cpp

```

### Remarque <!-- omit in toc -->

Les maillages peuvent être affichés par la fonction `plot()`

```cpp
plot(th, cmm="Maillage Th");
```

mais aussi par `medit()`

```cpp
load "medit"
medit("Maillage", th);
```

# Attributs et méthodes pour les maillages

| **Attributs et méthodes usuels**                  | `FreeFem++`             |
|:--------------------------------------------------|------------------------:|
| Aire du maillage                                  | `Th.area`               |
| Périmètre du maillage                             | `Th.bordermeasure`      |
| Nombre de triangles                               | `Th.nt`                 |
| Nombre d'arêtes                                   | `Th.nv`                 |
| Nombre d'éléments au bord                         | `Th.nbe`                | 
|---------------------------------------------------|-------------------------|
| Triangle `k` du maillage                          | `Th[k]`                 |
| Sommet `i` du triangle `k`                        | `Th[k][i]`              |
| Sommet `i` du maillage                            | `Th(i)`                 |
| Indice du triangle contenant `(x,y)`              | `Th(x, y).nuTriangle`   |
| Indice de la région contenant `(x,y)`             | `Th(x, y).region`       |
|---------------------------------------------------|-------------------------|
| Aire du triangle `k`                              | `Th[k].area`            |
| Région du triangle `k`                            | `Th[k].region`          |
| Triangle adjacent au triangle `k` par l'arête `e` | `Th[k].adj(e)`          |
|---------------------------------------------------|-------------------------|
| Arête `l` de l'élément sur le bord `k`            | `Th.be(k)[l]`           |
| Triangle de l'élément sur le bord `k`             | `Th.be(k).Element`      |
| Arête du triangle de l'élément sur le bord `k`    | `Th.be(k).whoinElement` |

# L'interpolation : espaces et champs

## `FreeFem++` <!-- omit in toc -->

Un espace d'interpolation est introduit par le mot-clef `fespace` pour *finite element space*. A la déclaration, on renseigne le maillage ainsi qu'une base d'interpolation.

```cpp
fespace Vh(Th, Ph);
```

où on a un maillage `Th` et une base d'interpolation `Ph` . On déclare un champ élément fini à l'aide de

```cpp
Vh u;
```

## Synthèse sur les espaces d'interpolation et les champs éléments finis <!-- omit in toc -->

# Implémentation des formes linéaires et résolution

La construction d'un cadre adapté à l'analyse par éléments finis d'une équation aux dérivées partielles implique de commencer par la recherche d'une formulation variationnelle équivalente à la formulation forte d'une équation. La détermination d'une telle forme utilise le théorème de Green et ses corollaires :

> **Théorème (Green)** $\forall u, v \in \text{H}^1(\Omega)$,
> $$ \int_\Omega (\Delta u) \, v \; d\mathbf{x} + \int_\Omega \nabla u^T \, \nabla v \; d\mathbf{x} = \int_{\partial \Omega} v \; (\nabla u^T \, \mathbf{n}) \; d\gamma(\mathbf{x}) $$

Par exemple, on considère l'équation de Poisson posée sur $\text{H}^1(\Omega)$. Soit $f \in L^2(\Omega)$,

$$
\left\{
    \begin{array}{rr}
        - \Delta u = f & \Omega \\
        u_{|\partial \Omega} = 0
    \end{array}
\right.
$$

sur un ouvert connexe régulier $\Omega$. Soit $v \in \text{H}_0^1(\Omega)$, on intègre l'équation de Poisson sur le domaine après l'avoir multipliée par $v$.

$$ - \int_\Omega (\Delta u) \, v \; \mathbf{dx} = \int_\Omega f \, v \; d\mathbf{x} $$

L'application du théorème de Green nous donne la forme variationnelle de Poisson 

$$ \int_\Omega (\nabla u)^T \, \nabla v \; d\mathbf{x} - \int_{\partial \Omega} v \; (\nabla u^T \, \mathbf{n}) \; d\gamma(\mathbf{x}) = \int_\Omega f \, v \; d\mathbf{x} $$

Par définition, $v = 0$ sur le bord $\partial \Omega$, d'où

$$ \boxed{ \int_\Omega (\nabla u)^T \, \nabla v \; d\mathbf{x} = \int_\Omega f \, v \; d\mathbf{x} } $$

## `FreeFem++`

Une première manière de le résoudre est de construire les deux formes $a(\cdot, \cdot)$ et $l(\cdot)$ définies comme étant les membre de gauche et de droite respectivement de l'équation encadrée. Les conditions aux limites s'ajoutent dans la forme bilinéaire $a(\cdot, \cdot)$. On suppose construit un maillage en deux dimensions `mesh Th` et un espace élément fini `fespace Vh`.

```
// Déclaration de la fonction second membre
func f = 1 - x^2 - y^2;

// Macro gradient d'un champ scalaire
macro grad(u) [dx(u), dy(u)] //

// Implémentation des formes a(.,.) et l(.)
varf a(u, v) = int2d(Th)( grad(u)' * grad(v) ) + on(1, 2, 3, 4, u=0);

varf l(unused, v) = int2d(Th)( f * v );

// Assemblage du système linéaire associé la formulation variationnelle
matrix A = a(Vh, Vh);
real[int] b = l(0, Vh);

// Résolution du problème
Vh u = A^(-1)*b;
```

Les fonctions données dans un problème, telles que le second membre $f$, des conditions aux limites non-homogènes, des fonctions paramètres, et à valeurs scalaires, se déclarent en tant que fonctions `func f`. On rappelle que les identificateurs `x`, `y`, `z` sont globaux. D'autre part, toute transformation sur les fonctions éléments finis, comme `grad(u)`, s'implémentent sous la forme de macro. Il en va de même des paramètres à valeurs vectorielles ou matricielles. Le système linéaire est paramétrable, on se réfère à la section sur les [matrices](#objets-pour-lalgèbre-linéaire-creuse).

D'autres implémentations du même problème existent. Une seconde manière de résoudre le même problème utilise le mot-clef `problem`.

```
func f = 1 - x^2 - y^2;

Vh u, v;

macro grad(u) [dx(u), dy(u)] //

problem Poisson(u, v) = int2d(Th)( grad(u)' * grad(v) ) - int2d(Th)( f * v ) + on(1, 2, 3, 4, u=0);

Poisson;
```

L'instruction `Poisson;` modifie la fonction `u` (ses degrés de liberté) de sorte qu'elle stocke la solution. On note que contrairement à l'usage du mot-clef `varf`, il faut explicitement déclarer les fonctions élément fini `u` et `v` avant l'appel. Une troisième méthode implique le mot-clef `solve`, comme dans

```
func f = 1 - x^2 - y^2;

Vh u, v;

macro grad(u) [dx(u), dy(u)] //

solve Poisson(u, v) = int2d(Th)( grad(u)' * grad(v) ) - int2d(Th)( f * v ) + on(1, 2, 3, 4, u=0);
```

Cette fois, le problème est résolu à sa déclaration. De nouveau, on déclare explicitement les champs `u` et `v` avant la résolution.

---

# Les conditions aux limites dans les éléments finis

