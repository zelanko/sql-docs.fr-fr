---
title: SMO and DMO XPs (option de configuration de serveur) | Microsoft Docs
description: Découvrez comment activer des procédures stockées étendues de SQL Server Management Object (SMO) sur un serveur. Affichez les informations de l’option de configuration « SMO and DMO XPs ».
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a636f58ba3f7e9e178489e87af4dc3aa777fdbab
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773608"
---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>SMO and DMO XPs (option de configuration de serveur)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Utilisez l'option SMO and DMO XPs pour activer les procédures stockées étendues [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) sur ce serveur.  
  
 Remarque : à compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], DMO a été supprimé de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les valeurs possibles sont décrites dans le tableau suivant :  
  
|Valeur|Signification|  
|-----------|-------------|  
|0|Les procédures étendues SMO ne sont pas disponibles.|  
|1|Les procédures étendues SMO sont disponibles. Il s’agit de la valeur par défaut.|  
  
 Le paramètre prend effet immédiatement.  
  
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
  
  
