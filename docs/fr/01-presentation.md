# Chapitre 1 — Presentation de Balancer v1

Balancer v1 generalise l'idee de teneur de marche automatise a produit constant popularisee par Uniswap : au lieu de deux actifs a poids egal (50/50), un pool Balancer accepte de deux a huit actifs, chacun avec son propre poids relatif librement choisi (par exemple 80/20, ou 50/30/20 sur trois actifs). Le prix et les swaps decoulent d'un invariant qui generalise le produit constant a des poids et un nombre d'actifs quelconques.

Ce depot correspond a la toute premiere generation du protocole (Balancer v1, parfois appele BCoW dans la communaute), architecturee autour d'un contrat `BPool` autonome par pool, deploye par une fabrique `BFactory` : chaque pool detient directement ses propres jetons, contrairement a l'architecture "Vault" centralisee introduite plus tard par Balancer v2. C'est cette version historique, plus simple a lire d'un seul tenant, que ce parcours documente.

Le depot d'origine, `balancer-labs/balancer-core`, a ete renomme suite a une reorganisation d'organisation GitHub et redirige automatiquement vers `balancer/balancer-core` ; il est archive en lecture seule par son proprietaire depuis fin aout 2026, ce qui en fait une reference stable et figee, ideale pour un parcours documentaire. Fichiers centraux : `contracts/BPool.sol` (logique du pool), `contracts/BMath.sol` (formules), `contracts/BNum.sol` (arithmetique en virgule fixe), `contracts/BFactory.sol` (fabrique), `contracts/BToken.sol` (jeton de part de pool).

Rien n'a ete installe, compile ni execute pour ecrire ces chapitres.

[Chapitre suivant : architecture BFactory et BPool](02-architecture.md)
