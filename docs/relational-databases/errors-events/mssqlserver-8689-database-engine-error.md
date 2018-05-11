---
title: MSSQLSERVER_8689 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 8689 (Database Engine error)
ms.assetid: 99467a32-6576-4272-a076-b16c06933f2a
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bf60cb3bb8959b42446b872ffce2e379a608ca70
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver8689"></a>MSSQLSERVER_8689
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|8689|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|USEPLAN_ERR_NO_DB|  
|Texte du message|La base de données '%.*ls' spécifiée dans l'indicateur USE PLAN n'existe pas. Indiquez une base de données existante.|  
  
## <a name="explanation"></a>Explication  
Une base de données spécifiée dans l'indicateur USE PLAN n'existe pas.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Veillez à ce que toutes les bases de données spécifiées dans l'indicateur USE PLAN existent.  
  
## <a name="see-also"></a> Voir aussi  
[Indicateurs de requête &#40;Transact-SQL&#41;](~/t-sql/queries/hints-transact-sql-query.md)  
[Repères de plan](~/relational-databases/performance/plan-guides.md)  
  
