---
title: MSSQLSERVER_41305 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41305 (Database Engine error)
ms.assetid: a96e5083-ff97-4003-a900-07942454151d
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 499ec2d1630f74a329a5f72a1bc6a784463ec2a4
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415878"
---
# <a name="mssqlserver41305"></a>MSSQLSERVER_41305
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|41305|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HK_TX_COMMIT_RR_VALIDATION|  
|Texte du message|La transaction en cours n'a pas été validée en raison d'un échec de validation REPEATABLE READ.|  
  
## <a name="explanation"></a>Explication  
 La transaction a rencontré une erreur de validation, et est maintenant vouée à l'échec.  
  
 Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Réexécutez la transaction en échec.  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
