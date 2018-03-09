---
title: MSSQLSERVER_7984 | Microsoft Docs
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
- 7984 (Database Engine error)
ms.assetid: e3192f56-e4e2-41da-b132-65f1e7540b1a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d19afab6a5c74088556a19763d3c456a11124df4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver7984"></a>MSSQLSERVER_7984
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|7984|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC2_PRE_CHECKS_BAD_PAGE_TYPE|  
|Texte du message|Pré-vérifications de table système : ID d'objet O_ID. La page P_ID possède un type de page PAGETYPE. Vérifiez l'instruction qui s'est arrêtée en raison d'une erreur irréparable.|  
  
## <a name="explanation"></a>Explication  
Une page avec un type autre que DATA_PAGE a été trouvée dans le niveau de données de l'objet spécifié. Cette erreur est générée au cours de la première phase des vérifications de la commande DBCC CHECKDB. Au cours de cette phase, DBCC CHECKDB effectue des vérifications primitives sur les pages de données des tables de base système critiques.  
  
> [!NOTE]  
> Si des erreurs sont détectées dans les tables système, les erreurs ne peuvent pas être réparées ; par conséquent, la commande DBCC CHECKDB se termine immédiatement.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
### <a name="look-for-hardware-failure"></a>Rechercher une défaillance matérielle  
Exécutez les diagnostics matériels et corrigez les éventuels problèmes rencontrés. Examinez également les journaux système et des applications de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, ainsi que le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vérifier si l'erreur est due à une défaillance matérielle. Corrigez les éventuels problèmes matériels contenus dans les journaux.  
  
Si vous avez des problèmes persistants de données endommagées, tentez d'échanger votre ordinateur, vos contrôleurs et vos lecteurs de disque contre d'autres composants. Assurez-vous que votre système n'a pas une mémoire cache d'écriture active sur le contrôleur de disque. Si vous soupçonnez qu’il s’agit là de la source du problème, contactez votre fournisseur de matériel.  
  
Enfin, il peut s'avérer bénéfique d'utiliser un matériel totalement nouveau, avec reformatage des lecteurs de disque et réinstallation du système d'exploitation.  
  
### <a name="restore-from-backup"></a>Restaurer à partir de la sauvegarde  
Si le problème n'est pas matériel et si une restauration réputée en bon état est disponible, restaurez la base de données à partir de la sauvegarde.  
  
### <a name="run-dbcc-checkdb"></a>Exécuter DBCC CHECKDB  
Non applicable. Cette erreur ne peut pas être réparée automatiquement. Si vous ne pouvez pas restaurer la base de données à partir d'une sauvegarde, contactez le service de support technique de [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
