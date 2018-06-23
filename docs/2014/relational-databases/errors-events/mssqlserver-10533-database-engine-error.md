---
title: MSSQLSERVER_10533 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 10533 (Database Engine error)
ms.assetid: cc2fbdab-7b90-415f-a1f9-066824344283
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 458716b859df07b3bef456a1c2e515168fc10744
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140977"
---
# <a name="mssqlserver10533"></a>MSSQLSERVER_10533
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10533|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_NAME_TOO_BIG|  
|Texte du message|Impossible de créer le repère de plan '%.*ls', car le nom du repère de plan dépasse 124, le nombre maximal de caractères autorisé. Indiquez un nom qui contient moins de 125 caractères.|  
  
## <a name="explanation"></a>Explication  
 Le nom du repère de plan dépasse 124 caractères, le nombre maximal autorisé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Indiquez un nom qui contient moins de 125 caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Repères de plan](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
