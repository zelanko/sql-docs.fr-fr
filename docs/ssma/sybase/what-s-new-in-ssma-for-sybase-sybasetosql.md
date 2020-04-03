---
title: Nouveautés dans la SSMA pour SAP ASE (SybaseToSQL) Microsoft Docs
authors: HJToland3;nahk-ivanov
ms.prod: sql
ms.custom: ''
ms.date: 4/2/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2be0cf8d-6dbe-443a-abbd-036249922205
ms.author: jtoland;alexiva
ms.openlocfilehash: 7f23c7e1c676b4ade42b43cf963e0fa6956f93c6
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625586"
---
# <a name="whats-new-in-ssma-for-sap-ase-sybasetosql"></a>Nouveautés en SSMA pour SAP ASE (SybaseToSQL)

Cet article répertorie SQL Server Migration Assistant (SSMA) pour LES modifications DE SAP ASE (anciennement SSMA pour Sybase) dans chaque version.

## <a name="ssma-v88"></a>SSMA v8.8

La version v8.8 de SSMA pour SAP ASE comprend :

* SQL Server objets améliorations de stabilité de synchronisation
* Amélioration du rendement de l’interface graphique lors de l’évaluation et de la conversion
* Correction du problème avec les caractères manquants dans les définitions SQL pour les objets

## <a name="ssma-v87"></a>SSMA v8.7

La version v8.7 de SSMA pour SAP ASE a des correctifs mineurs et des améliorations de performances dans l’interface utilisateur graphique.

> [!IMPORTANT]
> Avec SSMA v8.5 et plus tard, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v86"></a>SSMA v8.6

En plus d’un ensemble ciblé de correctifs conçus pour améliorer la convivialité et les performances, la version v8.6 de SSMA pour SAP ASE a été améliorée par l’ajout d’un paramètre qui permet aux utilisateurs d’omettre les propriétés étendues SSMA dans le code converti.

Pour tirer parti de ce paramètre, dans SSMA pour SAP ASE, naviguez vers **Tools** > **Project Settings** > **General** > **Conversion**, puis sous **Misc**, mettre à jour la valeur du **paramètre Omit Extended Properties** à **Yes**.

![Omettre le cadre des propriétés étendues](../sybase/media/ssma-omit-extended-properties.png)

> [!IMPORTANT]
> Avec SSMA v8.5 et plus tard, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v85"></a>SSMA v8.5

La version v8.5 de SSMA pour SAP ASE est renforcée par le support de l’authentification Azure Active Directory et le support de base pour les fonctionnalités JSON dans le serveur SQL, ainsi qu’un ensemble ciblé de correctifs conçus pour améliorer la convivialité et les performances.

En outre, SSMA pour SAP ASE vous permet désormais de masquer les tables et les vues du système (les exclure de la conversion).

> [!IMPORTANT]
> Avec SSMA v8.5, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v84"></a>SSMA v8.4

La version v8.4 de SSMA pour SAP ASE est enrichie de correctifs ciblés conçus pour résoudre les problèmes d’accessibilité et corriger un bogue lié aux colonnes d’index max (pour permettre 32 au lieu de 16) pour SQL Server 2016 et les versions ultérieures.

> [!IMPORTANT]
> Avec les versions SSMA 7.4 à 8.4, .NET 4.5.2 est une installation pré-requise.

## <a name="ssma-v83"></a>SSMA v8.3

La version v8.3 de SSMA pour SAP ASE est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion. En outre, cette version de SSMA pour SAP ASE fournit des correctifs qui:

* Résoudre les problèmes d’accessibilité
* Ajouter une `hierarchyid` prise en charge de base pour le type dans SQL Server

## <a name="ssma-v82"></a>SSMA v8.2

La version v8.2 de SSMA pour SAP ASE est enrichie d’un ensemble ciblé de correctifs conçus pour améliorer les mesures de qualité et de conversion, ainsi que des correctifs pour :

* Un problème avec les indices non groupés désactivés après la migration des données.
* Détection du cadre .NET lors de l’installation silencieuse.
* Un plantage intermittent qui se produit lorsqu’une nouvelle version est téléchargée.

> [!NOTE]
> Un problème connu avec l’auto-mise à jour peut causer l’échec d’une mise à jour de SSMA v8.1 à v8.2. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

## <a name="ssma-v81"></a>SSMA v8.1

La version v8.1 de SSMA pour SAP ASE est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion.

> [!NOTE]
> Un problème connu avec l’auto-mise à jour peut causer l’échec d’une mise à jour de SSMA v8.0 à v8.1. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

## <a name="ssma-v80"></a>SSMA v8.0

La version v8.0 de SSMA pour SAP ASE est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion. En outre, cette version offre les nouvelles fonctionnalités suivantes:

