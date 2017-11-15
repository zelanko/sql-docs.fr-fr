---
title: MSSQLSERVER_2596 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 8eb8b851b589c916a449b527c8037e932d683472
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver2596"></a>MSSQLSERVER_2596
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2596|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_DATABASE_IN_READ_ONLY_MODE|  
|Texte du message|L’instruction de réparation n’a pas été traitée. La base de données ne peut pas être en mode lecture seule.|  
  
## <a name="explanation"></a>Explication  
Ce message indique que la base de données est en mode lecture seule. Il est impossible de réparer une base de données qui est en mode lecture seule.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Passez la base de données en mode lecture/écriture à l'aide de ALTER DATABASE, puis exécutez de nouveau la commande DBCC.  
  
## <a name="see-also"></a>Voir aussi  
[ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
  
