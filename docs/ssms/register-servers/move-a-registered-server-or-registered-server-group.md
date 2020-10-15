---
description: Déplacer un serveur inscrit ou un groupe de serveurs inscrits
title: Déplacer un serveur ou un groupe de serveurs inscrit
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- moving registered server or server group
- Registered Servers [SQL Server], server groups
- server groups [SQL Server]
- Registered Servers [SQL Server], moving server or server group
- groups [SQL Server], server
ms.assetid: 4438ca98-3abe-4dea-a760-48a9dad63c2e
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.openlocfilehash: d433b5816919642b0d7b25b580f4314a949cf0c2
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92036907"
---
# <a name="move-a-registered-server-or-registered-server-group"></a>Déplacer un serveur inscrit ou un groupe de serveurs inscrits

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Cette rubrique explique comment organiser les serveurs dans des serveurs inscrits en déplaçant un serveur inscrit ou des groupes de serveurs dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les groupes de serveurs peuvent se composer de serveurs inscrits ou d'autres groupes de serveurs. Les serveurs comme les groupes de serveurs peuvent être déplacés d'un groupe de serveurs vers un autre.  

## <a name="SSMSProcedure"></a>  

### <a name="to-move-a-registered-server-or-server-group"></a>Pour déplacer un serveur ou un groupe de serveurs inscrit  

1. Dans Serveurs inscrits, cliquez avec le bouton droit sur un serveur ou un groupe de serveurs, puis cliquez sur **Déplacer vers**.  
  
2. Dans la boîte de dialogue **Déplacer l’inscription du serveur** , développez la liste des groupes de serveurs, cliquez sur le nœud où doit apparaître le serveur ou le groupe de serveurs, puis cliquez sur **OK**.  

## <a name="see-also"></a>Voir aussi

[Inscrire des serveurs](./register-servers.md)

[Créer ou modifier un groupe de serveurs &#40;SQL Server Management Studio&#41;](./create-or-edit-a-server-group-sql-server-management-studio.md)