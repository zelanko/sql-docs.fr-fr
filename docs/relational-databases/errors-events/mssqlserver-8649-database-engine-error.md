---
title: MSSQLSERVER_8649 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 8649 (Database Engine error)
ms.assetid: 992dbc74-7c3a-498b-9f1b-b28387640677
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 065e943af721367f648a81b1c4e44c5a2ecc358c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver8649"></a>MSSQLSERVER_8649
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|8649|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|COST_TOO_HIGH|  
|Texte du message|La requête a été annulée parce que son coût estimé (%d) est supérieur au seuil configuré, %d. Contactez l'administrateur système.|  
  
## <a name="explanation"></a>Explication  
La requête a été annulée parce que son coût estimé est supérieur au seuil configuré pour QUERY_GOVERNOR_COST_LIMIT.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Spécifiez une valeur supérieure pour l'option QUERY_GOVERNOR_COST_LIMIT.  
  
## <a name="see-also"></a>Voir aussi  
[SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](~/t-sql/statements/set-query-governor-cost-limit-transact-sql.md)  
  
