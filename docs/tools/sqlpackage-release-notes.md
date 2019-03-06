---
title: Notes de publication Microsoft DacFx & sqlpackage | Microsoft Docs
description: Notes de publication Microsoft sqlpackage
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: f9fe0558b169acea58bb98a4f9a07267549aa58f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56013000"
---
# <a name="sqlpackage-release-notes"></a>notes de publication de Sqlpackage

**[Télécharger la version la plus récente](sqlpackage-download.md)**

## <a name="sqlpackage-181"></a>sqlpackage 18.1

Date de publication : 1er février 2019  
Build : 15.0.4316.1 

La version inclut les correctifs et les fonctionnalités suivantes :

- Prise en charge pour les classements UTF-8.
- Correction des performances à utiliser l’estimateur de cardinalité héritée pour les requêtes ingénieries inverses.
- Activer les index columnstore non cluster sur des vues indexées.
- Correction d’un problème de performances de comparaison de schéma significatifs lors de la génération d’un script.
- Correction de la logique de détection de dérive du schéma afin d’ignorer certaines sessions xevent.
- Importation fixe de classement pour les tables de graphique.
- Correction d’exportation des tables externes avec les autorisations d’objet.
- Déplacé vers .NET Core 2.2 
- Utilisation du stockage de mémoire soutenue pour la comparaison de schémas sur .NET Core.

Cette version inclut les versions d’évaluation d’inter-plateformes de sqlpackage qui ciblent .NET Core 2.2 et peuvent s’exécuter sur macOS et Linux. Cette version préliminaire présente les problèmes connus suivants :

- Les contributeurs de génération et de déploiement ne sont pas pris en charge.
- Fichiers .dacpac et .bacpac plus anciens qui utilisent la sérialisation des données json ne sont pas pris en charge.
- .Dacpacs référencé (par exemple master.dacpac) ne peut pas résoudre en raison de problèmes avec les systèmes de fichiers respectant la casse.
  - Une solution de contournement consiste à mettre en majuscule le nom du fichier de référence (par exemple le serveur maître. BACPAC).
## <a name="sqlpackage-180"></a>sqlpackage 18.0

Date de publication : 24 octobre 2018  
Build : 15.0.4200.1 

La version inclut les correctifs et les fonctionnalités suivantes :

- Prise en charge ajoutée pour le niveau de compatibilité de base de données 150.
- Prise en charge pour les Instances gérées.
- Ajout MaxParallelism du paramètre de ligne de commande pour spécifier le degré de parallélisme pour les opérations de base de données.
- Ajouter un paramètre de ligne de commande de AccessToken pour spécifier un jeton d’authentification lors de la connexion à SQL Server.
- Prise en charge de types de données d’objet BLOB/CLOB flux pour les importations.
- Prise en charge pour la fonction UDF scalaire option « INLINE ».
- Prise en charge ajoutée pour la syntaxe de 'MERGE' table graphique.
- Fixe non résolue pseudo-colonne pour les tables de graphique.
- Correction de la création d’une base de données avec un fichier optimisé en mémoire groupes de tables optimisées en mémoire sont utilisés.
- Fixe, y compris les propriétés étendues sur les tables externes.

## <a name="sqlpackage-178"></a>sqlpackage 17.8

Date de publication : 22 juin 2018  
Build : 14.0.4079.2  

La version inclut les correctifs suivants :

- Amélioration des messages d’erreur pour les échecs de connexion, y compris le message d’exception SqlClient.
- Prend en charge la compression des index sur les index de partition unique pour l’importation/exportation.
- Correction d’un problème d’ingénierie inverse pour les jeux de colonnes XML avec SQL 2017 et versions ultérieures.
- Correction du problème selon lequel les scripts du niveau de compatibilité de la base de données 140 étaient ignorés pour Azure SQL Database.

## <a name="sqlpackage-1741"></a>sqlpackage 17.4.1

Date de publication : 25 janvier 2018  
Build : 14.0.3917.1

La version inclut les correctifs suivants :

- Lorsque vous importez un .bacpac de la base de données SQL Azure à une instance sur site, correction des erreurs en raison de « les clés principales de base de données sans mot de passe ne sont pas pris en charge dans cette version de SQL Server ».
- Prise en charge du classement de catalogue de base de données.
- Correction d’une erreur de colonne pseudo non résolues pour les tables de graphique.
- Ajout ThreadMaxStackSize du paramètre de ligne de commande pour analyser TSQL avec un grand nombre d’instructions imbriquées.
- Correction à l’aide de la SchemaCompareDataModel avec l’authentification SQL pour comparer les schémas.

## <a name="sqlpackage-1740"></a>sqlpackage 17.4.0

Date de publication : 12 décembre 2017  
Build : 14.0.3881.1

La version inclut les correctifs suivants :

- Ne bloquez pas lors de la survenue d’un niveau de compatibilité de base de données non compris. Au lieu de cela, la dernière base de données Azure SQL ou de la plateforme de sur site sera considéré comme.
- Prise en charge ajoutée pour la stratégie de rétention temporelle sur SQL2017 + et base de données SQL Azure.
- Paramètre de ligne de commande ajouté /DiagnosticsFile:"C:\Temp\sqlpackage.log » pour spécifier un chemin d’accès de fichier pour enregistrer les informations de diagnostic.
- Paramètre de ligne de commande ajouté /Diagnostics pour consigner des informations de diagnostic dans la console.

