---
title: "Administrer plusieurs serveurs à l’aide de serveurs de gestion centralisée | Microsoft Docs"
ms.custom: 
ms.date: 08/12/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiserver queries
- central management server
- multiserver administration [SQL Server]
- master servers [SQL Server], central management servers
- target configuration [SQL Server]
- server configuration [SQL Server]
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fbe8297c459d4513d1b8e45c7d64807e0d73b503
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="administer-multiple-servers-using-central-management-servers"></a>Administrer plusieurs serveurs à l'aide de serveurs de gestion centralisée
  Vous pouvez administrer plusieurs serveurs en désignant des serveurs de gestion centralisée et en créant des groupes de serveurs.  
  
## <a name="what-is-a-central-management-server-and-server-groups"></a>Qu’est-ce qu’un serveur de gestion centralisée et des groupes de serveurs ?  
 Une instance de SQL Server désignée comme serveur de gestion centralisée gère des groupes de serveurs qui contiennent les informations de connexion pour une ou plusieurs instances. Les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] et les stratégies de la Gestion basée sur des stratégies peuvent être exécutées simultanément sur des groupes de serveurs. Vous pouvez également consulter les fichiers journaux sur les instances gérées via un serveur de gestion centralisée. 
 
 En principe, un serveur de gestion centralisée constitue un référentiel central contenant une liste de vos serveurs gérés. Les versions antérieures à [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ne peuvent pas être désignées comme serveurs de gestion centralisée.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] Les instructions peuvent également être exécutées sur des groupes de serveurs locaux dans Serveurs inscrits.  
  
## <a name="create-central-management-server-and-server-groups"></a>Créer un serveur de gestion centralisée et des groupes de serveurs 
 Pour créer un serveur de gestion centralisée et des groupes de serveurs, utilisez la fenêtre **Serveurs inscrits** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Notez que le serveur de gestion centralisée ne peut pas être membre d'un groupe qu'il gère. 
 
 Pour en savoir plus sur la création de serveurs de gestion centralisée et de groupes de serveurs, consultez [Créer un serveur de gestion centralisée et un groupe de serveurs &#40;SQL Server Management Studio&#41;](../tools/sql-server-management-studio/create-a-central-management-server-and-server-group.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  

