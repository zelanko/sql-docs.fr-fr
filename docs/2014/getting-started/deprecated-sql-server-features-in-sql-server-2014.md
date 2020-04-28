---
title: Fonctionnalités de SQL Server dépréciées dans SQL Server 2014 | Microsoft Docs
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
ms.openlocfilehash: 44fbab98aa017be66cd4dc369a713f44e8d248d5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75228215"
---
# <a name="deprecated-sql-server-features-in-sql-server-2014"></a>Fonctionnalités SQL Server déconseillées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités déconseillées qui sont toujours disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Il est prévu que ces fonctionnalités soient supprimées dans une prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Les fonctions déconseillées ne doivent pas être utilisées dans de nouvelles applications.  
  
## <a name="features-not-supported-in-the-next-version-of-ssnoversion"></a>Fonctionnalités non prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
 Les fonctionnalités suivantes du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] ne seront pas prises en charge dans la prochaine version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Évitez d'utiliser ces fonctionnalités dans vos nouveaux développements et modifiez dès que possible les applications qui y ont recours. La colonne Nom de la fonctionnalité apparaît dans les événements de suivi comme ObjectName, et dans les compteurs de performance et sys.dm_os_performance_counters comme nom_instance. L'ID de la fonctionnalité apparaît dans les événements de trace comme ObjectId.  
  
|Category|Fonctionnalité déconseillée|Remplacement|Nom de la fonctionnalité|ID de la fonctionnalité|  
|--------------|------------------------|-----------------|------------------|----------------|  
|Programmabilité des données|[sys. soap_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-soap-endpoints-transact-sql)|Windows Communications Foundation (WCF) ou ASP.NET|Services Web XML natifs|22|  
|Programmabilité des données|[sys. endpoint_webmethods &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-endpoint-webmethods-transact-sql)|Windows Communications Foundation (WCF) ou ASP.NET|Services Web XML natifs|23|  
  
### <a name="slipstream-functionality"></a>Effectuer l'installation intégrée d'une fonctionnalité  
 La [fonctionnalité de mise à jour du produit](/previous-versions/sql/sql-server-2012/hh231670(v=sql.110)?redirectedfrom=MSDN) a été introduite dans SQL Server 2012 en tant qu’extension de [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] la fonctionnalité Slipstream qui était disponible dans PCU1. Dans SQL Server 2014, la fonctionnalité de mise à jour de produit est la méthode recommandée pour l’intégration des SQL Server. Par conséquent, les paramètres de ligne de commande,/*PCUSource* et/*CUSource*, associés à la fonctionnalité d’intégration d’origine, ne doivent plus être utilisés. Ces paramètres continuent de fonctionner, mais peuvent être supprimés dans une version ultérieure du [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] programme d’installation. Le paramètre recommandé pour utiliser est/*UpdateSource* , qui combine les fonctionnalités des paramètres d’intégration d’origine,/*PCUSource* et/*CUSource*.  
  
 Pour plus d’informations sur les fonctionnalités d’intégration qui [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] étaient disponibles dans PCU1, consultez [Slipstream a SQL Server Update](https://go.microsoft.com/fwlink/?LinkId=219945) (https://go.microsoft.com/fwlink/?LinkId=219945).  
 Pour plus d’informations sur l’utilisation de/*UpdateSource* pour intégrer SQL Server builds, reportez-vous aux éléments suivants :
 
 - [Procédure de correction du programme d’installation de SQL Server 2012 avec un package d’installation mis à jour (à l’aide de UpdateSource pour obtenir une installation intelligente)](https://blogs.msdn.microsoft.com/jason_howell/2012/08/28/how-to-patch-sql-server-2012-setup-with-an-updated-setup-package-using-updatesource-to-get-a-smart-setup/)
 
 - [Le programme d’installation de SQL Server 2012 a simplement été plus intelligent...](https://techcommunity.microsoft.com/t5/SQL-Server-Support/SQL-Server-2012-Setup-just-got-smarter-8230/ba-p/317440)
 
## <a name="see-also"></a>Voir aussi  
 [Compatibilité descendante](../../2014/getting-started/backward-compatibility.md)  
  
  
