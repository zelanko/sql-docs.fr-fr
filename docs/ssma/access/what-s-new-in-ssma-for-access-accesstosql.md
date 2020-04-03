---
title: Quoi de neuf dans la SSMA pour l’accès (AccessToSQL) Microsoft Docs
authors: HJToland3;nahk-ivanov
ms.prod: sql
ms.custom: ''
ms.date: 4/2/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: a24d3fc0-6911-4bfa-828a-197abf222e02
ms.author: jtoland;alexiva
ms.openlocfilehash: 2fd3da31e6a635a65f3d2a2f75320dd0586159d9
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625583"
---
# <a name="whats-new-in-ssma-for-access-accesstosql"></a>Quoi de neuf dans la SSMA pour l’accès (AccessToSQL)

Cet article répertorie SQL Server Migration Assistant (SSMA) pour les modifications d’accès dans chaque version.

## <a name="ssma-v88"></a>SSMA v8.8

La version v8.8 de SSMA for Access comprend :

* SQL Server objets améliorations de stabilité de synchronisation
* Amélioration du rendement de l’interface graphique lors de l’évaluation et de la conversion
* Un tout nouveau parser syntaxe Access pour améliorer encore les performances de conversion

## <a name="ssma-v87"></a>SSMA v8.7

La version v8.7 de SSMA for `IIF` Access a amélioré la conversion pour la fonction dans les requêtes, ainsi que des correctifs mineurs et des améliorations des performances dans l’interface utilisateur graphique.

> [!IMPORTANT]
> Avec SSMA v8.5 et plus tard, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v86"></a>SSMA v8.6

En plus d’un ensemble ciblé de correctifs conçus pour améliorer la convivialité et les performances, la version v8.6 de SSMA pour l’accès a été améliorée en ajoutant un paramètre qui permet aux utilisateurs d’omettre les propriétés étendues SSMA dans le code converti.

Pour tirer parti de ce paramètre, dans SSMA pour l’accès, naviguer vers **Tools** > **Project Settings** > **General** > **Conversion**, puis sous **Misc**, mettre à jour la valeur de **l’Omit Extended Properties** réglage à **Oui**.

![Omettre le cadre des propriétés étendues](../access/media/ssma-omit-extended-properties.png)

> [!IMPORTANT]
> Avec SSMA v8.5 et plus tard, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v85"></a>SSMA v8.5

La version v8.5 de SSMA for Access est renforcée par le support de l’authentification Azure Active Directory et le support de base pour les fonctionnalités JSON dans le serveur SQL, ainsi qu’un ensemble ciblé de correctifs conçus pour améliorer la convivialité et les performances.

En outre, SSMA pour Access prend désormais`ISNULL`en `IIF`charge la conversion de multiples fonctions standard (, , etc.).

> [!IMPORTANT]
> Avec SSMA v8.5, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v84"></a>SSMA v8.4

La version v8.4 de SSMA for Access est enrichie de correctifs ciblés conçus pour résoudre les problèmes d’accessibilité et corriger un bogue lié aux colonnes d’index max (pour permettre 32 au lieu de 16) pour SQL Server 2016 et les versions ultérieures.

> [!IMPORTANT]
> Avec les versions SSMA 7.4 bien que 8.4, .NET 4.5.2 est une installation pré-requis.

## <a name="ssma-v83"></a>SSMA v8.3

La version v8.3 de SSMA for Access est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion. En outre, cette version de SSMA for Access fournit des correctifs qui :

* Aborder les questions d’accessibilité.
* Ajoutez une `hierarchyid` prise en charge de base pour le type dans SQL Server.

## <a name="ssma-v82"></a>SSMA v8.2

La version v8.2 de SSMA for Access est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion.

> [!NOTE]
> Un problème connu avec l’auto-mise à jour peut causer l’échec d’une mise à jour de SSMA v8.1 à v8.2. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

## <a name="ssma-v81"></a>SSMA v8.1

La version v8.1 de SSMA for Access est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion.

> [!NOTE]
> Un problème connu avec l’auto-mise à jour peut causer l’échec d’une mise à jour de SSMA v8.0 à v8.1. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

## <a name="ssma-v80"></a>SSMA v8.0

