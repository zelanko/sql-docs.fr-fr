---
title: Quoi de neuf dans SSMA pour Oracle (OracleToSQL) Microsoft Docs
authors: HJToland3;nahk-ivanov
ms.prod: sql
ms.custom: ''
ms.date: 4/2/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f305ebb6-7393-4a43-abb3-6332b739d690
ms.author: jtoland;alexiva
ms.openlocfilehash: 88b87aad931f28637accc95aa4d993037fcf0b0a
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625596"
---
# <a name="whats-new-in-ssma-for-oracle-oracletosql"></a>Quoi de neuf dans SSMA pour Oracle (OracleToSQL)

Cet article répertorie SQL Server Migration Assistant (SSMA) pour les modifications d’Oracle dans chaque version.

## <a name="ssma-v88"></a>SSMA v8.8

La version v8.8 de SSMA pour Oracle comprend:

* SQL Server objets améliorations de stabilité de synchronisation
* Amélioration du rendement de l’interface graphique lors de l’évaluation et de la conversion
* Amélioration de `OVER PARTITION` la conversion des clauses analytiques
* Nouvelle conversion `LEAD` pour la fonction analytique
* Nouvelle conversion pour les clauses d’affacturage de sous-quier
* Nouvelle `REPLICATE` option de distribution pour Azure SQL Data Warehouse
* Un tout nouveau parser syntaxe Oracle pour améliorer encore les performances de conversion

## <a name="ssma-v87"></a>SSMA v8.7

La version v8.7 de SSMA pour Oracle a des correctifs mineurs et des améliorations de performances dans l’interface utilisateur graphique.

En outre, SSMA pour Oracle permet désormais de filtrer les objets basés sur l’état de validité dans le dialogue 'Advanced Object Selection'.

> [!IMPORTANT]
> Avec SSMA v8.5 et plus tard, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v86"></a>SSMA v8.6

En plus d’un ensemble ciblé de correctifs conçus pour améliorer la convivialité et les performances, la version v8.6 de SSMA pour Oracle a été améliorée par l’ajout d’un paramètre qui permet aux utilisateurs d’omettre les propriétés étendues SSMA dans le code converti.

Pour tirer parti de ce paramètre, dans SSMA pour Oracle, naviguez vers **Tools** > **Project Settings** > **General** > **Conversion**, puis sous **Misc**, mettre à jour la valeur de **l’Omit Extended Properties** setting à **Yes**.

![Omettre le cadre des propriétés étendues](../oracle/media/ssma-omit-extended-properties.png)

En outre, SSMA pour Oracle fournit maintenant `XMLTABLE` un analysement amélioré de la clause.

> [!IMPORTANT]
> Avec SSMA v8.5 et plus tard, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v85"></a>SSMA v8.5

La version v8.5 de SSMA pour Oracle est renforcée par le support de l’authentification Azure Active Directory et le support de base pour les fonctionnalités JSON dans le serveur SQL, ainsi qu’un ensemble ciblé de correctifs conçus pour améliorer la convivialité et les performances.

En outre, SSMA pour Oracle a été renforcée avec le soutien pour:

* Limiter le nombre d’objets sélectionnés à la découverte `WHERE .. IN (..)` à 990 (la limite de clause d’Oracle est de 1000 éléments).
* Migration des `RAW` `UNIQUEIDENTIFIER`données de .
* Parsing `PARALLEL_ENABLE` de la clause.

Enfin, la version v8.5 de SSMA pour Oracle fournit maintenant:

* Amélioration des performances des constantes emballées converties.
* Une mise à jour pour Oracle Data Provider pour .NET à la version 19.5.0.

> [!IMPORTANT]
> Avec SSMA v8.5, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v84"></a>SSMA v8.4

La version v8.4 de SSMA pour Oracle est enrichie de correctifs ciblés qui sont conçus pour résoudre les problèmes d’accessibilité et corriger un bogue lié aux colonnes d’index max (pour permettre 32 au lieu de 16) pour SQL Server 2016 et les versions ultérieures.

