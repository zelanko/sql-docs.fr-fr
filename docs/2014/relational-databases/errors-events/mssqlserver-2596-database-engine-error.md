---
title: MSSQLSERVER_2596 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 21f0f7fdbfc1658ccff24e9610ca96857de159ce
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551864"
---
# <a name="mssqlserver_2596"></a>MSSQLSERVER_2596
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|2596|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_DATABASE_IN_READ_ONLY_MODE|  
|Texte du message|L’instruction de réparation n’a pas été traitée. La base de données ne peut pas être en mode lecture seule.|  
  
## <a name="explanation"></a>Explication  
 Ce message indique que la base de données est en mode lecture seule. Il est impossible de réparer une base de données qui est en mode lecture seule.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Passez la base de données en mode lecture/écriture à l'aide de ALTER DATABASE, puis exécutez de nouveau la commande DBCC.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
