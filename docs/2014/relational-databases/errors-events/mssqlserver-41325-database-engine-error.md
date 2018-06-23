---
title: MSSQLSERVER_41325 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 41325 (Database Engine error)
ms.assetid: 97c6a8bb-139a-44f3-9ed5-f46d047e8ed3
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9fb25e864ec47f7574b683779b867f429c5a556d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051542"
---
# <a name="mssqlserver41325"></a>MSSQLSERVER_41325
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|41325|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HK_TX_COMMIT_SR_VALIDATION|  
|Texte du message|La transaction en cours n'a pas été validée en raison d'un échec de validation SERIALIZABLE.|  
  
## <a name="explanation"></a>Explication  
 La transaction a rencontré une erreur de validation, et est maintenant vouée à l'échec.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Réexécutez la transaction en échec. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  