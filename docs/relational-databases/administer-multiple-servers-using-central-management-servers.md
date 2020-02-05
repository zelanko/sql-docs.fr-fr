---
title: Administrer plusieurs serveurs à l’aide de serveurs d’administration centrale
ms.date: 08/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- central management server
- multiserver administration [SQL Server]
- master servers [SQL Server], central management servers
- target configuration [SQL Server]
- server configuration [SQL Server]
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
author: MashaMSFT
ms.author: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: a2e2da55bd04ba29cf1c6ef81757488f8d50fd24
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "74055619"
---
# <a name="administer-multiple-servers-using-central-management-servers"></a>Administrer plusieurs serveurs à l’aide de serveurs d’administration centrale
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Vous pouvez administrer plusieurs serveurs en désignant des serveurs de gestion centralisée et en créant des groupes de serveurs.  
  
## <a name="what-is-a-central-management-server-and-server-groups"></a>Qu’est-ce qu’un serveur de gestion centralisée et des groupes de serveurs ?  
 Une instance de SQL Server désignée comme serveur de gestion centralisée gère des groupes de serveurs qui contiennent les informations de connexion pour une ou plusieurs instances. Les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] et les stratégies de la Gestion basée sur des stratégies peuvent être exécutées simultanément sur des groupes de serveurs. Vous pouvez également consulter les fichiers journaux sur les instances gérées via un serveur de gestion centralisée. 
 
 En principe, un serveur de gestion centralisée constitue un référentiel central contenant la liste de vos serveurs gérés. Les versions antérieures à [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ne peuvent pas être désignées comme serveurs de gestion centralisée.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] Les instructions peuvent également être exécutées sur des groupes de serveurs locaux dans Serveurs inscrits.  
  
## <a name="create-central-management-server-and-server-groups"></a>Créer un serveur de gestion centralisée et des groupes de serveurs 
 Pour créer un serveur de gestion centralisée et des groupes de serveurs, utilisez la fenêtre **Serveurs inscrits** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Notez que le serveur de gestion centralisée ne peut pas être membre d'un groupe qu'il gère. 
 
 Pour en savoir plus sur la création de serveurs de gestion centralisée et de groupes de serveurs, consultez [Créer un serveur de gestion centralisée et un groupe de serveurs &#40;SQL Server Management Studio&#41;](../tools/sql-server-management-studio/create-a-central-management-server-and-server-group.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
