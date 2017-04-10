---
title: "SMO et DMO XPs (option de configuration de serveur) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# SMO et DMO XPs (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisez l'option des procédures étendues SMO et DMO pour activer les procédures stockées étendues [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object (SMO) sur ce serveur.  
  
 Remarque : à compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], DMO a été supprimé de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Les valeurs possibles sont décrites dans le tableau suivant :  
  
|Valeur|Signification|  
|-----------|-------------|  
|0|Les procédures étendues SMO ne sont pas disponibles.|  
|1|Les procédures étendues SMO sont disponibles. Il s'agit du paramètre par défaut.|  
  
 Ce paramètre prend effet immédiatement.  
  
## Exemples  
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
  
## Voir aussi  
 [Guide de programmation SQL Server Management Objects &#40;SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  