# Sécurité des cycles de vie {#quickstart:440ada84-6adb-4acc-94be-5d9f42a71ec3}

## Objectifs {#quickstart:8b745aaa-bfd5-4f2d-885c-f6aa27d82a7b}

* Mettre en place les autorisations de transition,
* Mettre en place les profils par étape.

## Cadre {#quickstart:1b96d939-42fb-434a-9379-08d8c7e365a6}

Lors de la phase d'analyse, les points suivants ont été relevés :

* Cycle de vie des audits : Seul les utilisateurs suivant peuvent effectuer les transitions :
    * Démarrer : Responsable de l'audit et auditeurs,
    * Renvoyer en planification : Responsable de l'audit,
    * Annuler l'audit : Responsable de l'audit,
    * Accorder la certification :  Responsable de l'audit et auditeurs,
    * Refuser la certification : Responsable de l'audit.

* Fiche d'audit :
    - Brouillon :
        + Voir : Tous les utilisateurs,
        + Modifier : Rôle auditeur,
        + Supprimer : Personne,
    + Annulé :
        + Voir : Tous les utilisateurs,
        + Modifier : Personne,
        + Supprimer : Personne,
    + Planifié :
        + Voir : Tous les utilisateurs,
        + Modifier : Rôle auditeur,
        + Supprimer : Personne,
    + Certifié :
        + Voir : Tous les utilisateurs,
        + Modifier : Personne,
        + Supprimer : Personne,
    + Refusé :
        + Voir : Tous les utilisateurs,
        + Modifier : Personne,
        + Supprimer : Personne,

## Théorie {#quickstart:8a31ac4f-7f7c-4d51-bc95-261272893958}

Le paramétrage des droits associés à un cycle de vie sont de deux natures.

* Les droits associés aux transitions. Ces droits permettent de définir quel type d'utilisateur peut franchir quelle transition,
* Des profil associés au document lors des changement d'étape, ces profils permettent de définir qui peut voir, modifier, supprimer le document.

## Profilage du cycle {#quickstart:bba49d4c-8ea4-4cd3-a064-f8c006c9ef1c}

Vous allez commencer par profiler le document cycle de vie, ce qui va vous permettre de définir quel type d'utilisateur peut effectuer quelle transition.

Connectez vous à l'interface d'administration : `http://<nomDeDomaine>/admin.php`.

Allez dans l'application `Gestion des documents > Explorateur de documents` cliquez ensuite sur `les cycles` et sélectionnez le cycle `Audit Audit`.

Cliquez sur `Autres > Sécurité > Profil dédié`, la page se recharge, cliquez sur `Autres > Sécurité > Accessibilités...`.

La fenêtre ci-dessous s'ouvre :

![ Cycle de vie : Audit : Profil ](40-40-wdoc-profil-empty.png "Cycle de vie : Audit : Profil")

<span class="flag inline nota-bene"></span> Les deux premières et la dernière colonnes sont dédiées aux droits associés au document cycle (qui peut voir, modifier et voir les droits du document cycle).

<span class="flag inline nota-bene"></span> Le code couleur des types de droits peut être consulté en cliquant sur le bouton `Légende`.

<span class="flag inline nota-bene"></span> Les entrées en jaune et en orange sont des champs provenant du document associé au cycle de vie.

<span class="flag inline nota-bene"></span> L'affectation de droit est décrite dans [le chapitre sécurité des documents][ParamDroit].

Modifiez la matrice comme ci-dessous :

![ Cycle de vie : Audit : Profil ](40-40-wdoc-profil-checked.png "Cycle de vie : Audit : Profil")

Et cliquez sur `Modifier les privilèges`.

Votre cycle est maintenant profilé. La liste des transitions présentée sur le document tient compte du profil de la personne connectée.

## Profil des étapes {#quickstart:99be7d83-d8c0-407f-894a-b44e1df6bfa4}

Vous allez maintenant ajouter des profils de document au différentes étapes.

### Création des profils {#quickstart:88533bb0-692a-4d4e-a61d-d5fbc29a4e78}

Vous allez commencer par créer les profils. 

#### Profil : Brouillon {#quickstart:30ab6e0d-632d-4011-a546-dbac1c9b76fe}

Cliquez sur `Création > Profil`. Remplissez les valeurs suivantes :

* **Titre** : `Audit WFL : Brouillon`,
* **Famille** : `Audit`.

Cliquez sur `Créer`.

Cliquez sur `Activer`. La page se recharge. Cliquez sur `Accessibilités`

Remplissez la matrice comme-ci dessous :

![ Profil Audit : Brouillon ](40-40-pdoc-brouillon.png "Profil Audit : Brouillon")

