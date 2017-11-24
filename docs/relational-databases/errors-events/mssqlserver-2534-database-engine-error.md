---
title: MSSQLSERVER_2534 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 2534 (Database Engine error)
ms.assetid: 121cf99d-0722-494c-be24-3369c1a0badc
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9774b2d3a6f89479f2477545ec8fab6abbf79151
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver2534"></a>MSSQLSERVER_2534
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2534|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT|  
|Texte du message|Erreur de table : la page P_ID, dont l'en-tête indique qu'elle est assignée à l'ID d'objet O_ID, ID d'index I_ID, ID de partition PN_ID, ID d'unité d'allocation A_ID (type TYPE), est assignée par un autre objet.|  
  
## <a name="explanation"></a>Explication  
L’en-tête de la page contient l’ID d’unité d’allocation *A_ID*, mais aucune des pages IAM (Index Allocation Map) de cette unité d’allocation n’alloue la page. L'en-tête de la page ne contenant pas l'ID d'unité d'allocation correct, la page génère une erreur de correspondance MSSQLServer_2533 qui se réfère à l'ID d'unité d'allocation auquel la page est de fait allouée.  
  
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
  
### <a name="results-of-running-repair-options"></a>Résultats de l'exécution des options REPAIR  
REPAIR reconstruira l'index, si index il y a.  
  
> [!CAUTION]  
> Le fait d’exécuter REPAIR pour corriger l’erreur de correspondance [MSSQLSERVER_2533](~/relational-databases/errors-events/mssqlserver-2533-database-engine-error.md) libère la page avant la reconstruction.  
  
> [!CAUTION]  
> Cette réparation peut entraîner une perte de données.  
  
