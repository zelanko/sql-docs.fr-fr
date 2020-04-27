---
title: Objets de messagerie de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], host databases
- Database Mail [SQL Server], messaging objects
- mail host databases [SQL Server]
- host databases [Database Mail]
ms.assetid: 5aa2886e-1db1-4066-85df-57ccf4538c54
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3657e45d18ac84ad737a016150692730f736b55f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62917702"
---
# <a name="database-mail-messaging-objects"></a>Objets de messagerie de base de données
  La base de données **msdb** est la base de données hôte de messagerie de base de données. Elle contient les procédures stockées et les objets de messagerie de la messagerie de base de données. Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] contient l'Assistant Configuration de la messagerie de base de données qui permet d'activer la messagerie de base de données, de créer et de gérer les profils et les comptes, et de configurer les options de la messagerie de base de données.  
  
##  <a name="objects-in-msdb-database"></a><a name="ComponentsAndConcepts"></a> Objets dans la base de données **msdb**  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] doit être activé dans la base de données **msdb** . Cependant, la messagerie de base de données n'utilise pas la mise en réseau [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Par conséquent, les utilisateurs ne sont pas obligés de créer un point de terminaison [!INCLUDE[ssSB](../../includes/sssb-md.md)] pour utiliser la messagerie de base de données. Le processus de messagerie de base de données externe utilise une connexion [!INCLUDE[vstecado](../../includes/vstecado-md.md)] standard pour communiquer avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La messagerie de base de données expose les objets suivants dans la base de données **msdb** lorsque la messagerie de base de données est activée.  
  
 Ces objets sont l'interface de la messagerie de base de données au sein de la base de données hôte de messagerie. D'autres objets sont installés pour implémenter les fonctions proposées par les objets répertoriés ci-dessus. Cependant, ces objets sont réservés à une utilisation interne.  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|[sysmail_allitems &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-allitems-transact-sql)|`View`|Liste tous les messages soumis à la messagerie de base de données.|  
|[sysmail_event_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql)|`View`|Liste les messages sur le comportement du [Database Mail External Program](database-mail-external-program.md).|  
|[sysmail_faileditems &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-faileditems-transact-sql)|`View`|Informations sur les messages que la messagerie de base de données n'a pas pu envoyer|  
|[sysmail_mailattachments &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql)|`View`|Informations sur les pièces jointes aux messages de la messagerie de base de données.|  
|[sysmail_sentitems &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-sentitems-transact-sql)|`View`|Informations sur les messages envoyés au moyen de la messagerie de base de données.|  
|[sysmail_unsentitems &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql)|`View`|Informations sur les messages que la messagerie de base de données est en train d'envoyer|  
|[sp_send_dbmail &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql)|`Stored Procedure`|Envoie des messages électroniques à l'aide de la messagerie de base de données.|  
|[sysmail_delete_log_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql)|`Stored Procedure`|Efface les messages du journal de la messagerie de base de données.|  
|[sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql)|`Stored Procedure`|Efface les messages de la file d'attente de la messagerie de base de données.|  
|[sysmail_help_status_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-help-status-sp-transact-sql)|`Stored Procedure`|Indique si la messagerie de base de données est démarrée.|  
|[sysmail_start_sp (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql)|`Stored Procedure`|Démarre les objets Service Broker utilisés par le programme externe. Ces objets sont démarrés par défaut.|  
|[sysmail_stop_sp (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql)|`Stored Procedure`|Arrête les objets Service Broker utilisés par le programme externe.|  
  

  
## <a name="see-also"></a>Voir aussi  
 [Database Mail](database-mail.md)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
