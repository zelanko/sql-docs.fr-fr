---
title: Chargement en masse des données dans des Tables dans une Publication de fusion (programmation Transact-SQL de la réplication) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
caps.latest.revision: 32
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 01c29e00546b0b90fce67fa4242c8398b2392614
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051028"
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication-replication-transact-sql-programming"></a>Charger en masse des données dans les tables d'une publication de fusion (programmation Transact-SQL de la réplication)
  Lorsque les données sont chargées dans des tables à l'aide des [bcp Utility](../../tools/bcp-utility.md) ou de la commande [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) , par défaut, les déclencheurs de réplication de fusion qui conservent les données de suivi dans la table système [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) ne sont pas déclenchés. Vous avez le choix entre forcer les déclencheurs de réplication de fusion à se déclencher au chargement des données et insérer par programmation les métadonnées de réplication générées après l'opération de copie en bloc à l'aide de procédures stockées de réplication.  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a>Pour charger en masse les données dans les tables publiées par la réplication de fusion à l'aide de l'utilitaire bcp  
  
1.  Sur le serveur de publication ou sur l'Abonné, exécutez l' [bcp Utility](../../tools/bcp-utility.md) ou [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) pour insérer des données dans une table a publié à l'aide de la réplication de fusion.  
  
2.  Utilisez l'une des méthodes suivantes pour garantir que les métadonnées de réplication sont générées pour les données insérées.  
  
    -   Exécutez la copie en bloc à l'aide de l'option FIRE_TRIGGERS.  
  
    -   Dans la base de données dans laquelle les données ont été insérées, exécutez [sp_addtabletocontents &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql). Spécifiez le nom de la table dans laquelle les données ont été insérées pour **@table_name**.  
  
  
