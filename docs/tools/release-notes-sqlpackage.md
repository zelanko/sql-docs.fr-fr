---
title: Notes de version de DacFx et SqlPackage | Microsoft Docs
description: Notes de publication de Microsoft SqlPackage.
ms.custom: tools|sos
ms.date: 02/02/2019
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: ad2f4eaadfb2140facc5bebd8d1f70cf163d1380
ms.sourcegitcommit: 6413b7495313830ad1ae5aefe0c09e8e7a284b07
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2019
ms.locfileid: "71016878"
---
# <a name="release-notes-for-sqlpackageexe"></a>Notes de version de SqlPackage.exe

**[Télécharger la version la plus récente](sqlpackage-download.md)**

Cet article présente les fonctionnalités et les correctifs fournis par les versions commerciales de SqlPackage.exe.

<!--
TODO:
The Introduction text needs to add clarity regarding the relationship between
'SqlPackage.exe' and 'DacFx' (the Microsoft 'Data-Tier Application Framework').
One added sentence would be sufficient.

Or, if there is no relationship, remove 'DacFx' from the metadata 'title:'.

I discussed this with SStein (SteveStein).
Thanks.  GeneMi (MightyPen in GitHub).  2019-03-27
-->

## <a name="1831-sqlpackage"></a>SqlPackage 18.3.1

|Plateforme|Télécharger|Date de publication|Options de version|Build
|:---|:---|:---|:---|:---|
|Windows|[Programme d’installation MSI](https://go.microsoft.com/fwlink/?linkid=2102893)|13 septembre 2019|18.3.1|15.0.4538.1|
|macOS .NET Core (préversion)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2102894)|13 septembre 2019| 18.3.1|15.0.4538.1|
|Linux .NET Core (préversion)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2102978)|13 septembre 2019| 18.3.1|15.0.4538.1|
|Windows .NET Core (version préliminaire)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2102979)|13 septembre 2019| 18.13.1|15.0.4538.1|

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Azure SQL Data Warehouse (préversion) | Ajoutez la prise en charge pour le déploiement sur Azure SQL Data Warehouse. | 
| Déploiement | Ajoutez le paramètre/p : DatabaseLockTimeout = (INT32 « 60 ») à SqlPackage. | 
| Déploiement | Ajoutez le paramètre/p : LongRunningCommandTimeout = (INT32) à SqlPackage. |
| Exportation/extraction | Ajoutez le paramètre/p : TempDirectoryForTableData = (STRING) à SqlPackage. |
| Déploiement | Autoriser le chargement des contributeurs de déploiement à partir d’emplacements supplémentaires. Les contributeurs de déploiement sont chargés à partir du même répertoire que la cible. dacpac en cours de déploiement, le répertoire des extensions par rapport au fichier binaire SqlPackage. exe et le paramètre/p : AdditionalDeploymentContributorPaths = (STRING) ajouté à SqlPackage où les emplacements de répertoire supplémentaires peuvent être spécifiés. |
| Déploiement | Ajoutez la prise en charge de OPTIMIZE_FOR_SEQUENTIAL_KEY. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Déploiement | Correction pour ignorer les index automatiques afin qu’ils ne soient pas supprimés lors du déploiement. | 
| Always Encrypted | Correction de la gestion des colonnes Always Encrypted varchar. | 
| Génération et déploiement | Correctif pour résoudre la méthode nodes () pour les jeux de colonnes XML.| 
| ScriptDom | Corrigez les cas supplémentaires où la chaîne’URL’a été interprétée comme un jeton de niveau supérieur. | 
| Graphique | Correction du TSQL généré pour les références de pseudo-colonnes dans les contraintes.  | 
| Exporter | Générez des mots de passe aléatoires conformes aux exigences de complexité. | 
| Déploiement | Correctif pour honorer les délais d’attente de commande lors de la récupération de contraintes. | 
| .NET Core (version préliminaire) | Correction de la journalisation des diagnostics dans un fichier. | 
| .NET Core (version préliminaire) | Utilisez la diffusion en continu pour exporter des données de table afin de prendre en charge les tables volumineuses. | 
| &nbsp; | &nbsp; |

## <a name="182-sqlpackage"></a>SqlPackage 18.2

|Plateforme|Télécharger|Date de publication|Options de version|Build
|:---|:---|:---|:---|:---|
|Windows|[Programme d’installation MSI](https://go.microsoft.com/fwlink/?linkid=2087429)|15 avril 2019|18.2|15.0.4384.2|
|macOS .NET Core (préversion)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2087247)|15 avril 2019 | 18.2 |15.0.4384.2|
|Linux .NET Core (préversion)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2087431)|15 avril 2019 | 18.2 |15.0.4384.2|

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Ajout de la prise en charge des tables de graphe pour les contraintes de bord et les clauses de contrainte de bord. | &nbsp; |
| Activation de la règle de validation de modèle afin de prendre en charge 32 colonnes pour les clés d’index avec SQL Server 2016 et les versions ultérieures. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Correction par rétroconception d’une base de données SQL Server 2016 RTM en raison d’un indicateur de requête non pris en charge. | &nbsp; |
| Correction de l’ordre de déploiement des instructions AUTO CLOSE ALTER pour qu’elles se produisent avant les instructions CREATE FILEGROUP. | &nbsp; |
| Correction de la régression de l’analyse ScriptDom selon laquelle la chaîne « URL » était interprétée comme un jeton de niveau supérieur. | &nbsp; |
| Correction d’une exception de référence Null lors de l’analyse d’une instruction ALTER TABLE ADD INDEX. | &nbsp; |
| Correction de la comparaison de schéma des colonnes calculées persistantes Nullable qui s’affichent toujours comme différentes.| &nbsp; |
| &nbsp; | &nbsp; |

