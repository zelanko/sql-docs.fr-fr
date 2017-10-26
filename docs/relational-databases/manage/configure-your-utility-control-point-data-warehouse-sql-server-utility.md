---
title: "Configurer votre entrepôt de données de point de contrôle de l’utilitaire (utilitaire SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 05a436bf21810e3c05c2f745d6f0c067f61d0d35
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Configurer votre entrepôt de données de point de contrôle de l'utilitaire (utilitaire SQL Server)
  Les données collectées par les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont stockées dans l'entrepôt de données de gestion de l'utilitaire (UMDW). Le nom de fichier UMDW est sysutility_mdw.  
  
 Vous pouvez configurer la période de rétention des données UMDW. Pour plus d’informations, consultez [Administration de l’utilitaire &#40;utilitaire SQL Server&#41;](http://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d)  
  
 Les paramètres de configuration suivants ne sont pas configurables dans cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   nom de l'UMDW: Sysutility_mdw ;  
  
-   fréquence de téléchargement du jeu d'éléments de collecte : toutes les 15 minutes.  
  
 Le répertoire UMDW est configurable : \<lecteur_système>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, où \<lecteur_système> est normalement le lecteur C:\. Le fichier journal, Sysutility_mdw_\<GUID>_LOG, se trouve dans le même répertoire.  
  
> [!NOTE]  
>  L'emplacement du fichier UMDW (sysutility_mdw) peut être modifié à l'aide des opérations de détachement et d'attachement ou d'ALTER DATABASE. Nous recommandons l'utilisation d'ALTER DATABASE. Pour plus d’informations, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités et tâches de l'utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  

