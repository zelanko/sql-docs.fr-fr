---
title: MSSQLSERVER_41332 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c9d0a01aeab48f11f88b511812f52d5416c61888
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85033001"
---
# <a name="mssqlserver_41332"></a>MSSQLSERVER_41332
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|41332|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQL_SNAPSHOT_NOT_SUPPORTED|  
|Texte du message|Les tables optimisées en mémoire et les procédures stockées compilées en mode natif ne sont pas accessibles ou ne peuvent pas être créées lorsque la session TRANSACTION ISOLATION LEVEL a la valeur SNAPSHOT.|  
  
## <a name="explanation"></a>Explication  
 La transaction a démarré au niveau d'isolation SNAPSHOT, puis a tenté d'utiliser une fonctionnalité qui n'est pas compatible.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Démarrer la transaction avec un autre niveau d'isolation. Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
