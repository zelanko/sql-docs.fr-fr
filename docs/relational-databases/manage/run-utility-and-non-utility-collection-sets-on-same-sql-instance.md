---
title: Exécuter des jeux d’éléments de collecte d’utilitaire et de non-utilitaire sur la même Instance SQL | Microsoft Docs
description: Découvrez comment surveiller une instance de SQL Server à l’aide d’utilitaires et de jeux d’éléments de collecte sans utilitaire qui fonctionnent côte à côte. Affichez les exigences de configuration.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ca7ee9b3-ef9a-4ba4-83d0-9ee9f80dab27
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 522b21e2a2c7e78c8ca16483fc02f2564e0ebaf5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773469"
---
# <a name="run-utility-and-non-utility-collection-sets-on-same-sql-instance"></a>Exécuter des jeux d’éléments de collecte d’utilitaire et de non-utilitaire sur la même Instance SQL
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Le jeu d'éléments de collecte de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est pris en charge côte à côte avec les jeux d'éléments de collecte d'utilitaires non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Autrement dit, une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être surveillée par d'autres jeux d'éléments de collecte bien qu'elle soit membre d'un utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Toutefois, vous devez désactiver les fonctionnalités du jeu d'éléments de collecte de l'utilitaire non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pendant que l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est inscrite dans l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Une fois l'instance inscrite avec l'UCP, vous pouvez redémarrer le jeu d'éléments de collecte de l'utilitaire non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Notez, toutefois, que tous les jeux d'éléments de collecte sur l'instance gérée téléchargeront leurs données dans l'entrepôt de données de gestion de l'utilitaire (UMDW). Le nom de fichier UMDW est sysutility_mdw.  
  
 Pour exécuter des jeux d'éléments de collecte d'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] côte à côte avec des jeux d'éléments de collecte d'utilitaire non- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , prenez en considération les points suivants :  
  
-   Les jeux d'éléments de collecte côte à côte sont pris en charge.  
  
-   Vous devez désactiver les collecteurs de données existants en inscrivant des instances dans l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Pour satisfaire aux exigences de validation, vous devez exécuter les procédures stockées suivantes sur l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de créer un UCP, et sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de l'inscrire dans l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
    ```  
    exec msdb.dbo.sp_syscollector_set_warehouse_database_name NULL  
    exec msdb.dbo.sp_syscollector_set_warehouse_instance_name NULL  
    ```  
  
     Si vous n'exécutez pas ces procédures stockées avant de lancer l'Assistant Créer un UCP ou l'Assistant Ajouter une instance gérée, l'opération échouera.  
  
-   Vous devez utiliser l'UMDW (sysutility_mdw) de l'utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour tous les jeux d'éléments de collecte sur une instance gérée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités et tâches de l'utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Configurer votre entrepôt de données de point de contrôle de l’utilitaire &#40;utilitaire SQL Server&#41;](../../relational-databases/manage/configure-your-utility-control-point-data-warehouse-sql-server-utility.md)  
  
  
