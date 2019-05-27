---
title: SQL Server fonctionnalités déconseillées dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: fdc0c778-cc8d-42ab-8833-4deb4329f37a
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d28d829280e205028a99afd9fec2e019bf567ab
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66089480"
---
# <a name="deprecated-sql-server-features-in-sql-server-2014"></a>Fonctionnalités SQL Server déconseillées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités déconseillées qui sont toujours disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Il est prévu que ces fonctionnalités soient supprimées dans une prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les fonctions déconseillées ne doivent pas être utilisées dans de nouvelles applications.  
  
## <a name="features-not-supported-in-the-next-version-of-includessnoversionincludesssnoversion-mdmd"></a>Fonctionnalités non prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
 Les fonctionnalités suivantes du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] ne seront pas prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Évitez d'utiliser ces fonctionnalités dans vos nouveaux développements et modifiez dès que possible les applications qui y ont recours. La colonne Nom de la fonctionnalité apparaît dans les événements de suivi comme ObjectName, et dans les compteurs de performance et sys.dm_os_performance_counters comme nom_instance. L'ID de la fonctionnalité apparaît dans les événements de trace comme ObjectId.  
  
|Category|Fonctionnalité déconseillée|Remplacement|Nom de la fonctionnalité|ID de la fonctionnalité|  
|--------------|------------------------|-----------------|------------------|----------------|  
|Programmabilité des données|[sys.soap_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-soap-endpoints-transact-sql)|Windows Communications Foundation (WCF) ou ASP.NET|Services Web XML natifs|22|  
|Programmabilité des données|[sys.endpoint_webmethods &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-endpoint-webmethods-transact-sql)|Windows Communications Foundation (WCF) ou ASP.NET|Services Web XML natifs|23|  
  
### <a name="slipstream-functionality"></a>Effectuer l'installation intégrée d'une fonctionnalité  
 La fonctionnalité Mise à jour de produit remplace la fonctionnalité Installation intégrée qui était disponible dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1. Par conséquent, les paramètres de ligne de commande, /*PCUSource* et /*CUSource*, associés à la fonctionnalité d'installation intégrée, ne doivent plus être utilisés. Les paramètres continueront de fonctionner mais peuvent être supprimés dans une version ultérieure du programme d'installation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Le paramètre /*UpdateSource* combine la fonctionnalité des paramètres d'installation intégrée /*PCUSource* et /*CUSource*.  
  
 Pour plus d’informations sur la fonctionnalité d’installation intégrée qui était disponible dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1, consultez [intégrer une mise à jour de SQL Server](https://go.microsoft.com/fwlink/?LinkId=219945) (https://go.microsoft.com/fwlink/?LinkId=219945).  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante](../../2014/getting-started/backward-compatibility.md)  
  
  
