---
title: SMO and DMO XPs (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a356db3b34db86b7b71810dcb0d030580183c879
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055929"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>SMO and DMO XPs (option de configuration de serveur)
  Utilisez l'option SMO and DMO XPs pour activer les procédures stockées étendues [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) sur ce serveur.  
  
 Remarque : à compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], DMO a été supprimé de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les valeurs possibles sont décrites dans le tableau suivant :  
  
|Valeur|Signification|  
|-----------|-------------|  
|0|Les procédures étendues SMO ne sont pas disponibles.|  
|1|Les procédures étendues SMO sont disponibles. Il s'agit du paramètre par défaut.|  
  
 Ce paramètre prend effet immédiatement.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant active les procédures stockées étendues de SMO.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation SQL Server Management Objects &#40;SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  
