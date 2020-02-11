---
title: MSSQLSERVER_1204 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1204 (Database Engine error)
ms.assetid: de6ece78-79de-484d-9224-ca0f7645815f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ee0544c14bbf3e05fcb59e16a9bb3e0d8e61e33b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62916100"
---
# <a name="mssqlserver_1204"></a>MSSQLSERVER_1204
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|1204|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LK_OUTOF|  
|Texte du message|L'instance du moteur de base de données SQL Server ne peut pas obtenir une ressource LOCK en ce moment. Réexécutez votre instruction lorsque le nombre d'utilisateurs actifs est moindre. Demandez à l'administrateur de base de données de vérifier la configuration du verrou et de la mémoire pour cette instance, ou de vérifier les longues transactions.|  
  
## <a name="explanation"></a>Explication  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas obtenir de ressource de verrouillage. Cela peut être dû à l'une des raisons suivantes :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas allouer plus de mémoire à partir du système d’exploitation, soit parce que d’autres processus l’utilisent, soit parce que le serveur fonctionne avec l’option **Mémoire maximum du serveur** configurée.  
  
-   Le gestionnaire de verrous n'utilisera pas plus de 60 % de la mémoire disponible pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si vous pensez que SQL Server ne peut pas allouer suffisamment de mémoire, essayez de procéder comme suit :  
  
-   Si des applications autres que SQL Server consomment des ressources, essayez d'arrêter ces applications ou envisagez de les exécuter sur un serveur distinct. Cela libérera de la mémoire à partir d'autres processus pour SQL Server.  
  
-   Si vous avez configuré l'option max server memory, augmentez la valeur de ce paramètre.  
  
 Si vous pensez que le gestionnaire de verrous a utilisé la quantité maximale de mémoire disponible, identifiez la transaction qui maintient le plus de verrous et mettez-y fin. Le script ci-dessous identifiera la transaction avec le plus de verrous :  
  
```  
SELECT request_session_id, COUNT (*) num_locks  
FROM sys.dm_tran_locks  
GROUP BY request_session_id   
ORDER BY count (*) DESC  
```  
  
 Considérez l'ID de session le plus élevé et mettez-y fin à l'aide de la commande KILL.  
  
  
