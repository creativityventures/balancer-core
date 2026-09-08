# Chapitre 6 — swapExactAmountIn, swapExactAmountOut et les ratios limites anti-manipulation

`swapExactAmountIn` (l'utilisateur fixe ce qu'il depense, avec un `minAmountOut` de protection contre le glissement) et `swapExactAmountOut` (l'utilisateur fixe ce qu'il recoit, avec un `maxAmountIn` symetrique) sont les deux points d'entree publics pour echanger un actif contre un autre au sein d'un pool finalise et ouvert au public (`_publicSwap`).

Chacune impose une limite sur la taille du swap relative aux reserves du pool : `MAX_IN_RATIO` (la moitie du solde de l'actif en entree, soit 50 %) et `MAX_OUT_RATIO` (un tiers du solde de l'actif en sortie, environ 33,3 %). Un swap qui depasserait ces proportions du pool en un seul appel echoue simplement — une protection contre les swaps disproportionnes qui deplaceraient trop brutalement le prix ou videraient dangereusement un pool en une seule transaction.

Chaque swap verifie egalement, apres l'operation, que le prix spot ne s'est pas deteriore au-dela de la limite `maxPrice` fournie par l'appelant, et que le nouveau prix spot reste superieur ou egal au prix spot avant frais (`spotPriceBefore <= spotPriceAfter`), une invariante de coherence qui garantit que l'AMM n'a jamais avantage un trader par rapport a un autre a cause d'une erreur d'arrondi dans le sens inverse de celui attendu.

[Chapitre suivant : BNum, l arithmetique en virgule fixe](07-bnum.md)
