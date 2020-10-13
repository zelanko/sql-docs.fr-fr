---
title: Configurer votre entrepôt de données de point de contrôle de l’utilitaire (utilitaire SQL Server) | Microsoft Docs
description: Découvrez l’entrepôt de données de gestion de l’utilitaire, où les instances de SQL Server stockent les données. Découvrez comment configurer sa période de conservation des données et son répertoire.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 06080937156afc4e38c9ef59bd9b92e98695eb57
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91867871"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Configurer votre entrepôt de données de point de contrôle de l'utilitaire (utilitaire SQL Server)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Les données collectées par les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont stockées dans l'entrepôt de données de gestion de l'utilitaire (UMDW). Le nom de fichier UMDW est sysutility_mdw.  
  
 Vous pouvez configurer la période de rétention des données UMDW. Pour plus d’informations, consultez [Administration de l’utilitaire &#40;utilitaire SQL Server&#41;](/previous-versions/sql/sql-server-2016/ee240832(v=sql.130)).  
  
 Les paramètres de configuration suivants ne sont pas configurables dans cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Nom UMDW : Sysutility_mdw.  
  
-   Fréquence de téléchargement du jeu d’éléments de collecte : toutes les 15 minutes.  
  
 Le répertoire UMDW est configurable : \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<Nom_UCP>\MSSQL\Data\\, où \<System drive> est normalement le lecteur C:\. Le fichier journal, Sysutility_mdw_\<GUID>_LOG, se trouve dans le même répertoire.  
  
> [!NOTE]  
>  L'emplacement du fichier UMDW (sysutility_mdw) peut être modifié à l'aide des opérations de détachement et d'attachement ou d'ALTER DATABASE. Nous recommandons l'utilisation d'ALTER DATABASE. Pour plus d’informations, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités et tâches de l’utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
