---
title: Configurer votre entrepôt de données de point de contrôle de l’utilitaire (utilitaire SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5e1749ce022b07215bfcabb4557bda0c9aacc197
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600318"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a>Configurer votre entrepôt de données de point de contrôle de l'utilitaire (utilitaire SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Les données collectées par les instances gérées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont stockées dans l'entrepôt de données de gestion de l'utilitaire (UMDW). Le nom de fichier UMDW est sysutility_mdw.  
  
 Vous pouvez configurer la période de rétention des données UMDW. Pour plus d’informations, consultez [Administration de l’utilitaire &#40;utilitaire SQL Server&#41;](http://msdn.microsoft.com/library/3e5a00c3-8905-40f0-9ddc-d924df9c2f0d)  
  
 Les paramètres de configuration suivants ne sont pas configurables dans cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   nom de l'UMDW: Sysutility_mdw ;  
  
-   fréquence de téléchargement du jeu d'éléments de collecte : toutes les 15 minutes.  
  
 Le répertoire UMDW est configurable : \<lecteur_système>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, où \<lecteur_système> est normalement le lecteur C:\. Le fichier journal, Sysutility_mdw_\<GUID>_LOG, se trouve dans le même répertoire.  
  
> [!NOTE]  
>  L'emplacement du fichier UMDW (sysutility_mdw) peut être modifié à l'aide des opérations de détachement et d'attachement ou d'ALTER DATABASE. Nous recommandons l'utilisation d'ALTER DATABASE. Pour plus d’informations, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Fonctionnalités et tâches de l'utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
