# Chapitre 5 — calcOutGivenIn / calcInGivenOut : la formule de swap a poids arbitraires

`calcOutGivenIn` calcule le montant recu pour un montant donne en entree, en appliquant l'invariant pondere du chapitre precedent : le ratio entre l'ancien et le nouveau solde de l'actif en entree, eleve a la puissance du ratio des poids (`weightIn / weightOut`), donne la fraction du solde de l'actif en sortie que le swap doit liberer. `calcInGivenOut` est la fonction reciproque, utile pour `swapExactAmountOut` (chapitre 6) quand l'utilisateur fixe le montant recu plutot que le montant depense.

Cette exponentiation a une puissance fractionnaire (`bpow`, chapitre 7) est ce qui distingue fondamentalement les calculs de swap Balancer de ceux d'Uniswap v2, ou le ratio des poids vaut toujours 1 (poids egaux) et l'exposant disparait de la formule. Avec des poids inegaux, chaque swap necessite une approximation numerique de cette puissance fractionnaire plutot qu'une simple division.

Les frais de swap (`_swapFee`, entre `MIN_FEE` et `MAX_FEE` soit entre 0,0001 % et 10 %) sont preleves des l'entree, en reduisant le montant effectivement pris en compte dans le calcul (`adjustedIn = tokenAmountIn * (1 - swapFee)`) avant d'appliquer la formule d'invariant : les frais restent donc dans le pool, augmentant legerement son solde total et donc la valeur de chaque part de pool existante.

[Chapitre suivant : swapExactAmountIn, swapExactAmountOut et les ratios limites](06-swapexact.md)