La version v8.0 de SSMA for Access est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion. Cette version offre également les nouvelles fonctionnalités suivantes :

* Prise en charge de **l’instance gérée par la base de données Azure SQL** comme cible. Vous pouvez désormais créer de nouveaux projets ciblant Azure SQL Database Managed Instance :

  ![Projet SQL DB MI](../media/ssma-newproject-sqldbmi.png)

* Conseiller **Fix**post-conversion . En savoir plus à ce sujet [ici](https://techcommunity.microsoft.com/t5/Microsoft-Data-Migration/Accelerate-your-Oracle-migrations-with-new-machine-learning/ba-p/368733).

* Sélection préliminaire de base de données/schémas.

    Lors de la connexion à la source, l’utilisateur peut désormais sélectionner des bases de données/schémas d’intérêt. Sélectionner uniquement les schémas que vous prévoyez de migrer permettra de gagner du temps pendant la connexion initiale et d’améliorer les performances globales de la SSMA.

   ![Objets filtreS SSMA](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

La version v7.10 de SSMA for Access est enrichie de correctifs ciblés conçus pour fournir des protections supplémentaires en matière de sécurité et de protection de la vie privée afin de répondre aux changements apportés aux exigences mondiales.

## <a name="ssma-v79"></a>SSMA v7.9

La version v7.9 de SSMA for Access contient les modifications suivantes :

* Des correctifs ciblés qui améliorent la qualité et les mesures de conversion.
* Soutien à la ligne de commande SSMA pour modifier la cartographie de type de données et les préférences de projet.
* Le dialogue de connexion de base de données Azure SQL dans SSMA a également été modifié pour spécifier le nom du serveur entièrement qualifié. Dans les versions précédentes de la SSMA, le préfixe azure SQL Database devait être explicitement mentionné à l’intérieur des paramètres des projets.

## <a name="ssma-v78"></a>SSMA v7.8

La version v7.8 de SSMA for Access contient les modifications suivantes :

* Modifier la cartographie de type mise en évidence dans les paramètres du projet.
* La possibilité pour les utilisateurs de désactiver la télémétrie.

## <a name="ssma-v77"></a>SSMA v7.7

La version v7.7 de SSMA for Access contient les modifications suivantes :

* Des correctifs ciblés qui améliorent la qualité et les mesures de conversion.
* Sur la base de la demande populaire, la version 32 bits de SSMA pour l’accès est de retour. Par rapport à la mise en œuvre précédente (avant v7.4), il ya deux paquets d’installateur, mais ils ne peuvent pas être installés côte à côte. Par conséquent, vous devez choisir la version la plus appropriée en fonction des composants de connectivité que vous avez. Il est toujours préférable d’utiliser la version 64 bits, si possible.

## <a name="ssma-v76"></a>SSMA v7.6

La version v7.6 de SSMA for Access est enrichie de correctifs ciblés qui améliorent la qualité et les mesures de conversion et avec la prise en charge de SQL Server 2017 (aperçu public). Le support pour SQL Server 2017 sur Windows et Linux est en avant-première publique et ne devrait pas être utilisé pour les migrations de production.

## <a name="ssma-v75"></a>SSMA v7.5

La version v7.5 de la SSMA pour l’accès est améliorée avec plusieurs améliorations afin d’assurer une plus grande accessibilité pour les personnes handicapées.

## <a name="ssma-v74"></a>SSMA v7.4

La version v7.4 de SSMA for Access contient les modifications suivantes :

* **L’option de temps d’arrêt De requête** est maintenant disponible lors de la découverte d’objets schématiques à la source et à la cible.

  ![option de délai d’attente de requête](../media/query-timeout_red.png)

* La mesure de qualité et de conversion a été améliorée grâce à des correctifs ciblés, basés sur la rétroaction des clients.

  > [!IMPORTANT]
  > .NET 4.5.2 est un pré-requis pour l’installation de SSMA v7.4. En outre, à partir de v7.4, la version 32 bits de SSMA a été abandonnée.

## <a name="ssma-v73"></a>SSMA v7.3

La version v7.3 de SSMA for Access contient les modifications suivantes :

* Amélioration de la qualité et de la mesure de conversion grâce à des correctifs ciblés basés sur la rétroaction des clients.
* Cadre d’extéabilité SSMA exposé via les éléments suivants :
  * Fonctionnalité d’exportation vers un projet SQL Server Data Tools (SSDT).
    * Vous pouvez maintenant exporter des scripts de schémas de SSMA vers un projet SSDT. Vous pouvez utiliser les scripts schéma pour apporter d’autres modifications de schéma et déployer votre base de données.

        ![Enregistrer comme commande de projet SSDT](../media/export-schema-scripts_red.png)
  * Bibliothèques qui peuvent être consommées par SSMA pour effectuer des conversions personnalisées.
    * Vous pouvez maintenant construire du code qui peut gérer les conversions et conversions syntaxes personnalisées qui n’ont pas été précédemment traitées par SSMA.
      * Des instructions sur la façon de construire un convertisseur personnalisé, ainsi qu’un projet d’exemple de conversion, sont disponibles dans le billet de blog [Extension SQL Server Migration Assistant’s conversion capabilities](https://techcommunity.microsoft.com/t5/Microsoft-Data-Migration/Extending-SQL-Server-Migration-Assistant-s-conversion/ba-p/1004181).

## <a name="ssma-v72"></a>SSMA v7.2

La version v7.2 de SSMA for Access contient les modifications suivantes :

* Amélioration de la qualité et de la mesure de conversion grâce à des correctifs ciblés basés sur la rétroaction des clients.
* Améliorations de la télémétrie pour fournir de meilleurs points de données pour résoudre les problèmes des clients et améliorer les taux de conversion de SSMA.

## <a name="ssma-v71"></a>SSMA v7.1

La version v7.1 de SSMA for Access contient les modifications suivantes :

* SQL Server 2017 sur Windows et Linux CTP1 est maintenant une plate-forme cible prise en charge pour la migration. Cette fonctionnalité est en aperçu technique et prend en charge le schéma et le mouvement des données pour cibler les serveurs SQL.
* SSMA prend désormais en charge les mises à jour automatiques pour télécharger la dernière version de SSMA dès qu’elle est disponible.
* Les binaires installables SSMA sont maintenant livrés via les fichiers de paquets Windows Installer (.msi).

## <a name="may-2016"></a>Mai 2016

La sortie en mai 2016 de SSMA for Access contient les changements suivants :

* Ajout d’un soutien officiel pour SQL Server 2016.
* Vérification de l’installateur supprimé pour .NET 2.0.
* Fixe `save-project` `open-project` et commandes pour console SSMA.
* Commande `securepassword` fixe pour console SSMA.
* Comptage fixe des objets pour le chargement initial.
* Chargement de données de tables fixes pour les onglets d’interface utilisateur pour l’accès.
* Bug fixe dans les paramètres globaux.

## <a name="march-2016"></a>Mars 2016

La sortie préliminaire de mars 2016 de SSMA for Access ajoute un soutien à la migration vers SQL Server 2016.

## <a name="january-2016"></a>Janvier 2016

La version de maintenance de janvier 2016 de SSMA for Access contient les modifications suivantes :

* Fonction invalide fixe pour défaut d’un champ GUID (RFC 3894811).
* Accrochez-vous fixe à l’importation de documents à SQL Database (Azure) (RFC 4919573).
* Ajout de l’élément de menu de journal de vue à SSMA (RFC 5706203).
* Ajout de la télémétrie.

## <a name="july-2014"></a>Juillet 2014

La sortie en juillet 2014 de SSMA for Access contient les changements suivants :

* Amélioration de la conversion du code Azure SQL DB.
* Déplacer la fonctionnalité du pack d’extension au schéma pour prendre en charge Azure SQL DB.
* Améliorations de performances testées pour les bases de données avec plus de 10k objets.
* Ajout d’améliorations de l’interface utilisateur pour traiter un grand nombre d’objets.
* Ajout d’un support pour mettre en évidence les schémas LOB « bien connus » (afin qu’ils puissent être ignorés dans la conversion).
* Amélioration de la vitesse de conversion ajoutée.
* Ajout d’une prise en charge pour afficher le nombre d’objets dans l’interface utilisateur.
* Réduction de la taille du rapport de plus de 25 %.
* Messages d’erreur améliorés pour les constructions non apprables.

## <a name="april-2014"></a>Avril 2014

La sortie en avril 2014 de SSMA for Access contient les changements suivants :

* Ajout d’un support pour MS SQL Server 2014.
* Bugs fixes liés à la conversion à Azure.
* Bugs fixes liés aux pages de rapport invisibles dans IE 10.

## <a name="january-2012"></a>janvier 2012

La sortie en janvier 2012 de SSMA for Access contient les changements suivants :

* A fourni la possibilité de ne pas persister le nom d’utilisateur et le mot de passe pour les tables liées à MS Access après la migration.
* Définissez des actions en cascade pour des références circulaires à No Action.
* Les messages appropriés indiquant des actions en cascade pour les références circulaires ont été réglés à Aucune action.

## <a name="july-2011"></a>juillet 2011

La publication en juillet 2011 de la SSMA pour l’accès ajoute une amélioration des rapports d’erreurs pendant la migration des données.

## <a name="april-2011"></a>Avril 2011

La sortie en avril 2011 de SSMA for Access contient les changements suivants :

* Ajout d’un seul installable de "SSMA for Access", qui prend en charge [!INCLUDE [ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE [ssSQL10](../../includes/sssql10-md.md)], [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)] et Azure SQL.
* Ajouté la capacité [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)]de se connecter à .
* Ajout de SSMA pour le support de la version Access Console pour la compatibilité vers l’arrière. Vous pouvez ouvrir les projets créés par des versions antérieures à SSMA v5.0.
* Ajouté la possibilité d’installer SSMA v5.0 produit côte à côte (SxS) avec des versions plus anciennes du produit SSMA.

## <a name="july-2010"></a>Juillet 2010

La sortie en juillet 2010 de SSMA for Access contient les changements suivants :

* Ajout d’un support pour la migration vers SQL Server 2008 R2 et Azure SQL.
* Ajout d’une connexion sécurisée à SQL Server et Azure SQL.
* Ajout d’une prise en charge des bases de données Access 2010.
* Ajout d’une nouvelle application SSMA Console pour l’exécution de la ligne de commande.
* Ajout d’une prise `DateTime2` en charge du type de données SQL Server.

## <a name="june-2008"></a>Juin 2008

La publication en juin 2008 de SSMA for Access ajoute un soutien aux bases de données Access 2007.

## <a name="may-2007"></a>Mai 2007

La sortie en mai 2007 de SSMA for Access contient les changements suivants :

* Ajout d’un soutien supplémentaire pour les bases de données Access qui utilisent les stratégies de groupe de travail.
* A fourni la possibilité de supprimer les objets convertis de l’explorateur de métadonnées SQL Server.
* Ajout d’une prise en charge des commentaires entrants par l’utilisateur dans le mode SQL Server formaté SQL.
* Améliorations ajoutées de la conversion d’objets.

## <a name="november-2006"></a>Novembre 2006

La sortie en novembre 2006 de SSMA for Access contient les changements suivants :

* Ajout d’un nouvel assistant de migration de base de [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)]données qui vous guide à travers la migration d’une base de données unique de l’accès à .
* Ajout d’une nouvelle commande Convert, Load et Migrate qui convertit [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)]les bases de [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)] données d’accès, charge les objets convertis en , et migre les données en une seule étape.
* Amélioration de la migration des requêtes. La migration de requête convertit maintenant plus de requêtes SELECT en vues. Pour plus d’informations, voir [Convertir les objets de base de données d’accès](converting-access-database-objects-accesstosql.md).
* Ajout de la possibilité d’éditer des propriétés de table et d’index sur l’onglet [!INCLUDE [ssNoVersion](../../includes/ssnoversion-md.md)] **Table.**
* Ajout de nouveaux paramètres globaux :
  * Vous pouvez choisir de montrer les numéros de ligne dans les fenêtres de l’éditeur.
  * Vous pouvez configurer SSMA pour inciter à remplacer les objets en double, ou toujours ou ne jamais remplacer les objets en double lors de la conversion de schémas.
* Ajout d’une nouvelle option de conversion qui vous permet de spécifier si SSMA affiche un avertissement lorsqu’une requête complexe contient une wildcard.

## <a name="july-2006"></a>En juillet 2006

La sortie en juillet 2006 de SSMA for Access a été la version initiale.