Cliquez sur `Modifier les privilèges`.

Ajoutez le nom logique `Autres > Propriétés` : `PDOC_AUDIT_BROUILLON`.

#### Profil : Planifié {#quickstart:7589a8f6-4975-431a-94b9-cf0d879bc127}

Cliquez sur `Création > Profil`. Remplissez les valeurs suivantes :

* **Titre** : `Audit WFL : Planifié`,
* **Famille** : `Audit`.

Cliquez sur `Créer`.

Cliquez sur `Activer`. La page se recharge. Cliquez sur `Accessibilités`.

Remplissez la matrice comme-ci dessous :

![ Profil Audit : Planifié ](40-40-pdoc-brouillon.png "Profil Audit : Planifié")

Cliquez sur `Modifier les privilèges`.

Ajoutez le nom logique `Autres > Propriétés` : `PDOC_AUDIT_PLANIFIE`.

#### Profil : Désactivé {#quickstart:24afdcf5-a615-4ede-a14f-437847d12fe6}

Cliquez sur `Création > Profil`. Remplissez les valeurs suivantes :

* **Titre** : `Audit WFL : Désactivé`,
* **Famille** : `Audit`.

Cliquez sur `Créer`.

Cliquez sur `Activer`. La page se recharge. Cliquez sur `Accessibilités`.

Remplissez la matrice comme-ci dessous :

![ Profil Audit : Désactivé ](40-40-pdoc-disabled.png "Profil Audit : Désactivé")

Cliquez sur `Modifier les privilèges`.

Ajoutez le nom logique `Autres > Propriétés` : `PDOC_AUDIT_DISABLED`.

<span class="flag inline nota-bene"></span> Pour tous les états où le document (Annulé, Certifié, Refusé) est désactivé, un seul profil est créé et utilisé pour tous ces états.

### Affectation des profils {#quickstart:24184161-6f14-4cde-bfaf-9868a84657fe}

Allez dans l'application `Gestion des documents > Explorateur de documents` cliquez ensuite sur `les cycles` et sélectionnez le cycle `Audit Audit`.

Cliquez sur `Modifier`, sélectionnez l'onglet `Étapes` pour chaque onglet d'étape associé le profil :

* Profil Brouillon : Audit WFL Brouillon,
* Profil Planifié : Audit WFL Planifié,
* Profil Annulé : Audit WFL Désactivé,
* Profil Certifié : Audit WFL Désactivé,
* Profil Refusé : Audit WFL Désactivé,

Vous obtenez le document suivant :

![ Cycle de vie ](40-40-pdoc-wdoc-associated.png "Cycle de vie")

<span class="flag inline nota-bene"></span> **Attention** les profils ne sont affectés au document qu'à l'arrivée dans l'étape, si des documents sont déjà dans cette étape alors le profil n'est pas affecté.

## Exportation {#quickstart:5d73ab75-ffa4-4509-8efc-32b3073bcfea}

Utilisez la procédure décrite dans le [chapitre précédent][ExportCycle].

Vous devez obtenir un fichier `./COGIP_AUDIT/COGIP_AUDIT_AUDIT__PARAM.csv` semblable à :

![ Export cycle de vie avec sécurité ](40-40-security-param.png "Export cycle de vie avec sécurité")

## Conclusion {#quickstart:c4e5ebfa-74b7-4565-819d-34537af6317e}

Vous savez maintenant paramétrer les éléments de sécurité associés au cycle de vie. Vous pouvez définir qui peut effectuer quelle transition et qui peut voir/modifier/supprimer les documents suivant l'étape.

## Voir aussi {#quickstart:44b393d1-c6ad-448b-997d-e9cc1d47fd89}

* [Import profil cycle de vie][DocCSVWFL],
* [Profil de document][DocProfilDocument].

<!-- links -->

[DocProfilDocument]: https://docs.anakeen.com/dynacase/3.2/dynacase-doc-core-reference/website/book/core-ref:a99dcc5f-f42f-4574-bbfa-d7bb0573c95d.html#core-ref:f1575705-10e8-4bf2-83b3-4c0b5bfb77cf "Documentation : profil de document"
[DocCSVWFL]: https://docs.anakeen.com/dynacase/3.2/dynacase-doc-core-reference/website/book/core-ref:e0d99925-df0d-4d51-8ebc-d44c4dd03873.html#core-ref:e0d99925-df0d-4d51-8ebc-d44c4dd03873 "Documentation : Import cycle de vie"
[ParamDroit]: #quickstart:1cd2c714-d287-4ca6-8282-c5a20393c0ea
[ExportCycle]: #quickstart:6633ab3c-ab35-48ad-93a9-71898bfad9f3