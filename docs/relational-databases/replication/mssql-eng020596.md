---
title: MSSQL_ENG020596 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG020596 error
ms.assetid: fa33627c-2e99-4be3-9424-52ab83446e07
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5eae24c46d8a92eb3906ba83ebac735c1ee563a9
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="mssqleng020596"></a>MSSQL_ENG020596
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|20596|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Seul '%1!' ou les membres de db_owner peuvent supprimer l'Agent anonyme.|  
  
## <a name="explanation"></a>Explication  
 Vous ne disposez pas des autorisations suffisantes pour supprimer l'agent pour l'abonnement anonyme. Le nom de connexion utilisé lors de l’appel de [sp_dropanonymousagent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropanonymousagent-transact-sql.md) doit être un membre du rôle de serveur fixe **sysadmin** sur le serveur de distribution ou du rôle de base de données fixe **db_owner** dans la base de données de distribution, ou bien l’utilisateur doit être celui qui a initié la première exécution de l’agent.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Connectez-vous avec les informations d'identification appropriées et exécutez **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
