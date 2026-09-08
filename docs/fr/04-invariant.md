# Chapitre 4 — L invariant pondere generalise et le prix spot

Le produit constant `x * y = k` d'un pool a deux actifs de poids egaux se generalise, dans Balancer, en un produit pondere : la somme, sur tous les actifs, de leur solde eleve a la puissance de leur poids normalise reste constante entre deux swaps (`prod(balance_i ^ weight_i) = k`). Avec des poids egaux et deux actifs, cette formule se reduit exactement au produit constant d'Uniswap v2 (deja documente pour ce compte) : Uniswap v2 est donc un cas particulier de l'invariant Balancer.

`calcSpotPrice`, dans `BMath.sol`, exprime le prix instantane d'un actif en unites d'un autre comme le ratio de leurs soldes divises chacun par leur propre poids, `(balanceIn / weightIn) / (balanceOut / weightOut)`, ajuste par les frais de swap courants. Un actif dont le poids est plus eleve relativement aux autres a, a solde egal, un impact de prix moindre lors d'un swap — c'est le mecanisme meme qui permet a un pool 80/20 de se comporter, cote de l'actif majoritaire, presque comme une reserve stable plutot que comme un actif de trading a part entiere.

Ce commentaire mathematique en ASCII-art au-dessus de chaque fonction de `BMath.sol` documente directement la formule dans le code source : une pratique de documentation inhabituelle mais tres lisible, propre a ce depot.

[Chapitre suivant : calcOutGivenIn et le mecanisme de swap](05-swap.md)
