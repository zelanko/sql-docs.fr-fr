---
title: MSSQLSERVER_2575 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2575 (Database Engine error)
ms.assetid: 92dfe449-a122-4730-942b-e1d319862d20
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81c6fb81b4099784ce9bd50c906eb3f496465d44
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551964"
---
# <a name="mssqlserver_2575"></a>MSSQLSERVER_2575
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|2575|  
|Source de l’événement|MSSQLSERVER|  
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
>  Si vous n'êtes pas sûr de l'effet de DBCC CHECKDB avec une clause REPAIR sur vos données, contactez l'assistance technique avant d'exécuter cette instruction.  
  
 Si l'exécution de DBCC CHECKDB avec une des clauses REPAIR ne résout pas le problème, contactez l’assistance technique.  
  
#### <a name="results-of-running-repair-options"></a>Résultats de l'exécution des options REPAIR  
 DBCC reconstruira l'index.  
  
## <a name="see-also"></a>Voir aussi  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
