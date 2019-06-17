---
title: MSSQLSERVER_41342 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 57ce65cb8fed85eed9eacc176a371dec52145e1c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62867913"
---
# <a name="mssqlserver41342"></a>MSSQLSERVER_41342
    
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
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
