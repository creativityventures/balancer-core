# Parcours francais de Balancer v1 — Swap / AMM

Lecture commentee du teneur de marche automatise a poids ponderes Balancer v1, en francais, un mecanisme par chapitre.
Aucun code n'a ete installe, compile ni execute : ce parcours est purement documentaire.

1. [Presentation de Balancer v1](01-presentation.md)
2. [Architecture : une fabrique BFactory, un contrat BPool par pool](02-architecture.md)
3. [bind, rebind et unbind : composer un pool avant sa finalisation](03-bind.md)
4. [L invariant pondere generalise et le prix spot](04-invariant.md)
5. [calcOutGivenIn / calcInGivenOut : la formule de swap a poids arbitraires](05-swap.md)
6. [swapExactAmountIn, swapExactAmountOut et les ratios limites anti-manipulation](06-swapexact.md)
7. [BNum : l arithmetique en virgule fixe et l exponentiation fractionnaire](07-bnum.md)
8. [joinPool et exitPool : deposer et retirer proportionnellement a tous les actifs](08-joinexit.md)
9. [joinswap et exitswap : deposer ou retirer un seul actif](09-joinswap.md)
10. [finalize : transformer un pool prive en marche public et permanent](10-finalize.md)
11. [gulp et les frais collectes par la fabrique](11-gulp.md)
12. [BToken : le jeton de part de pool (BPT)](12-btoken.md)
13. [Limites connues et perimetre de ce parcours](13-limites-et-perimetre.md)
