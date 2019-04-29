---
title: MSSQLSERVER_10520 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 79274cf031103e50151b6e93a9daff781005abad
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916171"
---
# <a name="mssqlserver10520"></a>MSSQLSERVER_10520
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10520|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_PARAM_NOT_ALLOWED|  
|Texte du message|Impossible de créer le repère de plan ’%.ls’, car @type a été spécifié comme ’%ls’ et une valeur autre que Null est spécifiée pour le paramètre ’%ls’. Ce type requiert une valeur Null pour le paramètre. Spécifiez la valeur Null pour le paramètre ou remplacez le type par un type qui autorise une valeur autre que Null pour le paramètre.|  
  
## <a name="explanation"></a>Explication  
 Le type spécifié dans @type nécessite une valeur Null pour le paramètre spécifié, mais une valeur non Null a été fournie.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Spécifiez la valeur Null pour le paramètre ou remplacez le type par un type qui autorise une valeur autre que Null pour le paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Repères de plan](../performance/plan-guides.md)  
  
  