* Prise en charge de **l’instance gérée par la base de données Azure SQL** comme cible. Vous pouvez désormais créer de nouveaux projets ciblant Azure SQL Database Managed Instance :

  ![Projet SQL DB MI](../media/ssma-newproject-sqldbmi.png)

* Conseiller **Fix**post-conversion . En savoir plus à ce sujet [ici](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Sélection préliminaire de base de données/schémas.

  Lors de la connexion à la source, l’utilisateur peut désormais sélectionner des bases de données/schémas d’intérêt. Sélectionner uniquement les schémas que vous prévoyez de migrer permettra de gagner du temps pendant la connexion initiale et d’améliorer les performances globales de la SSMA.

  ![Objets filtreS SSMA](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

La version v7.10 de SSMA pour SAP ASE est enrichie de correctifs ciblés conçus pour fournir des protections supplémentaires en matière de sécurité et de confidentialité afin de répondre aux changements dans les exigences mondiales.

## <a name="ssma-v79"></a>SSMA v7.9

La version v7.9 de SSMA pour SAP ASE contient les modifications suivantes :

* Des correctifs ciblés qui améliorent la qualité et les mesures de conversion.
* Soutien à la ligne de commande SSMA pour modifier la cartographie de type de données et les préférences de projet.
* Prise en charge des données de migration à l’aide des Services d’intégration des serveurs SQL (SSIS). Après avoir converti le schéma, il est possible de créer un package SSIS en utilisant une option de menu contextuelle à clic droit.
* Le dialogue de connexion de base de données Azure SQL dans SSMA a également été modifié pour spécifier le nom du serveur entièrement qualifié. Dans les versions précédentes de la SSMA, le préfixe azure SQL Database devait être explicitement mentionné à l’intérieur des paramètres des projets.

## <a name="ssma-v78"></a>SSMA v7.8

La version v7.8 de SSMA pour SAP ASE contient les modifications suivantes :

* Modifier la cartographie de type mise en évidence dans **les paramètres du projet**.
* La possibilité pour les utilisateurs de désactiver la télémétrie.

## <a name="ssma-v77"></a>SSMA v7.7

La version v7.7 de SSMA pour SAP ASE contient les modifications suivantes :

* SSMA pour SAP ASE a été amélioré avec des correctifs ciblés qui améliorent la qualité et les mesures de conversion.
* Sur la base de la demande populaire, la version 32 bits de SSMA pour SAP ASE est de retour. Par rapport à la mise en œuvre précédente (avant à v7.4), il ya deux paquets d’installateur, mais ils ne peuvent pas être installés côte à côte. Par conséquent, vous devez choisir la version la plus appropriée en fonction des composants de connectivité que vous avez. Il est toujours préférable d’utiliser la version 64 bits, si possible.

## <a name="ssma-v76"></a>SSMA v7.6

La version v7.6 de SSMA pour SAP ASE contient les modifications suivantes :

* Corrections ciblées qui améliorent les mesures de qualité et de conversion et avec prise en charge de SQL Server 2017 (aperçu public). Le support pour SQL Server 2017 sur Windows et Linux est en avant-première publique et ne devrait pas être utilisé pour les migrations de production.
* Prise en charge de la conversion des fonctions Sybase.

## <a name="ssma-v75"></a>SSMA v7.5

La version v7.5 de SSMA pour SAP ASE (anciennement SSMA pour Sybase) contient les changements suivants :

* Plusieurs améliorations visant à assurer une plus grande accessibilité pour les personnes handicapées.
* Soutien `CREATE OR REPLACE` à la syntaxe.

## <a name="ssma-v74"></a>SSMA v7.4

La version v7.4 de SSMA pour Sybase contient les modifications suivantes :

* **L’option de temps d’arrêt De requête** est maintenant disponible lors de la découverte d’objets schématiques à la source et à la cible.

  ![option de délai d’attente de requête](../media/query-timeout_red.png)
* La mesure de qualité et de conversion a été améliorée grâce à des correctifs ciblés, basés sur la rétroaction des clients.

  > [!IMPORTANT]
  > .NET 4.5.2 est un pré-requis pour l’installation de SSMA v7.4. En outre, à partir de v7.4, la version 32 bits de SSMA est en cours d’arrêt.

## <a name="ssma-v73"></a>SSMA v7.3

La version v7.3 de SSMA pour Sybase contient les modifications suivantes :

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

La version v7.2 de SSMA pour Sybase contient les modifications suivantes :

* Amélioration de la qualité et de la mesure de conversion grâce à des correctifs ciblés basés sur la rétroaction des clients.
* Améliorations de la télémétrie pour fournir de meilleurs points de données pour résoudre les problèmes des clients et améliorer les taux de conversion de SSMA.

## <a name="ssma-v71"></a>SSMA v7.1

La version v7.1 de SSMA pour Sybase contient les modifications suivantes :

* SQL Server 2017 sur Windows et Linux CTP1 est maintenant une plate-forme cible prise en charge pour la migration. Cette fonctionnalité est en aperçu technique et prend en charge le schéma et le mouvement des données pour cibler les serveurs SQL.
* Prendre en charge les mises à jour automatiques pour télécharger la dernière version de SSMA dès qu’elle est disponible.
* Les binaires installables SSMA sont maintenant livrés via les fichiers de paquets Windows Installer (.msi).

## <a name="may-2016"></a>Mai 2016

La sortie en mai 2016 de SSMA pour Sybase contient les changements suivants :

* Ajout d’un support pour SQL Server 2016.
* Vérification de l’installateur supprimé pour .NET 2.0.
* Mise à jour Extension Pack dépendance de .NET 3.5 à .NET 4.0.
* Fixe `save-project` `open-project` et commandes pour console SSMA.
* Commande `securepassword` fixe pour console SSMA.
* Comptage fixe des objets pour le chargement initial.
* Bug fixe dans les paramètres globaux.

## <a name="march-2016"></a>Mars 2016

La sortie en avant-première de SSMA pour Sybase en mars 2016 ajoute un soutien à la migration vers SQL Server 2016.

## <a name="january-2016"></a>Janvier 2016

La version de maintenance de janvier 2016 de SSMA pour Sybase contient les modifications suivantes :

* Ajout de l’élément de menu de journal de vue à SSMA (RFC 5706203).
* Ajout de la télémétrie.

## <a name="july-2014"></a>Juillet 2014

La sortie en juillet 2014 de SSMA pour Sybase contient les changements suivants :

* Amélioration de la conversion du code Azure SQL DB.
* Déplacer la fonctionnalité du pack d’extension au schéma pour prendre en charge Azure SQL DB.
* Ajout d’améliorations de performance testées pour les bases de données avec plus de 10k objets.
* Ajout d’améliorations de l’interface utilisateur pour traiter un grand nombre d’objets.
* Ajouté la capacité de mettre en évidence bien connu des schémas LOB (afin qu’ils puissent être ignorés dans la conversion).
* Amélioration de la vitesse de conversion ajoutée.
* Ajouté la capacité de montrer le nombre d’objets dans l’interface utilisateur.
* Réduction de la taille du rapport de plus de 25 %.
* Messages d’erreur améliorés pour les constructions non apprables.

## <a name="april-2014"></a>Avril 2014

La sortie en avril 2014 de SSMA pour Sybase contient les changements suivants :

* Ajout d’un soutien de MS SQL Server 2014.
* Bugs fixes concernant la conversion à Azure.
* Bugs fixes concernant les pages de rapport invisibles dans IE 10.

## <a name="january-2012"></a>janvier 2012

La sortie en janvier 2012 de SSMA pour Sybase contient les changements suivants :

* Ajout d’un support pour la conversion de déclenchement de recul.
* Correction fournie pour `@@ROWCOUNT` `@@ERROR` la conversion `SET` et dans la même déclaration.

## <a name="july-2011"></a>juillet 2011

La publication en juillet 2011 de la SSMA pour Sybase permet d’améliorer les rapports d’erreurs pendant la migration des données.

## <a name="april-2011"></a>Avril 2011

La sortie en avril 2011 de SSMA pour Sybase contient les changements suivants :

* Produit consolidé "SSMA for Sybase", [!INCLUDE [ssSQL10](../../includes/sssql10-md.md)] [!INCLUDE [ssSQL11](../../includes/ssSQL11-md.md)] qui prend en charge [!INCLUDE [ssVersion2005](../../includes/ssversion2005-md.md)], et Azure SQL.
* Ajout d’un support pour [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)]se connecter et migrer vers .
* Ajout d’une nouvelle fonctionnalité pour convertir et migrer les bases de données Sybase en Azure SQL.
* Amélioration du moteur de migration des données côté client, à l’appui de la migration parallèle des données.
* Amélioration des performances de migration des données grâce à des modèles de récupération connectés Simple et Bulk.
* Ajout de la capacité de convertir et de migrer correctement les bases de données Sybase sensibles aux cas en sqL Server sensible aux cas.
* Le soutien supplémentaire pour la conversion des déclarations de jointure Sybase ASE ASE Non-ANSI aux déclarations de jointure SQL Server ANSI a été étendu aux déclarations DE DELETE et UPDATE.
* Fournir des options de connectivité supplémentaires pour se connecter aux serveurs Sybase ASE en utilisant Sybase ASE ODBC fournisseur et Sybase ASE fournisseurs de ADO.NET.
* Supprimé la dépendance à une `SysDB`base de données séparée appelée , qui contient les fonctions d’émulation Sybase (installé dans le cadre de l’extension Pack).
* Ajouté la possibilité d’installer SSMA pour [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)] Sybase Extension Pack sur les clusters.
* Ajout de la compatibilité rétrograde des projets créés par les versions antérieures de SSMA (v4.0 et v4.2).
* Ajouté la possibilité d’installer le SSMA pour Sybase v5.0 produit côte à côte (SxS) avec des versions plus anciennes de SSMA (v4.0 et v4.2).

