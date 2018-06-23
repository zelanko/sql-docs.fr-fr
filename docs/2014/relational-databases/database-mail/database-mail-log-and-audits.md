---
title: Journal et audits de la messagerie de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- auditing [SQL Server]
- Database Mail [SQL Server], auditing
- logs [Database Mail]
- audits [SQL Server], Database Mail
- Database Mail [SQL Server], logging
ms.assetid: 846589ee-5fe5-4ab3-b335-0c253e569f99
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: aa41082daa7b0a80e613158b83c7dddb313502a0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044236"
---
# <a name="database-mail-log-and-audits"></a>Journal et audits de la messagerie de base de données
  La fonctionnalité de journalisation de la messagerie de base de données offre un moyen d'isoler et de résoudre les problèmes. La messagerie de base de données stocke les informations du journal dans la base de données **msdb** . Les informations sur le contenu des messages électroniques de la messagerie de base de données, l'état des messages électroniques et tous les messages reçus (notamment les erreurs) sont enregistrées par la messagerie de base de données et peuvent être utilisées à des fins de dépannage et d'audit.  
  
## <a name="database-mail-logs"></a>Journaux de la messagerie de base de données  
 Les tables de la base de données **msdb** journalisent les informations en provenance du [Programme externe de la messagerie de base de données](database-mail-external-program.md). Dans [Vues de la messagerie de base de données &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/database-mail-views-transact-sql), des tables sont exposées à des fins de dépannage. Des erreurs apparaissent dans la vue [sysmail_event_log &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sysmail-event-log-transact-sql) si Service Broker ne peut pas activer le programme externe, si celui-ci rencontre des erreurs réseau ou si le serveur SMTP (Simple Mail Transport Protocol) refuse un message électronique. Si le programme externe ne peut pas se connecter aux tables **msdb**, il consigne les erreurs dans le journal des événements des applications Windows.  
  
 Les tables internes de la base de données **msdb** contiennent les messages électroniques et les pièces jointes envoyés depuis la messagerie de base de données, ainsi que l’état actuel de chaque message. La messagerie de base de données met ces tables à jour chaque fois qu'un message est traité.  
  
## <a name="database-mail-auditing-tasks"></a>Tâches d'audit de la messagerie de base de données  
  
|||  
|-|-|  
|**Vérification et gestion des journaux de la messagerie de base de données**|**Lien vers la rubrique**|  
|Vérifier l'état de remise d'un message individuel|[Vérifier l'état des messages électroniques envoyés avec la messagerie de base de données](check-the-status-of-e-mail-messages-sent-with-database-mail.md)|  
|Nettoyer les messages, les pièces jointes et les entrées de journal de la messagerie de base de données|[sysmail_delete_mailitems_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql)<br /><br /> [sysmail_delete_log_sp &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sysmail-delete-log-sp-transact-sql)|  
|Archiver les messages et les journaux de la messagerie de base de données|[Créer un travail d'Agent SQL Server pour archiver les messages et les journaux d'événements de la messagerie de base de données](create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
