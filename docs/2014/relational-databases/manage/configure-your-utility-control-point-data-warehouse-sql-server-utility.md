---
title: Configurer votre entrepôt de données de point de contrôle de l’utilitaire (utilitaire SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d2a9f40c2d1566a1f8ca5f054467f61da1920e5f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52804041"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Configurer votre entrepôt de données de point de contrôle de l'utilitaire (utilitaire SQL Server)
  Les données collectées par les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont stockées dans l'entrepôt de données de gestion de l'utilitaire (UMDW). Le nom de fichier UMDW est sysutility_mdw.  
  
 Vous pouvez configurer la période de rétention des données UMDW. Pour plus d’informations, consultez [Administration de l’utilitaire &#40;utilitaire SQL Server&#41;](../../database-engine/utility-administration-sql-server-utility.md)  
  
 Les paramètres de configuration suivants ne sont pas configurables dans cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Nom de l’UMDW : Sysutility_mdw.  
  
-   Collection de définie la fréquence de téléchargement : Toutes les 15 minutes.  
  
 Le répertoire UMDW est configurable : \<Lecteur système > : Files\Microsoft SQL Server\MSSQL10_50. < nom_ucp > \MSSQL\Data\\, où \<lecteur système > est normalement le lecteur C:\. Le fichier journal, Sysutility_mdw_\<GUID>_LOG, se trouve dans le même répertoire.  
  
> [!NOTE]  
>  L'emplacement du fichier UMDW (sysutility_mdw) peut être modifié à l'aide des opérations de détachement et d'attachement ou d'ALTER DATABASE. Nous recommandons l'utilisation d'ALTER DATABASE. Pour plus d’informations, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités et tâches de l'utilitaire SQL Server](sql-server-utility-features-and-tasks.md)  
  
  
