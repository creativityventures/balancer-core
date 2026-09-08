# Chapitre 2 — Architecture : une fabrique BFactory, un contrat BPool par pool

`BFactory.newBPool` deploie un nouveau contrat `BPool` independant a chaque creation de pool et designe automatiquement l'appelant comme son `_controller` initial. Chaque `BPool` est donc un contrat autonome qui detient directement les jetons sous-jacents de ses actifs constitutifs, a l'oppose du "Vault" partage entre tous les pools qu'introduira Balancer v2 : cette version v1 privilegie l'isolation complete entre pools plutot que la mutualisation de la garde des actifs.

Un pool traverse deux etats. A sa creation, il est **non finalise** : seul le `_controller` peut appeler `bind`/`rebind`/`unbind` pour composer librement les actifs et leurs poids, et le pool n'est pas encore ouvert aux echanges publics. Apres `finalize` (chapitre 10), le pool devient permanent : plus aucun actif ne peut etre ajoute, retire ou repondere, et les echanges deviennent ouverts a tous.

`BFactory` conserve egalement une adresse `_blabs` ("Balancer Labs"), habilitee a collecter les parts de pool (`BPT`) que certains pools envoient a la fabrique elle-meme en guise de frais de protocole — un mecanisme separe des frais de swap (chapitre 6), controle au niveau de la fabrique plutot que pool par pool.

[Chapitre suivant : bind, rebind et unbind](03-bind.md)
