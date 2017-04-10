---
title: "clr enabled (option de configuration de serveur) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys [intégration CLR], vérification de la possibilité d’exécution"
  - "clr enabled (option)"
ms.assetid: 0722d382-8fd3-4fac-b4a8-cd2b7a7e0293
caps.latest.revision: 36
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 36
---
# clr enabled (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  L'option CLR activé vous permet de spécifier si des assemblys utilisateur peuvent être exécutés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L’option CLR activé fournit les valeurs suivantes : 
  
|Valeur|Description|  
|-----------|-----------------|  
|0|L'exécution de l'assembly n'est pas autorisée sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|1|L'exécution de l'assembly est autorisée sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
WOW64 uniquement. Redémarrez les serveurs WOW64 pour appliquer les modifications des paramètres. Le redémarrage n’est pas nécessaire pour les autres types de serveurs.  

Quand vous exécutez l’instruction RECONFIGURE et que la valeur d’exécution de l’option CLR activé est 0 et non plus 1, tous les domaines d’application contenant des assemblys utilisateur sont immédiatement déchargés.  
  
>  **L’exécution de CLR (Common language runtime) n’est pas prise en charge sous le regroupement léger** Désactivez l’une des deux options : "clr enabled" ou "lightweight pooling". Les fonctionnalités qui reposent sur le CLR et qui ne fonctionnent pas correctement en mode fibre incluent le type de données **hierarchy**, la réplication et la Gestion basée sur des stratégies.  
  
## Exemple  
 L'exemple suivant déclare indique d'abord le paramètre actuel de l'option clr enabled, puis active l'option en lui attribuant la valeur 1. Pour désactiver l'option, affectez-lui la valeur 0.  
  
```tsql  
EXEC sp_configure 'clr enabled';  
EXEC sp_configure 'clr enabled' , '1';  
RECONFIGURE;    
```  
  
## Voir aussi  
 [Regroupement léger (option de configuration de serveur)](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Regroupement léger (option de configuration de serveur)](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
  