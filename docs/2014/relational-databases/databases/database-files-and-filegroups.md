---
title: Groupes de fichiers et fichiers de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], files
- filegroups [SQL Server]
- transaction logs [SQL Server], about
- transaction logs [SQL Server], files
- .mdf files
- data files [SQL Server]
- default filegroups
- files [SQL Server], about files and filegroups
- secondary files [SQL Server]
- log files [SQL Server]
- .ndf files
- files [SQL Server]
- .ldf files
- database files [SQL Server]
- databases [SQL Server], filegroups
- filegroups [SQL Server], types
- primary filegroups [SQL Server]
- user-defined filegroups [SQL Server]
- filegroups [SQL Server], about filegroups
- primary files [SQL Server]
- file types [SQL Server]
ms.assetid: 9ca11918-480d-4838-9198-cec221ef6ad0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3d75dee637a5579ca3f189e14333fbf9356623d0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917276"
---
# <a name="database-files-and-filegroups"></a>Groupes de fichiers et fichiers de base de données
  Chaque base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possède au moins deux fichiers de système d'exploitation : un fichier de données et un fichier journal. Les fichiers de données contiennent des données et des objets tels que des tables, des index, des procédures stockées et des vues. Les fichiers journaux contiennent les informations nécessaires pour récupérer toutes les transactions de la base de données. Les fichiers de données peuvent être regroupés dans des groupes de fichiers à des fins d'allocation et d'administration.  
  
## <a name="database-files"></a>Fichiers de base de données  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les bases de données possèdent trois types de fichiers, comme indiqué dans le tableau suivant.  
  
|Fichier|Description|  
|----------|-----------------|  
|Principale|Le fichier de données primaire contient les informations de démarrage de la base de données, et il pointe vers les autres fichiers de la base de données. Les objets et les données utilisateur peuvent être stockés dans ce fichier ou dans des fichiers de données secondaires. Chaque base de données comprend un fichier de données primaire. L'extension de fichier recommandée est .mdf.|  
|Secondary|Les fichiers de données secondaires sont facultatifs, définis par l'utilisateur, et ils stockent les données utilisateur. Les fichiers secondaires peuvent être utilisés pour répartir des données sur plusieurs disques en plaçant chaque fichier sur un lecteur de disque distinct. En outre, si la taille d'une base de données excède la taille maximale autorisée pour un fichier Windows, vous pouvez avoir recours aux fichiers secondaires afin que la base de données puisse continuer à croître.<br /><br /> L'extension de fichier recommandée est .ndf.|  
|Journal des transactions|Les fichiers journaux des transactions contiennent les informations du journal qui sont utilisées pour la restauration de la base de données. Chaque base de données doit posséder au moins un fichier journal. L'extension de fichier recommandée pour les journaux des transactions est .ldf.|  
  
 Par exemple, il est possible de créer une base de données simple (appelée **Sales** ) incluant un fichier primaire qui contient toutes les données et tous les objets, et un fichier journal qui contient les informations du journal des transactions. Ou encore, il est possible de créer une base de données plus complexe (appelée **Orders** ) incluant un fichier primaire et cinq fichiers secondaires. Les données et les objets de la base de données sont répartis dans les six fichiers, et les quatre fichiers journaux contiennent les informations du journal des transactions.  
  
 Par défaut, les données et les journaux des transactions sont placés sur le même lecteur et leur chemin est identique, ceci afin de gérer les systèmes comportant un seul disque. Cependant, cette configuration n'est pas forcément optimale pour les environnements de production. Nous vous recommandons de placer les fichiers de données et les fichiers journaux sur des disques distincts.  
  
## <a name="filegroups"></a>Groupes de fichiers  
 Chaque base de données possède un groupe de fichiers primaire. Celui-ci contient le fichier de données primaire et tous les fichiers secondaires qui n'ont pas été placés dans d'autres groupes de fichiers. Il est possible de créer des groupes de fichiers définis par l'utilisateur pour regrouper des fichiers de données à des fins d'administration, d'allocation des données et de placement.  
  
 Par exemple, trois fichiers (Data1.ndf, Data2.ndf, et Data3.ndf) peuvent être créés sur trois lecteurs, respectivement, puis affectés au groupe de fichiers **fgroup1**. Une table peut alors être créée spécialement pour le groupe de fichiers **fgroup1**. Les requêtes portant sur des données de la table seront réparties sur les trois disques, ce qui permettra d'améliorer les performances. Une amélioration similaire des performances pourra être obtenue en créant un fichier unique sur un jeu de bandes RAID (Redundant Array of Independent Disks). Cependant, les fichiers et les groupes de fichiers vous permettent d'ajouter facilement des fichiers sur de nouveaux disques.  
  
 Tous les fichiers de données sont stockés dans les groupes de fichiers répertoriés dans le tableau suivant.  
  
|Groupe de fichiers|Description|  
|---------------|-----------------|  
|Principale|Groupe de fichiers qui contient le fichier primaire. Toutes les tables système sont allouées au groupe de fichiers primaire.|  
|Définie par l'utilisateur|Groupe de fichiers créé par l'utilisateur lorsque celui-ci crée la base de données ou lorsqu'il la modifie ultérieurement.|  
  
### <a name="default-filegroup"></a>Groupe de fichiers par défaut  
 Lorsque des objets sont créés dans la base de données, sans spécifier le groupe de fichiers auquel ils appartiennent, ces objets sont affectés au groupe de fichiers par défaut. À tout moment, un groupe de fichiers précis est désigné comme étant le groupe de fichiers par défaut. Les fichiers du groupe de fichiers par défaut doivent être suffisamment volumineux pour contenir tous les nouveaux objets qui ne sont pas affectés à d'autres groupes de fichiers.  
  
 Le groupe de fichiers PRIMARY est le groupe de fichiers par défaut sauf s'il est modifié par l'instruction ALTER DATABASE. Les objets et tables système restent affectés au groupe de fichiers PRIMARY, et non au nouveau groupe par défaut.  
  
## <a name="related-content"></a>Contenu associé  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
 [Options de fichiers et de groupes de fichiers ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-file-and-filegroup-options)  
  
 [Attacher et détacher une base de données &#40;SQL Server&#41;](database-detach-and-attach-sql-server.md)  
  
  
