# Aide-mémoire pour la physique de Darcy

Soit $\Omega$ une région du plan occupée par un milieu poreux. On suppose que ses pores, les espace vides, sont saturés d'un liquide qui s'écoule en régime stationnaire.

Un milieu poreux est caractérisé par les grandeurs
- $\varepsilon$ un nombre réel représentant sa porosité volumique, qui quantifie le rapport de l'espace occupé par le fluide par rapport à un volume de référence (comprenant le volume de la matrice solide)
- $\mathbf{K}$ un tenseur de type deux représentant la perméabilité du milieu.

Un fluide newtonien incompressible, est caractérisé par
- $\rho$ un nombre réel, sa masse volumique
- $\mu$ un nombre réel, sa viscosité dynamique

L'hypothèse d'**homogénéité** signifie que chaque grandeur définie plus haut est constante en espace. L'hypothèse d'**isotropie** impose que le milieu n'a pas de direction privilégiée, ce qui se traduit par le fait que le tenseur $\mathbf{K}$ se réduit à un scalaire, au sens où $$ \mathbf{K} = \lambda \, \text{Id} $$ et $\lambda$ est un nombre réel. Si le milieu est **orthotrope**, on distingue deux coefficients diagonaux pour la matrice associée au tenseur $$ \mathbf{K} = \begin{bmatrix} \lambda_1 & 0 \\ 0 & \lambda 2 \end{bmatrix} $$ Enfin, un milieu **anisotrope** voit une matrice la plus générale possible $$ \mathbf{K} = \begin{bmatrix} K_{11} & K_{12} \\ K_{21} & K_{22} \end{bmatrix} $$

Ainsi, dans un milieu **non-homogène**, chaque coefficient défini plus haut devient une fonction de l'espace : $\varepsilon \equiv \varepsilon(\vec x)$, $\mu \equiv \mu(\vec x)$, $\mathbf{K} \equiv \mathbf{K}(\vec x)$ etc.

---

La dynamique du problème est en fait celle de l'écoulement du fluide. Dans une vision eulérienne, l'état du fluide est entièrement déterminé par deux champs

- $\mathbf{v} : \Omega \rightarrow \mathbb R^2$, le champ de vecteurs vitesse dans le fluide
- $p : \Omega \rightarrow \mathbb R$, le champ scalaire de pression dans le fluide.

$$
\left\{
\begin{array}{rclr}
\text{div}(\varepsilon \, \mathbf{v}) & = & f & \Omega \\
\mathbf{v} & = & \frac{1}{\mu} \, \mathbf{K} \cdot \nabla p & \Omega
\end{array}
\right.
$$

> *Remarque* $f : \Omega \rightarrow \mathbb R$ est une fonction  témoignant d'une source de matière en tant que second membre d'une équation traduisant la conservation de la masse.

> *Remarque* Ici, seul le gradient de pression est impliqué. En pratique, la simulation pourra donc considérer des régions de pression nulle, bien que je ne sois pas certain que cela ait un sens physique en dehors d'un vide. Il s'agira ensuite de translater le champ de pression par une fonction constante pour retrouver le champ physique.
