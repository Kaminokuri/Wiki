---
title: Représentation des Données
description: 
published: true
date: 2026-04-02T14:01:27.771Z
tags: binaire, architecture, encodage, ieee-754
editor: markdown
dateCreated: 2026-04-02T14:01:27.771Z
---

# 🔢 Représentation des Données : Du Bit au Symbole

La représentation des données est l'interface entre le monde physique (tensions électriques) et le monde logique (nombres, textes, images). Une mauvaise compréhension de ces structures est à l'origine des bugs les plus célèbres de l'histoire de l'informatique.

---

## 1. Les Systèmes de Numération (Bases)

L'informatique utilise principalement trois bases pour manipuler les données :

* **Base 2 (Binaire)** : L'alphabet du processeur $\{0, 1\}$.
* **Base 16 (Hexadécimal)** : L'alphabet de l'ingénieur $\{0-9, A-F\}$. Utilisé pour condenser le binaire (1 quartet = 1 chiffre hexadécimal).
* **Base 8 (Octal)** : $\{0-7\}$. Moins fréquent aujourd'hui, mais encore présent dans les permissions Unix.

### Conversion et manipulation
Le passage d'une base à l'autre repose sur la notation positionnelle :
$$N = \sum_{i=0}^{n} d_i \cdot B^i$$
Où $d$ est le chiffre et $B$ la base.

---

## 2. Représentation des Nombres Entiers

### A. Entiers non signés (Unsigned)
Le codage est direct. Sur $n$ bits, on peut représenter les valeurs de $0$ à $2^n - 1$.

### B. Entiers signés : Le Complément à deux
Pour représenter les nombres négatifs, l'informatique moderne utilise presque exclusivement le **complément à deux**.
* **Avantage** : Permet d'utiliser le même circuit électronique pour l'addition et la soustraction (pas de gestion du signe séparée).
* **Calcul** : Pour obtenir l'opposé d'un nombre :
    1. Inverser tous les bits (NOT).
    2. Ajouter 1 au résultat.

**Exemple sur 8 bits pour $-5$ :**
$5$ en binaire = `0000 0101`
Inversion = `1111 1010`
$+1$ = `1111 1011` (Représentation de $-5$)

---

## 3. Les Nombres à Virgule Flottante (IEEE 754)

La norme **IEEE 754** définit comment stocker des nombres réels avec une précision variable. Un nombre est décomposé en trois parties :
1.  **Le Signe (S)** : 1 bit (0 pour +, 1 pour -).
2.  **L'Exposant (E)** : Codé avec un biais (souvent 127 en simple précision).
3.  **La Mantisse (M)** ou Fraction.



### Formule de calcul
La valeur d'un nombre en simple précision (32 bits) est :
$$V = (-1)^S \times (1 + M) \times 2^{E-127}$$

**Le problème de la précision** : Certains nombres décimaux simples (comme $0,1$) ne peuvent pas être représentés de manière exacte en binaire, ce qui entraîne des erreurs d'arrondi cumulatives dans les calculs financiers ou scientifiques.

---

## 4. Encodage des Caractères : Du Télégraphe à l'Universel

### A. L'ASCII (7 bits)
Le standard historique codant 128 caractères (principalement l'alphabet latin sans accents et les codes de contrôle).


### B. L'Unicode et l'UTF-8
Pour supporter toutes les langues du monde, l'Unicode attribue un "Code Point" unique à chaque symbole. **UTF-8** est l'encodage dominant car il est :
* **Variable** : Utilise de 1 à 4 octets.
* **Rétrocompatible** : Les 128 premiers caractères sont identiques à l'ASCII.
* **Auto-synchronisé** : On peut identifier le début d'un caractère même si le flux est corrompu.

---

## 5. L'Ordonnancement des Octets (Endianness)

L'Endianness définit l'ordre dans lequel les octets d'un mot de plusieurs octets (ex: un entier 32 bits) sont stockés en mémoire.

* **Big-Endian (Grand-boutiste)** : L'octet de poids fort est stocké à l'adresse la plus basse (ordre de lecture humain). Utilisé historiquement dans les protocoles réseau (IP).
* **Little-Endian (Petit-boutiste)** : L'octet de poids faible est stocké à l'adresse la plus basse. Utilisé par les processeurs Intel/AMD (x86).



**Exemple :** La valeur `0x12345678`
* **Big Endian** : `12 34 56 78`
* **Little Endian** : `78 56 34 12`

---

## 6. Structures de Données Complexes (Bas Niveau)

Au niveau du matériel, tout est "mis à plat" en mémoire :
* **Tableaux** : Contigus en mémoire. L'accès à `Tab[i]` est un simple calcul d'adresse : $Base + (i \times taille\_element)$.
* **Pointeurs** : Une variable dont la valeur est une adresse mémoire. C'est le fondement de la gestion dynamique de la mémoire (Heap vs Stack).
* **Alignement mémoire** : Pour des raisons de performance, les processeurs préfèrent lire les données à des adresses multiples de 4 ou 8 octets. Cela introduit du "Padding" (bourrage) dans les structures de données.

---

## 🛠️ Atelier Pratique : Inspection Binaire
Utilise un éditeur hexadécimal (comme `hexedit` sur Linux ou `HxD` sur Windows) pour ouvrir un fichier texte simple.
1.  Observe l'encodage des lettres.
2.  Change l'encodage du fichier en UTF-16 et observe comment chaque lettre passe de 1 à 2 octets.
3.  Cherche la "Signature" (Magic Number) du fichier (ex: `89 50 4E 47` pour un PNG).