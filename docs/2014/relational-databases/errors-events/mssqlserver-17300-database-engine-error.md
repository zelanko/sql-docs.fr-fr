---
title: MSSQLSERVER_17300 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17300 (Database Engine error)
ms.assetid: c1d6bfb6-28af-4df6-8087-25807602d282
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a6577ec13cc990eb65d66eb2975d61b5f1147201
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62915348"
---
# <a name="mssqlserver_17300"></a>MSSQLSERVER_17300
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|17300|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PROC_OUT_OF_SYSTASK_SESSIONS|  
|Texte du message|SQL Server n'a pas pu exécuter une nouvelle tâche système, soit parce que la mémoire est insuffisante, soit parce que le nombre de sessions configurées dépasse le nombre maximal autorisé sur le serveur. Vérifiez que le serveur dispose de la mémoire adéquate. Utilisez sp_configure avec l'option « User connections » pour spécifier le nombre maximal de connexions utilisateur autorisées. Utilisez sys.dm_exec_sessions pour vérifier le nombre actuel de sessions, y compris les processus utilisateur.|  
  
## <a name="explanation"></a>Explication  
 Une tentative d'exécution d'une nouvelle tâche système a échoué à cause d'une insuffisance de mémoire ou d'un dépassement du nombre de sessions configurées sur le serveur.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que le serveur dispose de suffisamment de mémoire. Vérifiez le nombre actuel de tâches système en utilisant sys.dm_exec_sessions et vérifiez la valeur configurée du maximum de connexions utilisateur en utilisant sp_configure.  
  
 Effectuez les tâches suivantes comme il convient :  
  
-   Ajoutez de la mémoire au serveur.  
  
-   Mettez fin à une ou plusieurs sessions.  
  
-   Augmentez le nombre maximal de connexions utilisateur autorisées sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sys. dm_exec_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql)   
 [Configurer l’option de configuration de serveur User connections](../../database-engine/configure-windows/configure-the-user-connections-server-configuration-option.md)   
 [KILL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/kill-transact-sql)  
  
  
