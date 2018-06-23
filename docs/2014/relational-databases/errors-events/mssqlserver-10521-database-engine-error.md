---
title: MSSQLSERVER_10521 | Microsoft Docs
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
- 10521 (Database Engine error)
ms.assetid: ba2d7e44-207c-4428-b5f0-c975ac122c0d
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 209496ac8159eb32c36fcded35992cac1e45d6f0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140052"
---
# <a name="mssqlserver10521"></a>MSSQLSERVER_10521
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|10521|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PG_PARAM_NEEDED|  
|Texte du message|Impossible de créer le repère de plan ' %. \*%.*ls, car `@type` a été spécifié en tant que '%.*ls' et le paramètre '%.*ls' est NULL. Ce type requiert une valeur autre que Null pour le paramètre. Spécifiez une valeur autre que Null pour le paramètre ou remplacez le type par un type qui autorise une valeur Null pour le paramètre.|  
  
## <a name="explanation"></a>Explication  
 Le type spécifié dans `@type` requiert une valeur non Null pour le paramètre spécifié ; toutefois, une valeur Null a été fournie.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Spécifiez une valeur autre que Null pour le paramètre ou remplacez le type par un type qui autorise une valeur Null pour le paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Repères de plan](../performance/plan-guides.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
