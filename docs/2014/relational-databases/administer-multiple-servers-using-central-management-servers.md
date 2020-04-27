---
title: Administrer plusieurs serveurs à l’aide de serveurs de gestion centralisée | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: f47eec543c21e74565d750035d20fbcee9baa82e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62877307"
---
# <a name="administer-multiple-servers-using-central-management-servers"></a>Administrer plusieurs serveurs à l'aide de serveurs de gestion centralisée
  Vous pouvez administrer plusieurs serveurs en désignant des serveurs de gestion centralisée et en créant des groupes de serveurs.  
  
## <a name="benefits-of-central-management-servers-and-server-groups"></a>Avantages des serveurs de gestion centralisée et des groupes de serveurs  
 Une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] désignée comme serveur de gestion centralisée gère des groupes de serveurs qui contiennent les informations de connexion pour une ou plusieurs instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] et les stratégies de la Gestion basée sur des stratégies peuvent être exécutées simultanément sur des groupes de serveurs. Vous pouvez également consulter les fichiers journaux de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur les instances gérées via un serveur de gestion centralisée. Les versions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ne peuvent pas être désignées comme serveurs de gestion centralisée.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] Les instructions peuvent également être exécutées sur des groupes de serveurs locaux dans Serveurs inscrits.  
  
### <a name="related-tasks"></a>Tâches associées  
 Pour créer un serveur de gestion centralisée et des groupes de serveurs, utilisez la fenêtre **Serveurs inscrits** dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Notez que le serveur de gestion centralisée ne peut pas être membre d'un groupe qu'il gère. Pour plus d’informations sur la création de serveurs de gestion centralisée et de groupes de serveurs, consultez [Créer un serveur de gestion centralisée et un groupe de serveurs &#40;SQL Server Management Studio&#41;](../ssms/register-servers/create-a-central-management-server-and-server-group.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Administrer des serveurs à l'aide de la Gestion basée sur des stratégies](policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