En outre, cette version de SSMA `SYS_REFCURSOR` pour `OUT` Oracle ajoute la conversion pour les paramètres de procédure stockés.

> [!IMPORTANT]
> Avec les versions SSMA 7.4 à 8.4, .NET 4.5.2 est une installation pré-requise.

## <a name="ssma-v83"></a>SSMA v8.3

La version v8.3 de SSMA pour Oracle est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion. En outre, cette version de SSMA pour Oracle fournit des correctifs qui:

* Aborder les questions d’accessibilité.
* Ajoutez une `hierarchyid` prise en charge de base pour le type dans SQL Server.
* Résoudre un problème avec un type de retour inconnu pour une fonction appelée par synonyme.
* Mise à jour ODP.NET à v19.3.

## <a name="ssma-v82"></a>SSMA v8.2

La version v8.2 de SSMA pour Oracle est améliorée à:

* Ajouter un `DBMS_OUTPUT.ENABLE` / `DISABLE`support pour .
* Supprimer `CAST AS FLOAT` `BINARY_FLOAT` et `BINARY_DOUBLE` supprimer les colonnes dans la requête de migration de données par défaut.
* Correction des séquences actualiser si la valeur actuelle a changé.
* Correction du bogue lié à une mauvaise`ROWNUM`interprétation des pseudo-colonnes (, etc.) si une colonne du même nom existe.
* Réparez un plantage qui se produit en convertissant des `FOR` boucles avec un identifiant ambigu non résolu.

En outre, cette version comprend un ensemble ciblé de correctifs conçus pour améliorer la qualité et les mesures de conversion, ainsi que des correctifs pour:

* Un problème avec les indices non groupés désactivés après la migration des données.
* Détection du cadre .NET lors de l’installation silencieuse.
* Un plantage intermittent qui se produit lorsqu’une nouvelle version est téléchargée.

> [!NOTE]
> Un problème connu avec l’auto-mise à jour peut causer l’échec d’une mise à jour de SSMA v8.1 à v8.2. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

## <a name="ssma-v81"></a>SSMA v8.1

La version v8.1 de SSMA pour Oracle est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion.

> [!NOTE]
> Un problème connu avec l’auto-mise à jour peut causer l’échec d’une mise à jour de SSMA v8.0 à v8.1. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

## <a name="ssma-v80"></a>SSMA v8.0

La version v8.0 de SSMA pour Oracle est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion. Cette version offre également les nouvelles fonctionnalités suivantes :

* Prise en charge de **l’instance gérée par la base de données Azure SQL** comme cible. Vous pouvez désormais créer de nouveaux projets ciblant Azure SQL Database Managed Instance :

  ![Projet SQL DB MI](../media/ssma-newproject-sqldbmi.png)

  > [!NOTE]
  > La SSMA pour Oracle Extension Pack a également été mise à jour pour permettre des installations à distance sur Azure SQL Database Managed Instance:
  >
  > ![SSMA pour Oracle Extension Pack](../media/ssma-oracle-ext-pack.png)

  Certaines fonctionnalités, y compris la migration de données côté testeur et serveur, ne sont pas prises en charge lorsqu’elles ciblent l’instance gérée par la base de données Azure SQL. Pour en savoir plus, cliquez [ici](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/migrate-your-oracle-database-to-azure-sql-database-managed-instance-using-ssma-8-0/).

