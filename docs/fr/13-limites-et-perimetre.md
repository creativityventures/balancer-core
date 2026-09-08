# Chapitre 13 — Limites connues et perimetre de ce parcours

Ce depot, `balancer-core`, correspond exclusivement a la version 1 du protocole (parfois appelee "Balancer v1" ou son coeur "BCoW"), archivee et figee par son proprietaire. L'architecture "Vault" de Balancer v2 (un contrat unique de garde partage entre tous les pools, des types de pools additionnels comme les pools stables ou les pools geres, et un systeme de gestion d'actifs externe) n'existe pas dans ce depot et n'est donc pas couverte par ce parcours ; elle vit dans un depot distinct (`balancer/balancer-v2-monorepo`).

Ce parcours ne couvre pas en detail le dossier `test/` (suite de tests JavaScript), les scripts de migration Truffle (`migrations/`), ni les details de l'outillage d'audit (`.circleci/`, `echidna/`, le rapport Trail of Bits inclus dans le depot sous forme de PDF). Le contrat `BColor.sol`, qui ne definit qu'une chaine de caracteres de "couleur" pour l'affichage des logs de deploiement, n'a aucun role fonctionnel et n'est pas detaille non plus.

Rien n'a ete installe, compile, deploye ni execute pour ecrire ces chapitres. Aucun test n'a ete lance ; ces chapitres decrivent ce que le code Solidity dit faire, en renvoyant aux fichiers cites. Le depot fournit sa propre suite de tests (dossier `test/`) pour verification independante.
