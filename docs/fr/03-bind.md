# Chapitre 3 — bind, rebind et unbind : composer un pool avant sa finalisation

`bind` enregistre un nouvel actif dans le pool (jusqu'a `MAX_BOUND_TOKENS` = 8 actifs simultanes) puis delegue immediatement a `rebind` pour fixer son solde initial et son poids. `rebind` peut aussi etre appele seule ensuite, tant que le pool n'est pas finalise, pour ajuster le solde ou le poids d'un actif deja lie : si le nouveau solde est superieur a l'ancien, le controleur doit fournir la difference (`_pullUnderlying`) ; s'il est inferieur, le controleur recupere l'excedent, moins un `EXIT_FEE` (fixe a zero dans cette version du code, `EXIT_FEE = 0` dans `BConst.sol`).

`unbind` retire completement un actif : elle utilise un motif classique de suppression en O(1) dans un tableau non ordonne, en copiant le dernier element du tableau `_tokens` a la place de l'element supprime avant de retirer le dernier emplacement (`_tokens.pop()`), plutot que de decaler tous les elements suivants.

Chaque poids (`denorm`, pour "poids denormalise") doit rester entre `MIN_WEIGHT` (1, soit 1×BONE) et `MAX_WEIGHT` (50×BONE), et la somme de tous les poids du pool (`_totalWeight`) ne doit jamais depasser `MAX_TOTAL_WEIGHT` (50×BONE) : ce sont ces poids denormalises, une fois divises par leur somme, qui donnent les poids relatifs normalises utilises par les formules de prix et de swap.

[Chapitre suivant : l invariant pondere et le prix spot](04-invariant.md)
