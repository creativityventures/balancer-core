# Chapitre 10 — finalize : transformer un pool prive en marche public et permanent

`finalize`, appelable une seule fois par le controleur, marque la transition irreversible d'un pool en cours de composition vers un pool public et fige. Elle exige au moins `MIN_BOUND_TOKENS` (2) actifs deja lies, bascule les deux drapeaux `_finalized` et `_publicSwap` a vrai, puis frappe et attribue au controleur l'offre initiale de parts de pool (`INIT_POOL_SUPPLY`, fixee a 100 jetons BPT quel que soit le nombre ou la valeur des actifs deposes — une convention arbitraire mais constante d'un pool a l'autre).

Une fois finalise, plus aucun appel a `bind`, `rebind` ou `unbind` n'est possible (chacune verifie explicitement `!_finalized`) : la composition du pool (quels actifs, quels poids) est geleee pour toujours. Seuls les soldes des actifs peuvent encore evoluer, via les swaps et les operations de depot/retrait des chapitres precedents, jamais leur liste ni leur ponderation relative.

Ce cycle de vie en deux temps — configuration privee par un controleur unique, puis ouverture permanente et sans permission — est une alternative plus simple a la gouvernance mutable de MakerDAO ou Aave deja documentee pour ce compte : Balancer v1 ne prevoit aucun mecanisme de reponderation ou de remplacement d'actif apres coup, la seule option etant de creer un nouveau pool entierement distinct.

[Chapitre suivant : gulp et les frais de la fabrique](11-gulp.md)
