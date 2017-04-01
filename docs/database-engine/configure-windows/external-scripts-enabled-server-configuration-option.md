---
title: "option de configuration de serveur scripts externes activ&#233;s | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "external scripts enabled"
  - "external_scripts_enabled_TSQL"
helpviewer_keywords: 
  - "option de scripts externes activés"
ms.assetid: 9d0ce165-8719-4007-9ae8-00f85cab3a0d
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 8
---
# option de configuration de serveur scripts externes activ&#233;s
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Utilisez l’option **external scripts enabled** pour activer l’exécution de scripts avec certaines extensions de langage à distance. Cette propriété est désactivée par défaut. Le programme d’installation peut éventuellement définir cette propriété sur true si **Advanced Analytics Services** est installé.  
  
||  
|-|  
|**S’applique à** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 Vous devez activer l’option de scripts externes activés avant de pouvoir exécuter un script externe à l’aide de la procédure **sp_execute_external_script**. Utilisez **sp_execute_external_script** pour exécuter des scripts écrits dans un langage pris en charge, tels que R. Dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] comprend un composant de serveur installé avec [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], ainsi qu’un ensemble d’outils de station de travail et de bibliothèques de connectivité qui connectent les données scientifiques à l’environnement hautes performances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Installez la fonction **Extensions analytiques avancées** pendant l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour permettre l’exécution de scripts R. Pour plus d’informations, voir [Installing Previous Versions of SQL Server R Services](../Topic/Installing%20Previous%20Versions%20of%20SQL%20Server%20R%20Services.md).  
  
 Exécutez le script suivant pour activer les scripts externes.  
  
```  
sp_configure 'external scripts enabled', 1;  
RECONFIGURE;  
```  
  
 Vous devez redémarrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour que ce changement soit effectif.  
  
## Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)   
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)  
  
  