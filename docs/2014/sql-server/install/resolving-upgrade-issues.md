---
title: Résolution des problèmes de mise à niveau | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- installing Upgrade Advisor
- Upgrade Advisor [SQL Server], reference
- component issue resolution [Upgrade Advisor]
- resolving upgrade issues
- upgrade blocks [Upgrade Advisor]
- detecting upgrade issues
- finding upgrade issues
- Upgrade Advisor [SQL Server], blocking issues
- configurations preventing upgrading [Upgrade Advisor]
- locating upgrade issues
- blocking issues [Upgrade Advisor]
- issues preventing upgrading [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, reference
- analyzing system [Upgrade Advisor], resolving issues
- settings preventing upgrading [Upgrade Advisor]
- upgrade issue reference [Upgrade Advisor]
- identifying upgrade issues
- fixing upgrade issues [Upgrade Advisor]
ms.assetid: 113eb435-8d36-4ed6-9790-b5e4c14809c8
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6072fb3c1d52048832bd6d07f34828c84eb2d491
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051411"
---
# <a name="resolving-upgrade-issues"></a>Résolution de problèmes de mise à niveau
  Les rubriques dans cette section décrivent les problèmes de mise à niveau qui peuvent être détectés ainsi que ceux qui ne peuvent pas être détectés mais sont susceptibles d'affecter la mise à niveau ou les fonctionnalités après la mise à niveau. Les problèmes sont organisés par composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Problèmes de mise à niveau de dernière minute](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [Problèmes de mise à niveau de recherche en texte intégral](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [Problèmes de mise à niveau de réplication](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [Problèmes de mise à niveau Reporting Services &#40;le Conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [Problèmes de mise à niveau de SQL Server Agent](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a>Problèmes qui empêchent la mise à niveau  
 Quelques configurations ou paramètres d'une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent vous empêcher d'effectuer une mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Si le programme d’installation détecte ces problèmes lorsque vous installez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], le programme d’installation arrête le processus de mise à niveau et que vous exécutez le Conseiller de mise à niveau et corrigez les problèmes de blocage des demandes.  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 Si les tâches suivantes sont répertoriées dans le rapport de mise à niveau du [!INCLUDE[ssDE](../../includes/ssde-md.md)], vous devez effectuer les actions requises avant de procéder à la mise niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] :  
  
-   [Détachez la base de données ID 32767](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [Renommer les connexions correspondant aux noms de rôle de serveur fixe](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [Renommer l’utilisateur système](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [Utiliser sp_rename pour renommer le nom de l’index en double](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
