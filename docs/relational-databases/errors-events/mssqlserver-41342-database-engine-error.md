---
title: MSSQLSERVER_41342 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
caps.latest.revision: 8
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 33ea4c8f9fb2188bade1341e5b4c859572b8f9f5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver41342"></a>MSSQLSERVER_41342
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|41342|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HK_HW_NOT_SUPPORTED|  
|Texte du message|Le modèle du processeur sur le système ne prend pas en charge la création de *construct*. En règle générale, cette erreur se produit avec les processeurs plus anciens. Pour plus d'informations sur les modèles pris en charge, consultez la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
## <a name="explanation"></a>Explication  
Les tables optimisées en mémoire requièrent un modèle de processeur qui prend en charge les opérations de comparaison et d'échange atomiques sur les valeurs 128 bits, qui nécessitent l'instruction d'assemblage CMPXCHG16B. Certains modèles de processeur AMD plus anciens ne prennent pas en charge l'instruction CMPXCHG16B. En outre, certains environnements de virtualisation n'autorisent pas cette instruction par défaut.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Mettez à niveau votre processeur. Si votre processeur prend en charge l'instruction et que vous exécutez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un ordinateur virtuel, modifiez la configuration afin de prendre en charge l'instruction CMPXCHG16B.  
  
## <a name="see-also"></a> Voir aussi  
[OLTP en mémoire &#40;Optimisation en mémoire&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
