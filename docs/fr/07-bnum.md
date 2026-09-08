# Chapitre 7 — BNum : l arithmetique en virgule fixe et l exponentiation fractionnaire

Solidity ne manipule nativement que des entiers : `BNum.sol` definit `BONE` (10^18) comme unite de virgule fixe et fournit les operations de base (`badd`, `bsub`, `bmul`, `bdiv`) qui multiplient ou divisent par `BONE` au bon moment pour preserver la precision decimale a travers les calculs — le meme motif que le "facteur" (factor) deja rencontre dans les parcours Aave v3 et Compound v3 de ce compte, ici nomme differemment mais avec la meme unite de 18 decimales.

`bpow` est la fonction la plus delicate : elle calcule une puissance `base^exp` ou l'exposant `exp` peut lui-meme etre une fraction (representee en virgule fixe). Elle decompose l'exposant en une partie entiere, traitee par exponentiation rapide (`bpowi`, multiplications successives par doublement), et une partie fractionnaire, approchee par `bpowApprox`, un developpement en serie qui s'arrete des que le terme suivant devient plus petit que `BPOW_PRECISION` (10^8, soit une precision d'environ 10 decimales).

Cette approximation numerique introduit une imprecision volontaire mais bornee dans tous les calculs de swap et de prix qui en dependent : le code documente explicitement cette limite de precision plutot que de pretendre a une exactitude parfaite, un choix de conception assume pour rendre l'exponentiation fractionnaire calculable a un cout de gaz raisonnable on-chain.

[Chapitre suivant : joinPool et exitPool, le depot et retrait multi-actifs](08-joinexit.md)
