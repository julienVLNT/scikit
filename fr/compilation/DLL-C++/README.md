# Tutoriel de création d'une D.L.L écrite en C

Notes sur le tutoriel proposé par Microsoft : [https://docs.microsoft.com/fr-fr/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp?view=msvc-170](https://docs.microsoft.com/fr-fr/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp?view=msvc-170).

La procédure de création d'une DLL est la suivante. Ici, on écrit la librairie dynamique en C et l'application cliente en C++. Il s'agit d'une librairie qui calcule les termes de la suite de Fibonacci (généralisée) et le client appelle la fonction de calcul jusqu'à remplir un entier de 64 bits.

On commence par ouvrire Visual Studio.

## Créer un projet D.L.L

![Créer un projet DLL](images/creerUnProjetDLL.jpg)

## Ajouter un fichier header `fibonacci.h`

Dans le noeud de l'explorateur de projet `Fichiers d'en-tête`, ajouter un fichier `header .h`. On le rédige ainsi

```cpp
#pragma once

#ifdef FIBONACCI_EXPORTS
#define FIBONACCI_API __declspec(dllexport)
#else
#define FIBONACCI_API __declspec(dllimport)
#endif

extern "C" FIBONACCI_API void fibonacci_init(
    const unsigned long long a, const unsigned long long b);

extern "C" FIBONACCI_API bool fibonacci_next();

extern "C" FIBONACCI_API unsigned long long fibonacci_current();

extern "C" FIBONACCI_API unsigned fibonacci_index();
```

## Ajouter une implémentation pour la D.L.L
