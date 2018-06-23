---
title: SQL Server fonctionnalités déconseillées dans SQL Server 2014 | Documents Microsoft
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fdc0c778-cc8d-42ab-8833-4deb4329f37a
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d0cafd847932ef5f87064defb8e92e7ac4b09784
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140326"
---
# <a name="deprecated-sql-server-features-in-sql-server-2014"></a>Fonctionnalités SQL Server déconseillées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités déconseillées qui sont toujours disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Il est prévu que ces fonctionnalités soient supprimées dans une prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les fonctions déconseillées ne doivent pas être utilisées dans de nouvelles applications.  
  
## <a name="features-not-supported-in-the-next-version-of-includessnoversionincludesssnoversion-mdmd"></a>Fonctionnalités non prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
 Les fonctionnalités suivantes du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] ne seront pas prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Évitez d'utiliser ces fonctionnalités dans vos nouveaux développements et modifiez dès que possible les applications qui y ont recours. La colonne Nom de la fonctionnalité apparaît dans les événements de suivi comme ObjectName, et dans les compteurs de performance et sys.dm_os_performance_counters comme nom_instance. L'ID de la fonctionnalité apparaît dans les événements de trace comme ObjectId.  
  
|Catégorie|Fonctionnalité déconseillée|Remplacement|Nom de la fonctionnalité|ID de la fonctionnalité|  
|--------------|------------------------|-----------------|------------------|----------------|  
|Programmabilité des données|[Sys.soap_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-soap-endpoints-transact-sql)|Windows Communications Foundation (WCF) ou ASP.NET|Services Web XML natifs|22|  
|Programmabilité des données|[Sys.endpoint_webmethods &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-endpoint-webmethods-transact-sql)|Windows Communications Foundation (WCF) ou ASP.NET|Services Web XML natifs|23|  
  
### <a name="slipstream-functionality"></a>Effectuer l'installation intégrée d'une fonctionnalité  
 La fonctionnalité Mise à jour de produit remplace la fonctionnalité Installation intégrée qui était disponible dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1. Par conséquent, les paramètres de ligne de commande, /*PCUSource* et /*CUSource*, associés à la fonctionnalité d'installation intégrée, ne doivent plus être utilisés. Les paramètres continueront de fonctionner mais peuvent être supprimés dans une version ultérieure du programme d'installation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Le paramètre /*UpdateSource* combine la fonctionnalité des paramètres d'installation intégrée /*PCUSource* et /*CUSource*.  
  
 Pour plus d’informations sur la fonctionnalité installation intégrée qui était disponible dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] PCU1, consultez [intégrer une mise à jour de SQL Server](http://go.microsoft.com/fwlink/?LinkId=219945) (http://go.microsoft.com/fwlink/?LinkId=219945).  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante](../../2014/getting-started/backward-compatibility.md)  
  
  
