---
title: "V&#233;rification d&#39;acc&#232;s au cache (option de configuration de serveur) | Microsoft Docs"
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
  - "option access check cache"
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# V&#233;rification d&#39;acc&#232;s au cache (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]accède aux objets de base de données, la vérification de l'accès est mise en cache dans une structure interne appelée le **cache de résultat de la vérification d'accès**. Les options **access check cache quota** et **access check cache bucket count** contrôlent le nombre d'entrées et le nombre de compartiments de hachage utilisés pour le **cache de résultat de la vérification d'accès**. Dans de rares circonstances, la modification de ces options peut améliorer les performances.  
  
 Les valeurs par défaut 0 indiquent que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gère ces options. Microsoft recommande de ne modifier ces options que sur recommandation du support technique.  
  
## Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  