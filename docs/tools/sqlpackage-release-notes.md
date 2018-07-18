---
title: Notes de publication Microsoft DacFx & sqlpackage | Microsoft Docs
description: Notes de publication Microsoft sqlpackage
ms.custom: tools|sos
ms.date: 06/20/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sqlpackage
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: 7d05ec161b89e548cf529bc82c6d714a1960fb0f
ms.sourcegitcommit: 0dff9dd43e80eee900eb92d25df9ca18397f3485
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37080150"
---
# <a name="sqlpackage-release-notes"></a>notes de publication de Sqlpackage

**[Télécharger la version la plus récente](sqlpackage-download.md)**

## <a name="sqlpackage-178"></a>sqlpackage 17.8

Date de publication : 22 juin 2018  
Build : 14.0.4079.2  

La version inclut les correctifs suivants :

- Amélioration des messages d’erreur pour les échecs de connexion, y compris le message d’exception SqlClient.
- Ajout MaxParallelism du paramètre de ligne de commande pour spécifier le degré de parallélisme pour les opérations de base de données.
- Prend en charge la compression des index sur les index de partition unique pour l’importation/exportation.
- Correction d’un problème d’ingénierie inverse pour les jeux de colonnes XML avec SQL 2017 et versions ultérieures.
- Correction d’un problème où le niveau de compatibilité de base de données 140 de script a été ignoré pour la base de données SQL Azure.

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

## <a name="sqlpackage-on-macos-and-linux-001-preview"></a>Sqlpackage sur macOS et Linux 0.0.1 (version préliminaire)

Date de publication : 9 mai 2018  
Build : 15.0.4057.1

Cette version contient la version préliminaire d’inter-plateformes de sqlpackage qui cible .NET Core 2.0 et peut s’exécuter sur macOS et Linux. 

Cette version est une version préliminaire avec les problèmes connus suivants :

- Le paramètre /p:CommandTimeout est difficile à 120.
- Les contributeurs de génération et de déploiement ne sont pas pris en charge.
  - Doit être corrigée après le passage à .NET Core 2.1 où System.ComponentModel.Composition.dll est pris en charge.
  - Nécessité de gérer les chemins d’accès de la casse.
- Types SQL CLR UDT ne sont pas pris en charge, y compris les Types d’UDT CLR SQL Server : SqlGeography, SqlGeometry & SqlHierarchyId.
- Fichiers .dacpac et .bacpac plus anciens qui utilisent la sérialisation des données json ne sont pas pris en charge.
- .Dacpacs référencé (par exemple master.dacpac) ne peut pas résoudre en raison de problèmes avec les systèmes de fichiers respectant la casse.
  - Une solution de contournement consiste à mettre en majuscule le nom du fichier de référence (par exemple le serveur maître. BACPAC).