* Conseiller **Fix**post-conversion . En savoir plus à ce sujet [ici](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Sélection préliminaire de base de données/schémas.

  Lors de la connexion à la source, l’utilisateur peut désormais sélectionner des bases de données/schémas d’intérêt. Sélectionner uniquement les schémas que vous prévoyez de migrer permettra de gagner du temps pendant la connexion initiale et d’améliorer les performances globales de la SSMA.

  ![Objets filtreS SSMA](../media/ssma-filter-objects.png)

* La possibilité d’utiliser le pilote officiel, géré .NET pour se connecter à Oracle. Le pilote OCI n’est plus une condition préalable à l’utilisation de SQL Server Migration Assistant pour Oracle.

* La possibilité `ROWID` de `UROWID` `VARCHAR` cartographier et de faire par défaut. Modifié `uniqueidentifier` pour tenir compte `ROWID` de la migration des données pour les colonnes explicites.

## <a name="ssma-v710"></a>SSMA v7.10

La version v7.10 de SSMA pour Oracle contient les modifications suivantes :

* Des correctifs ciblés conçus pour fournir des protections supplémentaires en matière de sécurité et de protection de la vie privée afin de répondre aux changements apportés aux exigences mondiales.
* Une amélioration de conversion liée aux requêtes hiérarchiques.

## <a name="ssma-v79"></a>SSMA v7.9

La version v7.9 de SSMA pour Oracle contient les modifications suivantes :

* Des correctifs ciblés qui améliorent la qualité et les mesures de conversion.
* Prise en charge des déclarations de migration "Continuer" d’Oracle à SQL Server.
* Soutien à la ligne de commande SSMA pour modifier la cartographie de type de données et les préférences de projet.
* Prise en charge des données de migration à l’aide des Services d’intégration des serveurs SQL (SSIS). Après avoir converti le schéma, il est possible de créer un package SSIS en utilisant une option de menu contextuelle à clic droit.
* Le dialogue de connexion de base de données Azure SQL dans SSMA a également été modifié pour spécifier le nom du serveur entièrement qualifié. Dans les versions précédentes de la SSMA, le préfixe azure SQL Database devait être explicitement mentionné à l’intérieur des paramètres des projets.

## <a name="ssma-v78"></a>SSMA v7.8

La version v7.8 de SSMA pour Oracle contient les modifications suivantes :

* Soutien à :
  * Expression de `IN` ligne pour la clause.
  * Moulages de type implicite.
  * `UID`conversion pour Azure SQL Database.
* Modifier la cartographie de type mise en évidence dans **les paramètres du projet**.
* La possibilité pour les utilisateurs de désactiver la télémétrie.

## <a name="ssma-v77"></a>SSMA v7.7

La version v7.7 de SSMA pour Oracle contient les modifications suivantes :

* SSMA pour Oracle a été amélioré avec des correctifs ciblés qui améliorent la qualité et les mesures de conversion.
* Sur la base de la demande populaire, la version 32 bits de SSMA pour Oracle est de retour. Par rapport à la mise en œuvre précédente (avant v7.4), il ya deux paquets d’installateur, mais ils ne peuvent pas être installés côte à côte. Par conséquent, vous devez choisir la version la plus appropriée en fonction des composants de connectivité que vous avez. Il est toujours préférable d’utiliser la version 64 bits, si possible.
* Le support SQL Server 2017 est désormais officiel avec le pack d’extension Oracle pris en charge sur Linux (nouvelle option d’installation à distance). Notez que la fonctionnalité Extension Pack est limitée lorsqu’elle est installée sur Linux, car les fonctionnalités de migration des données côté testeur et serveur ne sont pas prises en charge.
* SSMA pour Oracle vous permet de migrer Des vues matérialisées en tables régulières (configurable à travers les paramètres de la**synchronisation** ->  **des paramètres** -> du projet Découvrez les tables**d’accompagnement pour les vues matérialisées**).

## <a name="ssma-v76"></a>SSMA v7.6

La version v7.6 de SSMA pour Oracle est enrichie de correctifs ciblés qui améliorent la qualité et les mesures de conversion et avec la prise en charge de SQL Server 2017 (aperçu public). Le support pour SQL Server 2017 sur Windows et Linux est en avant-première publique et ne devrait pas être utilisé pour les migrations de production.

## <a name="ssma-v75"></a>SSMA v7.5

La version v7.5 de SSMA pour Oracle contient les modifications suivantes :

* Amélioration de plusieurs améliorations afin d’assurer une plus grande accessibilité pour les personnes handicapées.
* Mise à jour pour améliorer la qualité et la mesure de conversion avec des correctifs ciblés, tels que l’amélioration de la manipulation des types de données de date et de flottement pendant la migration des données, en fonction de la rétroaction des clients.

## <a name="ssma-v74"></a>SSMA v7.4

La version v7.4 de SSMA pour Oracle contient les modifications suivantes :

* SSMA pour Oracle prend désormais en charge Azure SQL Data Warehouse en tant que plate-forme cible pour la migration.

  ![Fenêtre Nouveau projet](../media/new-project.png)
  * Prend en charge les options de stockage data Warehouse telles qu’indiquées dans l’image suivante :

  ![options de stockage pour l’entrepôt de données](../media/storage-options_red.png)
  * Prend en charge les options de distribution de données telles qu’elles sont indiquées dans l’image suivante :

  ![distribution de données pour l’entrepôt de données](../media/data-distribution_red.png)

* **L’option de temps d’arrêt De requête** est maintenant disponible lors de la découverte d’objets schématiques à la source et à la cible.

  ![option de délai d’attente de requête](../media/query-timeout_red.png)

* La mesure de qualité et de conversion a été améliorée grâce à des correctifs ciblés, basés sur la rétroaction des clients.

> [!IMPORTANT]
> .NET 4.5.2 est un pré-requis pour l’installation de SSMA v7.4. En outre, à partir de v7.4, la version 32 bits de SSMA est en cours d’arrêt.

## <a name="ssma-v73"></a>SSMA v7.3

La version v7.3 de SSMA pour Oracle contient les modifications suivantes :

* Amélioration de la qualité et de la mesure de conversion grâce à des correctifs ciblés basés sur la rétroaction des clients.
* Cadre d’extéabilité SSMA exposé via les éléments suivants :
  * Fonctionnalité d’exportation vers un projet SQL Server Data Tools (SSDT).
    * Vous pouvez maintenant exporter des scripts de schémas de SSMA vers un projet SSDT. Vous pouvez utiliser les scripts schéma pour apporter d’autres modifications de schéma et déployer votre base de données.

      ![Enregistrer comme commande de projet SSDT](../media/export-schema-scripts_red.png)
  * Bibliothèques qui peuvent être consommées par SSMA pour effectuer des conversions personnalisées.
    * Vous pouvez maintenant construire du code qui peut gérer les conversions et conversions syntaxes personnalisées qui n’ont pas été précédemment traitées par SSMA.
      * Des instructions sur la façon de construire un convertisseur personnalisé sont disponibles dans ce billet de blog, [Extension des capacités de conversion de SQL Server Migration Assistant](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      * Téléchargez un exemple de projet de conversion à partir de ce billet de [blog](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

## <a name="ssma-v72"></a>SSMA v7.2

La version v7.2 de SSMA pour Oracle contient les modifications suivantes :

* Amélioration de la qualité et de la mesure de conversion grâce à des correctifs ciblés basés sur la rétroaction des clients.
* Améliorations de la télémétrie pour fournir de meilleurs points de données pour résoudre les problèmes des clients et améliorer les taux de conversion de SSMA.

## <a name="ssma-v71"></a>SSMA v7.1

La version v7.1 de SSMA pour Oracle contient les modifications suivantes :

* SQL Server 2017 sur Windows et Linux CTP1 est maintenant une plate-forme cible prise en charge pour la migration. Cette fonctionnalité est en aperçu technique et permet au schéma et au mouvement des données de cibler les serveurs SQL.
* SSMA prend désormais en charge les mises à jour automatiques pour télécharger la dernière version de SSMA dès qu’elle est disponible.
* Les binaires installables SSMA sont maintenant livrés via les fichiers de paquets Windows Installer (.msi).

## <a name="may-2016"></a>Mai 2016

La sortie en mai 2016 de SSMA pour Oracle contient les changements suivants :

* Ajout d’un support pour SQL Server 2016.
* Ajout de la conversion des tables d’archives de flashback Oracle en tables temporelles SQL Server.

  > [!NOTE]
  > SSMA ne copie pas les données historiques des tables Oracle Flashback Data Archive. Par conséquent, les données d’historique doivent être copiées manuellement pendant le processus de migration. De plus, bien que SSMA n’affiche pas la table d’histoire de l’explorateur de métadonnées SQL Server parce qu’elle est traitée comme une table système, vous pouvez voir la table d’histoire dans SQL Server Management Studio.
  >
  > SQL Server 2016 ne prend pas en charge plusieurs fonctionnalités d’Oracle Flashback, notamment :
  >
  >   * Oracle Flashback Transaction Requête
  >   * `DBMS_FLASHBACK`Paquet
  >   * Flashback Transaction
  >   * Archives de données Flashback
  >   * Flashback Table
  >   * Flashback Drop
  >   * Base de données Flashback

* Ajout de la conversion de la politique VPD Oracle en objets SQL Server Policy (Row Level Security pour Oracle).
* Diminution du temps de chargement initial pour Oracle.
* Analyse et résolveur améliorés.
* Vérification de l’installateur supprimé pour .NET 2.0.
* Mise à jour Extension Pack dépendance de .NET 3.5 à .NET 4.0.
* Fixe `save-project` `open-project` et commandes pour console SSMA.
* Commande `securepassword` fixe pour console SSMA.
* Comptage fixe des objets pour le chargement initial.
* Conversion fixe des types de données de caractère pour Oracle.
* Bug fixe dans les paramètres globaux.

## <a name="march-2016"></a>Mars 2016

La sortie en avant-première de mars 2016 de SSMA pour Oracle a ajouté un soutien pour :

* Migration vers SQL Server 2016.
* Migration de la sécurité de niveau Oracle Row (avec quelques limitations).
* Migrer Oracle dans des tables mémoire à SQL Server Column Store.

## <a name="january-2016"></a>Janvier 2016

La sortie de maintenance de janvier 2014 de SSMA pour Oracle contient les modifications suivantes :

* Ajout d’un support pour les indices groupés.
* Requêtes Oracle lentes fixes (RFC 5076207).
* Connexion fixe à Azure à partir de la console.
* Ajout de l’élément de menu de journal de vue à SSMA (RFC 5706203).
* Ajout de la télémétrie.

## <a name="july-2014"></a>Juillet 2014

La sortie en juillet 2014 de SSMA pour Oracle contient les changements suivants :

* Ajout d’un support pour Azure SQL DB.
* La fonctionnalité du pack d’extension s’est déplacée au schéma pour prendre en charge Azure SQL DB.
* Ajout d’un support pour les vues matérialisées Oracle.
* Ajout d’un support pour les tables optimisées pour SQL Server 2014 Memory.
* Inclus améliorations de performance testées pour les bases de données avec plus de 10k objets.
* Ajout d’améliorations de l’interface utilisateur pour traiter un grand nombre d’objets.
* Ajout d’une mise en évidence des schémas LOB bien connus.
* Améliorations incluses de la vitesse de conversion.
* Ajout d’une prise en charge pour afficher le nombre d’objets dans l’interface utilisateur.
* Réduction de la taille du rapport de plus de 25 %.
* Messages d’erreur améliorés pour les constructions non apprables.

## <a name="april-2014"></a>Avril 2014

La sortie en avril 2014 de SSMA pour Oracle contient les changements suivants :

* Ajout d’un soutien de MS SQL Server 2014.
* Ajout d’un support d’Oracle 12 et d’optimisation des requêtes.
* Bugs fixes concernant la conversion à Azure.
* Bugs fixes concernant les pages de rapport invisibles dans IE 10.

## <a name="january-2012"></a>janvier 2012

La sortie en janvier 2012 de SSMA pour Oracle ajoute un support et `RowType` `RecordType` des paramètres d’entrée par défaut à `NULL`.

## <a name="july-2011"></a>juillet 2011

La sortie en juillet 2011 de SSMA pour Oracle contient les changements suivants :

* Ajout d’un support [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)] pour la conversion de la séquence Oracle en générateur de séquences.
* Amélioration de la déclaration d’erreurs pendant la migration des données.
* Amélioration de la conversion de l’instruction à l’aide de mots réservés.
* Amélioration de la conversion implicite de la valeur de la date dans une fonction.

## <a name="april-2011"></a>Avril 2011

La sortie en avril 2011 de SSMA pour Oracle contient les changements suivants :

* Produit consolidé "SSMA pour Oracle", [!INCLUDE [ssSQL10](../../includes/sssql10-md.md)] [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)]qui prend en charge, [!INCLUDE [ssVersion2005](../../includes/ssversion2005-md.md)]et .
* Ajout d’un support pour [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)]se connecter et migrer vers .
* Amélioration du moteur de migration des données côté client, à l’appui de la migration parallèle des données.
* Amélioration des performances `Simple` `Bulk` de migration des données avec des modèles de récupération et d’enregistrement.
* Ajout d’un support pour la compatibilité vers l’arrière des projets créés par les versions antérieures de SSMA (v4.0 et v4.2).
* Ajouté la possibilité d’installer SSMA pour Oracle v5.0 produit côte à côte (SxS) avec des versions plus anciennes de SSMA (v4.0 et v4.2).
* Ajout d’une prise en charge pour `VARRAY`la `NESTED TABLE`communication des types définis par l’utilisateur (y compris le sous-type, , la table d’objet et la vue de l’objet) et leurs utilisations dans les blocs PL/SQL avec des messages d’erreur spéciaux.

