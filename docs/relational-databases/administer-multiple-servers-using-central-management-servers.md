---
title: "Administrer plusieurs serveurs &#224; l&#39;aide de serveurs de gestion centralis&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "08/12/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "requêtes multiserveurs"
  - "serveur de gestion centralisée"
  - "administration multiserveur [SQL Server]"
  - "serveurs maîtres [SQL Server], serveurs de gestion centralisée"
  - "configuration cible [SQL Server]"
  - "configuration du serveur [SQL Server]"
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# Administrer plusieurs serveurs &#224; l&#39;aide de serveurs de gestion centralis&#233;e
  Vous pouvez administrer plusieurs serveurs en désignant des serveurs de gestion centralisée et en créant des groupes de serveurs.  
  
## Qu’est-ce qu’un serveur de gestion centralisée et des groupes de serveurs ?  
 Une instance de SQL Server désignée comme serveur de gestion centralisée gère des groupes de serveurs qui contiennent les informations de connexion pour une ou plusieurs instances. Les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] et les stratégies de la Gestion basée sur des stratégies peuvent être exécutées simultanément sur des groupes de serveurs. Vous pouvez également consulter les fichiers journaux sur les instances gérées via un serveur de gestion centralisée. 
 
 En principe, un serveur de gestion centralisée constitue un référentiel central contenant une liste de vos serveurs gérés. Les versions antérieures à [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ne peuvent pas être désignées comme serveurs de gestion centralisée.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] Les instructions peuvent également être exécutées sur des groupes de serveurs locaux dans Serveurs inscrits.  
  
## Créer un serveur de gestion centralisée et des groupes de serveurs 
 Pour créer un serveur de gestion centralisée et des groupes de serveurs, utilisez la fenêtre **Serveurs inscrits** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Notez que le serveur de gestion centralisée ne peut pas être membre d'un groupe qu'il gère. 
 
 Pour en savoir plus sur la création de serveurs de gestion centralisée et de groupes de serveurs, consultez [Créer un serveur de gestion centralisée et un groupe de serveurs &#40;SQL Server Management Studio&#41;](../tools/sql-server-management-studio/create-a-central-management-server-and-server-group.md).  
  
## Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  