## <a name="181-sqlpackage"></a>SqlPackage 18.1

Date de publication : &nbsp; 1er février 2019  
Build : &nbsp; 15.0.4316.1  
Préversion.

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Ajout de la prise en charge des classements UTF-8. | &nbsp; |
| Activation des index columnstore non cluster sur une vue indexée. | &nbsp; |
| Déplacement vers .NET Core 2.2. | &nbsp; |
| Utilisation du stockage sur mémoire pour la comparaison de schémas sur .NET Core. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Correction des performances afin d’utiliser l’ancien estimateur de cardinalité pour les requêtes de rétroconception. | &nbsp; |
| Correction d’un problème important de performances de la comparaison de schéma lors de la génération d’un script. | &nbsp; |
| Correction de la logique de détection de dérive du schéma afin d’ignorer certaines sessions d’événements étendus (XEvent). | &nbsp; |
| Correction de l’ordre d’importation des tables de graphe. | &nbsp; |
| Correction de l’exportation de tables externes comportant des autorisations d’objet. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus

Cette version inclut les versions d’évaluation multiplateformes de SqlPackage qui ciblent .NET Core 2.2. SqlPackage peut s’exécuter sur macOS et Linux.

| Problème connu | Détails |
| :---------- | :------ |
| Les contributeurs de build et de déploiement ne sont pas pris en charge. | &nbsp; |
| Les anciens fichiers .dacpac et .bacpac qui utilisent la sérialisation de données JSON ne sont pas pris en charge. | &nbsp; |
| Il peut arriver que les .dacpac référencés (par exemple, master.dacpac) ne se résolvent pas en raison de problèmes avec les systèmes de fichiers sensibles à la casse. | Pour contourner le problème, il suffit de mettre en majuscules le nom du fichier de référence (par exemple, MASTER.BACPAC). |
| &nbsp; | &nbsp; |

## <a name="180-sqlpackage"></a>SqlPackage 18.0

Date de publication : &nbsp; 24 octobre 2018  
Build : &nbsp; 15.0.4200.1

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Ajout de la prise en charge du niveau 150 de compatibilité de base de données. | &nbsp; |
| Ajout de la prise en charge de Managed Instance. | &nbsp; |
| Ajout du paramètre de ligne de commande MaxParallelism pour spécifier le degré de parallélisme des opérations de base de données. | &nbsp; |
| Ajout du paramètre de ligne de commande AccessToken pour spécifier un jeton d’authentification lors de la connexion à SQL Server. | &nbsp; |
| Ajout de la prise en charge des flux de types de données BLOB/CLOB pour les importations. | &nbsp; |
| Ajout de la prise en charge de l’option « INLINE » des fonctions UDF scalaires. | &nbsp; |
| Ajout de la prise en charge de la syntaxe « MERGE » des tables de graphe. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Correction des pseudo-colonnes non résolues pour les tables de graphe. | &nbsp; |
| Correction de la création d’une base de données avec des groupes de fichiers à mémoire optimisée lorsque des tables à mémoire optimisée sont utilisées. | &nbsp; |
| Correction de l’intégration de propriétés étendues sur les tables externes. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="178-sqlpackage"></a>SqlPackage 17.8

Date de publication : &nbsp; 22 juin 2018  
Build : &nbsp; 14.0.4079.2

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Amélioration des messages d’erreur en cas d’échec de connexion, y compris le message d’exception SqlClient. | &nbsp; |
| Prise en charge de la compression des index à partition unique pour l’importation/exportation. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Correction d’un problème de rétroconception pour les jeux de colonnes XML avec SQL 2017 et les versions ultérieures. | &nbsp; |
| Correction du problème selon lequel les scripts du niveau de compatibilité de la base de données 140 étaient ignorés pour Azure SQL Database. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="1741-sqlpackage"></a>SqlPackage 17.4.1

Date de publication : &nbsp; 25 janvier 2018  
Build : &nbsp; 14.0.3917.1

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Ajout du paramètre de ligne de commande ThreadMaxStackSize pour analyser du code Transact-SQL comportant de nombreuses instructions imbriquées. | &nbsp; |
| Prise en charge du classement de catalogue de base de données. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Lors de l’importation d’un .bacpac Azure SQL Database dans une instance sur site, correction des erreurs liées au fait que _Les clés principales de base de données sans mot de passe ne sont pas prises en charge dans cette version de SQL Server_. | &nbsp; |
| Correction d’une erreur de pseudo-colonnes non résolue pour les tables de graphe. | &nbsp; |
| Correction de SchemaCompareDataModel avec l’authentification SQL pour comparer les schémas. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="1740-sqlpackage"></a>SqlPackage 17.4.0

Date de publication : &nbsp; 12 décembre 2017  
Build : &nbsp; 14.0.3881.1

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Ajout de la prise en charge de la _stratégie de rétention temporelle_ sur SQL 2017 et versions ultérieures et sur Azure SQL Database. | &nbsp; |
| Ajout du paramètre de ligne de commande /DiagnosticsFile:"C:\Temp\sqlpackage.log" pour spécifier un chemin de fichier permettant d’enregistrer les informations de diagnostic. | &nbsp; |
| Ajout du paramètre de ligne de commande /Diagnostics pour consigner les informations de diagnostic dans la console. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Suppression du blocage en cas de niveau de compatibilité de base de données non compris. | La dernière version de Azure SQL Database ou la dernière plateforme sur site sera présumée. |
| &nbsp; | &nbsp; |