## <a name="july-2010"></a>Juillet 2010

La sortie en juillet 2010 de SSMA pour Oracle a ajouté :

* Prise en charge de la migration vers SQL Server 2008 R2.
* Une nouvelle application SSMA Console pour l’exécution de la ligne de commande.
* Prise en charge de la migration des données à l’aide de moteurs de migration de données côté serveur et côté client.
* Prise en charge de l’énoncé « Custom SELECT » dans la migration des données.
* Soutien à la migration d’Oracle 11g R2.

## <a name="june-2008"></a>Juin 2008

La sortie en juin 2008 de SSMA pour Oracle contient les modifications suivantes :

* Ajout d’améliorations au rapport d’évaluation, y compris des renseignements supplémentaires pour les synonymes, une source brute pour les objets parsables, des panneaux et la suppression du logo SQL Server, et la persistance de la mise en page.
* Améliorations ajoutées de la conversion d’objets :
  * `DBMS_LOB`Paquets `DBMS_SQL` , conversion ajoutée.
  * Joint la conversion révisée.
  * Modification des collections et conversion des enregistrements, conversion des enregistrements dans des cas simples publiés via des variables distinctes pour chaque champ.
  * Amélioration de la mise en œuvre des dossiers et des collections.
  * Fonctions d’agrégation de fenêtre ajoutées.
  * `ROLLUP`/`CUBE`clause ajoutée.
  * Amélioration `NEXTVAL` / `CURVAL`pour .
  * Des colonnes `SET` regroupées en clause, des ensembles de regroupement et des pièces d’identité de regroupement ont été ajoutées.
  * `MERGE`déclaration ajoutée.
  * Prise en charge de nouveaux types d’heure de date et conversion des enregistrements et des collections comme les types de données CLR ajouté.
* Ajout de nouvelles fonctionnalités de Tester. Les tables peuvent maintenant être testées en tant qu’objets utilisant Tester, une commande d’appel de plusieurs objets testables dans le cas de test peut être modifiée, l’utilisateur peut tester les procédures et les fonctions avec des enregistrements et des collections comme paramètres et valeurs de retour, et un analyseur de dépendances a été ajouté pour vérifier uniquement les tables utilisées.
  
## <a name="august-2007"></a>En août 2007

La sortie en août 2007 de SSMA pour Oracle a ajouté:

* Un nouveau composant Tester vous permet de créer, de gérer et d’exécuter des cas de test pour vérifier le code SQL converti.
* Le support pour la conversion des sous-types Oracle, des collections et des modules locaux a été ajouté au convertisseur SQL.
* Une nouvelle fonction de synchronisation vous permet de synchroniser des objets spécifiques avec la base de données SQL Server.
* Nouvelles options de conversion.
  
## <a name="april-2007"></a>Avril 2007

La sortie en avril 2007 de SSMA pour Oracle a été la version initiale.