## <a name="july-2010"></a>Juillet 2010

La sortie en juillet 2010 de SSMA pour Sybase a ajouté :

* Prise en charge de la migration vers SQL Server 2008 R2.
* Une nouvelle application SSMA Console pour l’exécution de la ligne de commande.
* Prise en charge de la migration des données à l’aide de moteurs de migration de données côté serveur et côté client.
* Prise en charge de l’énoncé « Custom SELECT » dans la migration des données.
* Soutien à la migration de Sybase ASE 15.0.3 et 15.5.

## <a name="june-2008"></a>Juin 2008

La sortie en juin 2008 de SSMA pour Sybase contient les changements suivants :

* Ajout de SSMA Tester, qui teste automatiquement la conversion de l’objet de base de données et la migration de données effectuée par SSMA. Une fois toutes les étapes de migration SSMA terminées, utilisez SSMA Tester pour vérifier que les objets convertis fonctionnent de la même manière et que toutes les données ont été transférées correctement.
* Ajout de la conversion pré-SQL. L’utilisateur peut désormais spécifier des déclarations temporaires de table (et d’autres objets) pour chaque procédure source à utiliser dans la conversion.
* Améliorations ajoutées de la conversion d’objets :
  * Joint la conversion révisée.
  * Agrégats et non-agrégats sans avoir/groupe par clauses.
  * La `IDENTITY` fonction `SELECT INTO` avec une déclaration.
  * Contraintes et index groupés sur les données uniquement verrouillées.
  * Tables temporaires `SELECT INTO`créées par .
  * Contraintes / Index pour les tables temporaires.
  * Les [!INCLUDE [ssSQL10](../../includes/sssql10-md.md)] nouveaux types d’heure de rendez-vous sont pris en charge.
  * Sybase 15.0 connectivité et type de données de soutien.

