# Chapitre 8 — joinPool et exitPool : deposer et retirer proportionnellement a tous les actifs

`joinPool` est la maniere "par defaut" de fournir de la liquidite a un pool Balancer deja finalise : l'utilisateur choisit un nombre de parts de pool (`poolAmountOut`) qu'il souhaite recevoir, et le contrat calcule le ratio correspondant par rapport a l'offre totale de parts existante, puis preleve **chaque** actif du pool dans ce meme ratio exact — un depot simultane et proportionnel sur tous les actifs a la fois, jamais sur un seul.

`exitPool` fait l'inverse : bruler des parts de pool (`poolAmountIn`) rend, dans le meme ratio, une portion de chacun des actifs detenus par le pool, apres deduction d'un `exitFee` optionnel (nul dans cette version, `EXIT_FEE = 0`). Un tableau `minAmountsOut`, un par actif du pool, protege le sortant contre un retrait qui livrerait moins que ce qu'il attend sur n'importe lequel des actifs.

Ce mecanisme proportionnel garantit qu'un depot ou un retrait via `joinPool`/`exitPool` ne modifie jamais le prix relatif des actifs du pool (puisque tous les soldes bougent dans la meme proportion, l'invariant pondere du chapitre 4 reste inchange a un facteur d'echelle pres) — contrairement aux fonctions a un seul actif du chapitre suivant, qui elles deplacent volontairement le prix.

[Chapitre suivant : joinswap et exitswap, le depot et retrait a un seul actif](09-joinswap.md)
