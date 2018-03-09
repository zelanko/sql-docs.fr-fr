---
title: MSSQLSERVER_2575 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 2575 (Database Engine error)
ms.assetid: 92dfe449-a122-4730-942b-e1d319862d20
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 806a9086dcbe4ebbe229293a90e40769fa2ef3b3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver2575"></a>MSSQLSERVER_2575
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2575|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_IAM_PAGE_WAS_NOT_SEEN|  
|Texte du message|La page IAM (Index Allocation Map) P_ID1 est désignée par le prochain pointeur de la page IAM P_ID2 dans l'ID d'objet O_ID, ID d'index I_ID, ID de partition PN_ID, ID d'unité d'allocation A_ID (type TYPE), mais elle n'a pas été détectée lors de l'analyse.|  
  
## <a name="explanation"></a>Explication  
Une page IAM (Index Allocation Map) a été trouvée pour l'index spécifié ; toutefois, la page IAM pour son pointeur de page suivante reste introuvable.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
### <a name="look-for-hardware-failure"></a>Rechercher une défaillance matérielle  
Exécutez les diagnostics matériels et corrigez les éventuels problèmes rencontrés. Examinez également les journaux système et des applications de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, ainsi que le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vérifier si l'erreur est due à une défaillance matérielle. Corrigez les éventuels problèmes matériels contenus dans les journaux.  
  
Si vous avez des problèmes persistants de données endommagées, tentez d'échanger votre ordinateur, vos contrôleurs et vos lecteurs de disque contre d'autres composants. Assurez-vous que votre système n'a pas une mémoire cache d'écriture active sur le contrôleur de disque. Si vous soupçonnez qu’il s’agit là de la source du problème, contactez votre fournisseur de matériel.  
  
Enfin, il peut s'avérer bénéfique d'utiliser un matériel totalement nouveau, avec reformatage des lecteurs de disque et réinstallation du système d'exploitation.  
  
### <a name="restore-from-backup"></a>Restaurer à partir de la sauvegarde  
Si le problème n'est pas matériel et si une restauration réputée en bon état est disponible, restaurez la base de données à partir de la sauvegarde.  
  
### <a name="run-dbcc-checkdb"></a>Exécuter DBCC CHECKDB  
Si aucune sauvegarde saine n'est disponible, exécutez DBCC CHECKDB sans clause REPAIR afin de déterminer l'étendue de l'altération. DBCC CHECKDB recommande une clause REPAIR à utiliser. Puis, exécutez DBCC CHECKDB avec la clause REPAIR adéquate afin de réparer les dommages.  
  
> [!CAUTION]  
> Si vous n'êtes pas sûr de l'effet de DBCC CHECKDB avec une clause REPAIR sur vos données, contactez l'assistance technique avant d'exécuter cette instruction.  
  
Si l'exécution de DBCC CHECKDB avec une des clauses REPAIR ne résout pas le problème, contactez l’assistance technique.  
  
#### <a name="results-of-running-repair-options"></a>Résultats de l'exécution des options REPAIR  
DBCC reconstruira l'index.  
  
## <a name="see-also"></a>Voir aussi  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  
