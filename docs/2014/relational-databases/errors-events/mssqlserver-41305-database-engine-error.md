---
title: MSSQLSERVER_41305 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41305 (Database Engine error)
ms.assetid: a96e5083-ff97-4003-a900-07942454151d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 41cf51944a865d5309f8b730d07a6f558296829b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551454"
---
# <a name="mssqlserver_41305"></a>MSSQLSERVER_41305
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|41305|  
|Source de l’événement|MSSQLSERVER|  
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
  
  
