# Chapitre 12 — BToken : le jeton de part de pool (BPT)

`BToken.sol` implemente un ERC20 standard (transfert, allowance, evenements `Transfer`/`Approval`) pour representer les parts de chaque pool individuel : chaque `BPool` est lui-meme, via cet heritage, un jeton ERC20 nomme "Balancer Pool Token" (BPT). Detenir des BPT d'un pool donne droit, au prorata, a une part de tous les actifs qu'il contient, recuperable via `exitPool` (chapitre 8).

Les fonctions internes `_mintPoolShare`/`_burnPoolShare`/`_pushPoolShare`/`_pullPoolShare` de `BPool.sol` s'appuient directement sur les fonctions internes `_mint`/`_burn`/`_move` heritees de `BToken`, sans jamais passer par les fonctions publiques `transfer`/`transferFrom` habituelles : le contrat de pool agit directement sur son propre solde de jetons en tant que contrat, un motif possible uniquement parce que `BPool` est lui-meme le contrat du jeton BPT plutot qu'un simple detenteur d'un jeton externe.

Le nom et le symbole du jeton BPT sont fixes globalement (`NAME`, `SYMBOL` en constantes dans `BToken.sol`) et identiques pour tous les pools Balancer v1 : contrairement a un jeton ERC20 classique, aucune information sur les actifs sous-jacents ou leurs poids n'apparait dans le nom du jeton lui-meme, seule l'adresse du contrat de pool permet de les distinguer.

[Chapitre suivant : limites et perimetre](13-limites-et-perimetre.md)
