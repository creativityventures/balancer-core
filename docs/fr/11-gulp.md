# Chapitre 11 — gulp et les frais collectes par la fabrique

`gulp` resynchronise le solde interne enregistre pour un actif (`_records[token].balance`) avec le solde reel detenu par le contrat (`IERC20(token).balanceOf(address(this))`). Si quelqu'un envoie des jetons directement au pool par un transfert externe plutot que via `joinPool`, ce solde reste invisible aux formules de prix et de swap tant que `gulp` n'a pas ete appelee : cette fonction, ouverte a n'importe qui, permet d'absorber volontairement ces jetons "egares" dans la comptabilite active du pool, au benefice de tous les detenteurs de parts existants.

Les frais de swap eux-memes (chapitre 5) restent entierement dans le pool et profitent proportionnellement a tous les detenteurs de parts, sans prelevement direct par la fabrique. Le seul canal de revenu pour `BFactory` est indirect : un pool peut choisir d'envoyer une partie de ses parts de pool nouvellement frappees a l'adresse de la fabrique (comme le fait `rebind` avec `EXIT_FEE`, ici nul), que `BFactory.collect` permet ensuite au detenteur de `_blabs` de reclamer.

`setBLabs`, reserve a l'actuel titulaire de `_blabs`, permet de transferer ce role de collecte des frais de protocole vers une nouvelle adresse — un motif de propriete simple en une seule etape, sans confirmation en deux temps contrairement au motif "propose puis confirme" deja rencontre dans d'autres parcours de ce compte.

[Chapitre suivant : BToken, le jeton de part de pool](12-btoken.md)
