---
title: Surveiller la copie des journaux de transaction (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], status
- history tables [SQL Server]
- historical information [SQL Server], log shipping
- log shipping [SQL Server], monitoring
- alerts [SQL Server], log shipping
- status information [SQL Server], log shipping
- monitoring log shipping [SQL Server]
ms.assetid: acf3cd99-55f7-4287-8414-0892f830f423
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d480fe510b6d2e252faefaae13d7dd3776c8ec5d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62774883"
---
# <a name="monitor-log-shipping-transact-sql"></a>Surveiller la copie des journaux de transaction (Transact-SQL)
  Une fois l'envoi de journaux configuré, vous pouvez contrôler les informations d'état de l'ensemble des serveurs d'envoi de journaux. L'historique et l'état des opérations d'envoi de journaux sont toujours enregistrés localement par les travaux d'envoi de journaux. L'historique et l'état de l'opération de sauvegarde sont stockés sur le serveur principal, tandis que l'historique et l'état des opérations de copie et de restauration sont stockés sur le serveur secondaire. Si vous avez implémenté un serveur moniteur distant, ces informations sont également stockées sur le serveur moniteur.  
  
 Vous pouvez définir des alertes qui se déclenchent si les opérations d'envoi de journaux ne sont pas exécutées conformément à la planification. Les erreurs sont signalées par un travail d'alerte qui surveille l'état des opérations de sauvegarde et de restauration. Vous pouvez définir des alertes qui indiquent à l'opérateur l'occurrence de ces erreurs. Si un serveur moniteur est configuré, un travail d'alerte s'exécute sur le serveur moniteur qui signale les erreurs de toutes les opérations dans la configuration d'envoi des journaux. Si aucun serveur moniteur n'est défini, un travail d'alerte s'exécute sur l'instance du serveur principal qui surveille la sauvegarde. Si aucun serveur moniteur n'est défini, un travail d'alerte s'exécute également sur chaque instance de serveur secondaire pour surveiller les opérations de copie et de restauration.  
  
> [!IMPORTANT]  
>  Pour analyser une configuration d'envoi de journaux, vous devez ajouter le serveur moniteur lorsque vous activez l'envoi de journaux. Si vous ajoutez un serveur moniteur ultérieurement, vous devez supprimer la configuration d'envoi de journaux, puis la remplacer par une nouvelle configuration qui inclut un serveur moniteur. Pour plus d’informations, consultez [Configurer la copie des journaux de transaction &#40;Transact-SQL&#41;](configure-log-shipping-sql-server.md). Qui plus est, une fois le serveur moniteur configuré, il ne peut pas être modifié sans que l'envoi de journaux ne soit auparavant supprimé.  
  
## <a name="history-tables-containing-monitoring-information"></a>Tables d'historique contenant les informations d'analyse  
 Les tables d'historique d'analyse contiennent des métadonnées stockées sur le serveur moniteur. Une copie des informations spécifiques à un serveur principal ou secondaire est également stockée localement.  
  
 Vous pouvez interroger ces tables pour contrôler l'état d'une session d'envoi de journaux. Pour connaître l'état de l'envoi des journaux, par exemple, vérifiez l'état et l'historique du travail de sauvegarde, du travail de copie et du travail de restauration. Vous pouvez afficher un historique d'envoi de journaux et des informations d'erreur spécifiques en interrogeant les tables d'analyse.  
  
|Table de charge de travail|Description|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|Contient l'ID du travail d'alerte.|  
|[log_shipping_monitor_error_detail](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|Contient les informations d'erreur des travaux d'envoi des journaux. Vous pouvez interroger cette table pour identifier les erreurs d'une session d'agent. Vous pouvez également trier les erreurs en fonction de leurs date et heure d'enregistrement. Chaque erreur est consignée sous la forme d'une séquence d'exceptions, et plusieurs erreurs (séquences) peuvent être consignées pour chaque session d'agent.|  
|[log_shipping_monitor_history_detail](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|Contient l'historique des agents d'envoi de journaux. Vous pouvez interroger cette table pour consulter l'historique d'une session d'agent.|  
|[log_shipping_monitor_primary](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)|Contient un enregistrement d'analyse pour la base de données principale dans chaque configuration d'envoi de journaux, y compris des informations sur le dernier fichier de sauvegarde et le dernier fichier restauré, qui sont utiles pour l'analyse.|  
|[log_shipping_monitor_secondary](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql)|Contient un enregistrement d'analyse pour chaque base de données secondaire, y compris des informations sur le dernier fichier de sauvegarde et le dernier fichier restauré, qui sont utiles pour l'analyse.|  
  
## <a name="stored-procedures-for-monitoring-log-shipping"></a>Procédures stockées pour l'analyse de l'envoi des journaux  
 Les informations d’analyse et d’historique sont stockées dans des tables dans **msdb**, accessibles à l’aide de procédures stockées d’envoi de journaux. Exécutez les procédures stockées suivantes sur les serveurs indiqués dans le tableau ci-dessous.  
  
|Procédure stockée|Description|Serveur concerné|  
|----------------------|-----------------|---------------------------|  
|[sp_help_log_shipping_monitor_primary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql)|Retourne les enregistrements d’analyse de la base de données primaire spécifiée, à partir de la table **log_shipping_monitor_primary** .|Serveur moniteur ou serveur principal|  
|[sp_help_log_shipping_monitor_secondary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql)|Retourne les enregistrements d’analyse de la base de données secondaire définie depuis la table **log_shipping_monitor_secondary** .|Serveur moniteur ou serveur secondaire|  
|[sp_help_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-alert-job-transact-sql)|Retourne l'ID du travail d'alerte.|Serveur moniteur, serveur principal ou serveur secondaire si aucune surveillance n'est définie|  
|[sp_help_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql)|Extrait les paramètres de la base de données primaire et affiche les valeurs des tables **log_shipping_primary_databases** et **log_shipping_monitor_primary** .|Serveur principal|  
|[sp_help_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-secondary-transact-sql)|Extrait les noms des bases de données secondaires d'une base de données principale.|Serveur principal|  
|[sp_help_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql)|Extrait les paramètres des bases de données secondaires depuis les tables **log_shipping_secondary**, **log_shipping_secondary_databases** et **log_shipping_monitor_secondary** tables.|Serveur secondaire|  
|[sp_help_log_shipping_secondary_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-primary-transact-sql)|Cette procédure stockée récupère les paramètres d'une base de données primaire donnée sur le serveur secondaire.|Serveur secondaire|  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher le rapport de la copie des journaux de transaction &#40;SQL Server Management Studio&#41;](view-the-log-shipping-report-sql-server-management-studio.md)   
 [Tables et procédures stockées de copie des journaux de transaction](log-shipping-tables-and-stored-procedures.md)  
  
  
