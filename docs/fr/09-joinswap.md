# Chapitre 9 — joinswap et exitswap : deposer ou retirer un seul actif

`joinswapExternAmountIn` et `joinswapPoolAmountOut` permettent de fournir de la liquidite avec un **seul** actif plutot que tous les actifs du pool a la fois : sous le capot, cela revient mathematiquement a un swap partiel de cet actif contre les autres, suivi d'un depot proportionnel, combine en une seule formule (`calcPoolOutGivenSingleIn` dans `BMath.sol`). Ce depot mono-actif deplace donc legerement le prix du pool, a la difference de `joinPool`.

`exitswapPoolAmountIn` et `exitswapExternAmountOut` sont les fonctions miroir pour un retrait mono-actif : bruler des parts de pool pour ne recevoir qu'un seul actif en retour, plutot qu'une portion de chacun. La encore, cette operation deplace le prix relatif des actifs du pool, contrairement a un retrait proportionnel via `exitPool`.

Ces quatre fonctions offrent donc un compromis explicite a l'utilisateur : `joinPool`/`exitPool` preservent le prix du pool mais exigent de detenir (ou de recevoir) tous ses actifs simultanement ; `joinswap*`/`exitswap*` n'exigent qu'un seul actif, au prix d'un leger impact de marche equivalent a un swap partiel.

[Chapitre suivant : finalize, ouvrir un pool au public](10-finalize.md)
