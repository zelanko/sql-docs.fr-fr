---
title: log_shipping_monitor_error_detail (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_error_detail_TSQL
- log_shipping_monitor_error_detail
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_error_detail system table
ms.assetid: 0c38a625-60d2-4ee2-bcf3-2ba367914220
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e441e5165262a4455e34cb9a0adb55b9679578f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67990057"
---
# <a name="log_shipping_monitor_error_detail-transact-sql"></a>log_shipping_monitor_error_detail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stocke les détails des erreurs des opérations de copie des journaux de transaction. Cette table est stockée dans la base de données **msdb** .  
  
 Les tables liées à l'historique et à la surveillance sont également utilisées au niveau du serveur principal et des serveurs secondaires.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**uniqueidentifier**|ID principal pour la sauvegarde ou ID secondaire pour la copie ou la restauration.|  
|**agent_type**|**tinyint**|Type d'opération de copie des journaux de transaction.<br /><br /> 0 = Sauvegarde.<br /><br /> 1 = Copie.<br /><br /> 2 = Restauration.|  
|**session_id**|**int**|ID de session pour le travail de sauvegarde/copie/restauration.|  
|**database_name**|**sysname**|Nom de la base de données associée à cet enregistrement d'erreur. Base de données primaire pour la sauvegarde, base de données secondaire pour la restauration ou vide pour la copie.|  
|**sequence_number**|**int**|Numéro incrémentiel indiquant l'ordre correct des informations dans le cas d'erreurs qui s'étendent sur plusieurs enregistrements.|  
|**log_time**|**datetime**|Date et heure de création de l'enregistrement.|  
|**log_time_utc**|**datetime**|Date et heure de création de l'enregistrement, exprimée en heure UTC.|  
|**message**|**nvarchar**|Texte du message.|  
|**code**|**nvarchar**|Source du message d'erreur ou de l'événement.|  
|**help_url**|**nvarchar**|URL, si elle est disponible, qui permet de consulter des informations complémentaires à propos de l'erreur.|  
  
## <a name="remarks"></a>Notes  
 Cette table contient le détail des erreurs des agents de copie des journaux de transaction. Chaque erreur est enregistrée sous la forme d'une séquence d'exceptions. Il peut y avoir plusieurs erreurs (séquences) pour chaque session d'agent.  
  
 En plus d’être stockées sur le serveur moniteur distant, les informations relatives au serveur principal sont stockées sur le serveur principal dans la table **log_shipping_monitor_error_detail** , et les informations relatives à un serveur secondaire sont également stockées sur le serveur secondaire dans sa table **log_shipping_monitor_error_detail** .  
  
 Pour identifier une session d’agent, utilisez les colonnes **agent_id**, **agent_type**et **session_id**. Triez par **log_time** pour voir les erreurs dans l’ordre dans lequel elles ont été enregistrées.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux de &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [log_shipping_monitor_history_detail &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql.md)   
 [sp_cleanup_log_shipping_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql.md)   
 [sp_delete_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [Tables système &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
