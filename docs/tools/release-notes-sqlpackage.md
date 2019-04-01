---
title: Notes de version de DacFx et SqlPackage | Microsoft Docs
description: Notes de publication pour Microsoft sqlpackage.
ms.custom: tools|sos
ms.date: 02/02/2019
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: de45add2b02686f990d68f7c1c23eec385848751
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538775"
---
# <a name="release-notes-for-sqlpackageexe"></a>Notes de version de SqlPackage.exe

**[Télécharger la version la plus récente](sqlpackage-download.md)**

Cet article répertorie les fonctionnalités et les correctifs fournis par les versions commerciales de SqlPackage.exe.

<!--
TODO:
The Introduction text needs to add clarity regarding the relationship between
'SqlPackage.exe' and 'DacFx' (the Microsoft 'Data-Tier Application Framework').
One added sentence would be sufficient.

Or, if there is no relationship, remove 'DacFx' from the metadata 'title:'.

I discussed this with SStein (SteveStein).
Thanks.  GeneMi (MightyPen in GitHub).  2019-03-27
-->

## <a name="181-sqlpackage"></a>SqlPackage 18.1

Date de publication : &nbsp; 1er février 2019  
Build : &nbsp; 15.0.4316.1  
La version préliminaire.

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Prise en charge pour les classements UTF-8. | &nbsp; |
| Activer les index columnstore non cluster sur une vue indexée. | &nbsp; |
| Déplacé vers .NET Core 2.2. | &nbsp; |
| Utilisation du stockage de mémoire soutenue pour la comparaison de schémas sur .NET Core. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Correction des performances à utiliser l’estimateur de cardinalité héritée pour les requêtes ingénieries inverses. | &nbsp; |
| Correction d’un problème de performances de comparaison de schéma significatifs lors de la génération d’un script. | &nbsp; |
| Correction de la logique de détection de dérive du schéma afin d’ignorer certaines sessions événements étendus (xevent). | &nbsp; |
| Importation fixe de classement pour les tables de graphique. | &nbsp; |
| Correction d’exportation des tables externes avec les autorisations d’objet. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus

Cette version inclut les versions d’évaluation d’inter-plateformes de sqlpackage qui ciblent .NET Core 2.2. Le sqlpackage peut s’exécuter sur macOS et Linux.

| Problème connu | Détails |
| :---------- | :------ |
| Les contributeurs de génération et de déploiement ne sont pas pris en charge. | &nbsp; |
| Fichiers .dacpac et .bacpac plus anciens qui utilisent la sérialisation des données json ne sont pas pris en charge. | &nbsp; |
| .Dacpacs référencé (par exemple master.dacpac) ne peut pas résoudre en raison de problèmes avec les systèmes de fichiers respectant la casse. | Une solution de contournement consiste à mettre en majuscule le nom du fichier de référence (par exemple le serveur maître. BACPAC). |
| &nbsp; | &nbsp; |

## <a name="180-sqlpackage"></a>SqlPackage 18.0

Date de publication : &nbsp; le 24 octobre 2018  
Build : &nbsp; 15.0.4200.1

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Prise en charge ajoutée pour le niveau de compatibilité de base de données 150. | &nbsp; |
| Prise en charge pour les Instances gérées. | &nbsp; |
| Ajout MaxParallelism du paramètre de ligne de commande pour spécifier le degré de parallélisme pour les opérations de base de données. | &nbsp; |
| Ajout AccessToken du paramètre de ligne de commande pour spécifier un jeton d’authentification lors de la connexion à SQL Server. | &nbsp; |
| Prise en charge de types de données d’objet BLOB/CLOB flux pour les importations. | &nbsp; |
| Prise en charge pour la fonction UDF scalaire option « INLINE ». | &nbsp; |
| Prise en charge ajoutée pour la syntaxe de 'MERGE' table graphique. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Fixe non résolue pseudo-colonne pour les tables de graphique. | &nbsp; |
| Correction de la création d’une base de données avec un fichier optimisé en mémoire groupes de tables optimisées en mémoire sont utilisés. | &nbsp; |
| Fixe, y compris les propriétés étendues sur les tables externes. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="178-sqlpackage"></a>SqlPackage 17.8

Date de publication : &nbsp; 22 juin 2018  
Build : &nbsp; 14.0.4079.2

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Amélioration des messages d’erreur pour les échecs de connexion, y compris le message d’exception SqlClient. | &nbsp; |
| Prend en charge la compression des index sur les index de partition unique pour l’importation/exportation. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Correction d’un problème d’ingénierie inverse pour les jeux de colonnes XML avec SQL 2017 et versions ultérieures. | &nbsp; |
| Correction du problème selon lequel les scripts du niveau de compatibilité de la base de données 140 étaient ignorés pour Azure SQL Database. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="1741-sqlpackage"></a>SqlPackage 17.4.1

Date de publication : &nbsp; 25 janvier 2018  
Build : &nbsp; 14.0.3917.1

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Paramètre de ligne de commande ajouté ThreadMaxStackSize analyse Transact-SQL avec un grand nombre d’instructions imbriquées. | &nbsp; |
| Prise en charge du classement de catalogue de base de données. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Lorsque vous importez un .bacpac de la base de données SQL Azure à une instance sur site, correction d’erreurs dues aux _clés principales de base de données sans mot de passe ne sont pas pris en charge dans cette version de SQL Server_. | &nbsp; |
| Correction d’une erreur de colonne pseudo non résolues pour les tables de graphique. | &nbsp; |
| Correction à l’aide de la SchemaCompareDataModel avec l’authentification SQL pour comparer les schémas. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="1740-sqlpackage"></a>SqlPackage 17.4.0

Date de publication : &nbsp; 12 décembre 2017  
Build : &nbsp; 14.0.3881.1

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Prise en charge pour _stratégie de rétention temporelle_ sur la base de données SQL Azure et SQL 2017 +. | &nbsp; |
| Paramètre de ligne de commande ajouté /DiagnosticsFile:"C:\Temp\sqlpackage.log » pour spécifier un chemin d’accès de fichier pour enregistrer les informations de diagnostic. | &nbsp; |
| Paramètre de ligne de commande ajouté /Diagnostics pour consigner des informations de diagnostic dans la console. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Ne bloquez pas lorsqu’il rencontre un niveau de compatibilité de base de données qui n’est pas compris. | Au lieu de cela, la dernière plateforme de base de données SQL Azure ou sur site sera considéré comme. |
| &nbsp; | &nbsp; |