## <a name="may-2007"></a>Mai 2007

La sortie en mai 2007 de SSMA pour Sybase a ajouté:

* La possibilité de charger le contenu de base de données plus rapidement lors de l’enregistrement d’un projet.
* Prise en charge des commentaires entrants par l’utilisateur en mode SQL Server formaté SQL.
* Améliorations de la conversion d’objets.

## <a name="november-2006"></a>Novembre 2006

La sortie en novembre 2006 de SSMA pour Sybase contient les changements suivants :

* Ajout de nouveaux paramètres globaux :
  * Vous pouvez choisir de montrer les numéros de ligne dans les fenêtres de l’éditeur.
  * Vous pouvez configurer SSMA pour inciter à remplacer les objets en double, ou toujours ou ne jamais remplacer les objets en double lors de la conversion de schémas.
* Ajout d’une nouvelle option de conversion qui vous permet de configurer la façon dont SSMA gère les situations suivantes :
  * A `CAST` `CONVERT` ou une déclaration qui contient une chaîne binaire.
  * Vérifications des valeurs nulles dans les expressions d’égalité.
  * Tables proxy.
  * Numéros d’erreur de message d’utilisateur pour `RAISERROR`.
  * `UPDATE`déclarations contenant des identifiants non résolus.
* Ajout d’une nouvelle option de migration qui vous permet de [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)] spécifier comment SSMA doit gérer les dates qui sont en dehors de la plage de date.
* Ajout **d’un** paramètre SQL formaté sur l’onglet **SQL,** qui formate le code pour améliorer la lisibilité.
* Corrections de bogues, y compris :
  * SSMA convertit `LOCK TABLE <table> IN { SHARED | EXCLUSIVE } MODE` maintenant les `TABLOCK` `TABLOCKX` déclarations en `SELECT` ajoutant un ou un indice à la requête suivante sur la table.
  * Les moulages nécessaires sont maintenant ajoutés lorsque les types binaires sont utilisés dans les expressions de caractère.
  * Amélioration de la mémoire et des performances.

## <a name="july-2006"></a>En juillet 2006

La version de juillet 2006 de SSMA pour Sybase était la version initiale.

## <a name="see-also"></a>Voir aussi

[Démarrage avec SSMA pour Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)
