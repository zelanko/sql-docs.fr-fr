---
title: Tables et procédures stockées de copie des journaux de transaction | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- secondary servers [SQL Server]
- monitor servers [SQL Server]
- log shipping [SQL Server], system tables
- log shipping [SQL Server], stored procedures
- primary servers [SQL Server]
ms.assetid: 03420810-4c38-4c0c-adf0-913eb044c50a
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fdc9d9c52af95f9b76c882befc9dfc3a1a218259
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169317"
---
# <a name="log-shipping-tables-and-stored-procedures"></a>Log Shipping Tables and Stored Procedures
  Cette rubrique décrit toutes les tables et procédures stockées associées à une configuration d'envoi de journaux. Toutes les tables liées à l’envoi de journaux sont stockées, sur chaque serveur, dans **msdb** . Le tableau ci-dessous décrit les tables et les procédures stockées utilisées par serveur, au sein d'une configuration d'envoi de journaux.  
  
## <a name="primary-server-tables"></a>Tables du serveur principal  
  
|Table de charge de travail|Description|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|Contient l'ID du travail d'alerte. Cette table est utilisée uniquement sur le serveur principal, dans le cas où aucun serveur moniteur distant n'a été configuré.|  
|[log_shipping_monitor_error_detail](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|Stocke le détail des erreurs des travaux d'envoi de journaux associés à ce serveur principal.|  
|[log_shipping_monitor_history_detail](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|Stocke le détail de l'historique des travaux d'envoi de journaux associés à ce serveur principal.|  
|[log_shipping_monitor_primary](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)|Stocke un enregistrement de surveillance pour cette base de données primaire.|  
|[log_shipping_primary_databases](/sql/relational-databases/system-tables/log-shipping-primary-databases-transact-sql)|Contient les informations de configuration des bases de données primaires d'un serveur donné. Stocke une ligne par base de données primaire.|  
|[log_shipping_primary_secondaries](/sql/relational-databases/system-tables/log-shipping-primary-secondaries-transact-sql)|Corrèle les bases de données primaires avec les bases de données secondaires.|  
  
## <a name="primary-server-stored-procedures"></a>Procédures stockées du serveur principal  
  
|Procédure stockée|Description|  
|----------------------|-----------------|  
|[sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)|Initialise la base de données primaire d'une configuration d'envoi de journaux, ce qui inclut le travail de sauvegarde, l'enregistrement de surveillance local, et l'enregistrement de surveillance distant.|  
|[sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql)|Ajoute une base de données secondaire à une base de données primaire existante.|  
|[sp_change_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql)|Modifie les paramètres de la base de données primaire, ce qui inclut l'enregistrement de surveillance local et l'enregistrement de surveillance distant.|  
|[sp_cleanup_log_shipping_history](/sql/relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql)|Purge l'historique localement et sur le moniteur, en fonction de la période de rétention.|  
|[sp_delete_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql)|Supprime l'envoi du journal de la base de données primaire, ce qui inclut le travail de sauvegarde ainsi que les historiques local et distant.|  
|[sp_delete_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql)|Supprime le nom d'une base de données secondaire d'une base de données primaire.|  
|[sp_help_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-database-transact-sql)|Extrait les paramètres de la base de données principale et affiche les valeurs des tables **log_shipping_primary_databases** et **log_shipping_monitor_primary** .|  
|[sp_help_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-primary-secondary-transact-sql)|Extrait les noms des bases de données secondaires d'une base de données principale.|  
|[sp_refresh_log_shipping_monitor](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)|Actualise le moniteur et affiche les informations les plus récentes relatives à l'agent d'envoi de journal spécifié.|  
  
## <a name="secondary-server-tables"></a>Tables du serveur secondaire  
  
|Table de charge de travail|Description|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|Contient l'ID du travail d'alerte. Cette table est utilisée uniquement sur le serveur secondaire, dans le cas où aucun serveur moniteur distant n'a été configuré.|  
|[log_shipping_monitor_error_detail](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|Stocke le détail des erreurs des travaux d'envoi de journaux associés à ce serveur secondaire.|  
|[log_shipping_monitor_history_detail](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|Stocke le détail de l'historique des travaux d'envoi de journaux associés à ce serveur secondaire.|  
|[log_shipping_monitor_secondary](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql)|Stocke un enregistrement de surveillance par base de données secondaire associée à ce serveur secondaire.|  
|[log_shipping_secondary](/sql/relational-databases/system-tables/log-shipping-secondary-transact-sql)|Contient les informations de configuration des bases de données secondaires d'un serveur donné. Stoke une ligne par ID secondaire.|  
|[log_shipping_secondary_databases](/sql/relational-databases/system-tables/log-shipping-secondary-databases-transact-sql)|Stocke les informations de configuration d'une base de données secondaire donnée. Stoke une ligne par base de données secondaire.|  
  
> [!NOTE]  
>  Les bases de données secondaires d’une base de données primaire donnée, situées sur le même serveur secondaire, partagent les paramètres de la table **log_shipping_secondary** . Si un paramètre partagé est modifié pour une base de données secondaire, la modification est effectuée pour l'ensemble des bases de données secondaires.  
  
## <a name="secondary-server-stored-procedures"></a>Procédures stockées du serveur secondaire  
  
|Procédure stockée|Description|  
|----------------------|-----------------|  
|[sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql)|Initialise une base de données secondaire pour l'envoi de journaux.|  
|[sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql)|Initialise les informations liées au serveur principal, ajoute des liens de surveillance local et distant, et crée des travaux de copie et de restauration sur le serveur secondaire pour la base de données primaire spécifiée.|  
|[sp_change_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-database-transact-sql)|Modifie les paramètres de la base de données secondaire, ce qui inclut les enregistrements de surveillance local et distant.|  
|[sp_change_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-secondary-primary-transact-sql)|Modifie les paramètres de la base de données secondaire, tels que les répertoires sources et de destination, et la période de rétention des fichiers.|  
|[sp_cleanup_log_shipping_history](/sql/relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql)|Purge l'historique localement et sur le moniteur, en fonction de la période de rétention.|  
|[sp_delete_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql)|Supprime une base de données secondaire, ainsi que les historiques local et distant.|  
|[sp_delete_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-primary-transact-sql)|Supprime les informations relatives au serveur principal spécifié du serveur secondaire.|  
|[sp_help_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-database-transact-sql)|Extrait les paramètres des bases de données secondaires à partir des tables **log_shipping_secondary**, **log_shipping_secondary_databases**et **log_shipping_monitor_secondary** .|  
|[sp_help_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-secondary-primary-transact-sql)|Cette procédure stockée récupère les paramètres d'une base de données primaire donnée sur le serveur secondaire.|  
|[sp_refresh_log_shipping_monitor](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql)|Actualise le moniteur et affiche les informations les plus récentes relatives à l'agent d'envoi de journal spécifié.|  
  
## <a name="monitor-server-tables"></a>Tables du serveur moniteur  
  
|Table de charge de travail|Description|  
|-----------|-----------------|  
|[log_shipping_monitor_alert](/sql/relational-databases/system-tables/log-shipping-monitor-alert-transact-sql)|Contient l'ID du travail d'alerte.|  
|[log_shipping_monitor_error_detail](/sql/relational-databases/system-tables/log-shipping-monitor-error-detail-transact-sql)|Stocke les détails des erreurs des opérations de copie des journaux de transaction.|  
|[log_shipping_monitor_history_detail](/sql/relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql)|Stocke le détail de l'historique des travaux d'envoi de journaux.|  
|[log_shipping_monitor_primary](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql)|Stocke un enregistrement de surveillance par base de données primaire associée à ce serveur moniteur.|  
|[log_shipping_monitor_secondary](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql)|Stocke un enregistrement de surveillance par base de données secondaire associée à ce serveur moniteur.|  
  
## <a name="monitor-server-stored-procedures"></a>Procédures stockées du serveur moniteur  
  
|Procédure stockée|Description|  
|----------------------|-----------------|  
|[sp_add_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql)|Crée un travail d'alerte pour l'envoi de journaux si aucun n'a encore été créé.|  
|[sp_delete_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-delete-log-shipping-alert-job-transact-sql)|Supprime un travail d'alerte pour l'envoi de journaux si aucune base de données primaire associée n'existe.|  
|[sp_help_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-alert-job-transact-sql)|Retourne l'ID du travail d'alerte.|  
|[sp_help_log_shipping_monitor_primary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql)|Retourne les enregistrements d’analyse de la base de données primaire spécifiée, à partir de la table **log_shipping_monitor_primary** .|  
|[sp_help_log_shipping_monitor_secondary](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql)|Retourne les enregistrements d’analyse de la base de données secondaire définie depuis la table **log_shipping_monitor_secondary** .|  
  
  
