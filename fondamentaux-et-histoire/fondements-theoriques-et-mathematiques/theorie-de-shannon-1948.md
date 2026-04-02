---
title: Théorie de l'Information de Shannon (1948)
description: Fondements de la quantification, de la compression et de la transmission de données.
published: true
date: 2026-04-02T13:57:46.445Z
tags: réseaux, shannon, entropie, bit, cryptographie
editor: markdown
dateCreated: 2026-04-02T13:57:46.445Z
---

# 📡 La Théorie de l'Information : L'Art du Signal

> **"Le bit n'est pas une unité de stockage, c'est une unité de réduction d'incertitude."**

## 📖 1. La Vulgarisation : C'est quoi ?
Avant 1948, on ne savait pas "combien" d'information contenait un message. Claude Shannon a prouvé que l'information est une grandeur physique mesurable, indépendante du support (fil de cuivre, ondes radio ou papier).

Le concept est simple : plus un événement est **imprévisible**, plus il contient d'**information**. 
* Si je te dis "Le soleil va se lever demain", l'information est quasi nulle (incertitude faible).
* Si je te donne les numéros du Loto, l'information est maximale (incertitude forte).



---

## 🔬 2. Théorie & Concepts (Niveau Expert)

### A. L'Entropie de Shannon ($H$)
Shannon a emprunté le terme "entropie" à la thermodynamique pour mesurer le degré d'incertitude d'une source de données. La formule est :
$$H(X) = -\sum_{i=1}^{n} P(x_i) \log_2 P(x_i)$$
* **$H(X)$** : Entropie en bits.
* **$P(x_i)$** : Probabilité du symbole $i$.

**Application :** Un mot de passe de 8 caractères purement aléatoires a une entropie bien plus élevée qu'un mot de dictionnaire, car chaque caractère est "imprévisible".



### B. Le Théorème du Codage de Canal
Shannon démontre qu'il existe une limite maximale de données que l'on peut envoyer sur un canal (fibre, Wi-Fi) sans erreur, appelée la **Capacité du Canal ($C$)**. 
$$C = B \log_2 (1 + \frac{S}{N})$$
* **$B$** : Bande passante (Hz).
* **$S/N$** : Rapport Signal/Bruit (Signal-to-Noise Ratio).

---

## 🛠️ 3. Application Pratique & Ateliers

### Atelier 1 : Compression (Réduction de la redondance)
La théorie de Shannon est la base du format ZIP ou du JPEG. 
* **Principe** : Remplacer les motifs fréquents (prévisibles) par des codes courts.
* **Exercice** : Analyse de la fréquence des lettres dans un texte (Codage de Huffman). "E" est très fréquent, on lui donne un code de 2 bits. "Z" est rare, on lui donne 8 bits.

### Atelier 2 : Détection d'erreurs
Dans un canal bruité (ex: Wi-Fi perturbé), on ajoute de la **redondance** pour corriger les erreurs. 
* **Concepts à documenter** : Bit de parité, Checksum (Somme de contrôle), CRC (Cyclic Redundancy Check).

---

## 🛡️ 4. Le Lien avec la Cybersécurité & l'Infra

Pourquoi un Manager Cyber doit-il maîtriser Shannon ?

1.  **Force des mots de passe (Password Cracking)** : On ne mesure pas la sécurité d'un mot de passe par sa longueur, mais par son **entropie**. Une attaque par force brute est une tentative de réduire l'entropie de Shannon à zéro.
2.  **Stéganographie** : L'art de cacher un message dans le "bruit" d'une image. Shannon nous aide à comprendre où se situe le bruit exploitable.
3.  **Disponibilité (Availability)** : En infrastructure, le calcul de la capacité du canal ($C$) permet de dimensionner les liens réseaux pour éviter la congestion (bruit logique).
4.  **Cryptographie "Parfaite"** : Shannon a prouvé que le **Masque Jetable (One-Time Pad)** est le seul système inviolable, car l'entropie du message chiffré est égale à celle de la clé, ne laissant aucun indice à l'attaquant.

---

## 📚 Ressources complémentaires
* *Papier Original* : "A Mathematical Theory of Communication" (1948).
* *Vidéo* : "The Bit" (Documentaire sur Claude Shannon).
* *Outil* : Calculateur d'entropie de fichiers (utilisé en Forensic pour détecter des fichiers chiffrés ou compressés).