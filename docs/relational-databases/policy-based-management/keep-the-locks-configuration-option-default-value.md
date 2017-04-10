---
title: "Conserver la valeur par d&#233;faut de l&#39;option de configuration locks | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "meilleures pratiques [moteur de base de données]"
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
caps.latest.revision: 12
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 12
---
# Conserver la valeur par d&#233;faut de l&#39;option de configuration locks
  Cette règle vérifie la valeur de l'option de configuration locks (verrous). Cette option détermine le nombre maximal de verrous disponibles et limite ainsi la quantité de mémoire utilisée par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] pour les verrous. La valeur par défaut 0 permet à [!INCLUDE[ssDE](../../includes/ssde-md.md)] d’allouer et de libérer des structures de verrous de manière dynamique en fonction des modifications de la configuration requise.  
  
 Si la valeur de l'option locks est différente de zéro, les programmes de traitement par lots s'arrêtent et un message d'erreur indiquant un nombre de verrous insuffisant est généré lorsque la valeur spécifiée est dépassée.  
  
## Meilleures pratiques recommandées  
 Utilisez la procédure stockée système sp_configure pour rétablir la valeur par défaut de l'option locks à l'aide de l'instruction suivante :  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## Pour plus d'informations  
 [Configurer l'option de configuration du serveur locks](../../database-engine/configure-windows/configure-the-locks-server-configuration-option.md)  
  
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)  
  
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
  
 [Article 271509 de la Base de connaissances Microsoft](http://go.microsoft.com/fwlink/?linkid=117788)  
  
## Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  