---
title: MSqreader_history (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSqreader_history
- MSqreader_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSqreader_history system table
ms.assetid: c5c91d39-513c-4a77-870b-c8ef74a1cd6b
author: stevestein
ms.author: sstein
ms.openlocfilehash: f21873e8db662bc77bd1acbb5d48c6af49aba404
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032528"
---
# <a name="msqreaderhistory-transact-sql"></a>MSqreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le **MSqreader_history** table contient des lignes d’historique pour les Agents de lecture de file d’attente associée à un serveur de distribution local. Cette table est stockée dans la base de données de distribution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ID de l'Agent de lecture de la file d'attente.|  
|**publication_id**|**int**|ID de la publication.|  
|**runstatus**|**int**|État d'exécution de l'agent :<br /><br /> **1** = démarrage.<br /><br /> **2** = réussisse.<br /><br /> **3** = en cours d’exécution.<br /><br /> **4** = inactif.<br /><br /> **5** = nouvelle tentative.<br /><br /> **6** = échec.|  
|**start_time**|**datetime**|Date et heure du début de la session de l'Agent.|  
|**time**|**datetime**|Date et heure du dernier message enregistré.|  
|**duration**|**int**|Durée de l'activité enregistrée de la session, en secondes.|  
|**comments**|**nvarchar(255)**|Texte descriptif.|  
|**transaction_id**|**nvarchar(40)**|ID de transaction stocké avec le message, le cas échéant.|  
|**transaction_status**|**int**|L’état de la transaction.|  
|**transactions_processed**|**int**|Nombre total de transactions traitées pendant la session.|  
|**commands_processed**|**int**|Nombre total de commandes traitées pendant la session.|  
|**delivery_rate**|**float(53)**|Le nombre moyen des commandes transmises par seconde.|  
|**transaction_rate**|**float(53)**|Taux des transactions traitées.|  
|**subscriber** (Abonné)|**sysname**|Nom de l'Abonné.|  
|**SubscriberDB**|**sysname**|Le nom de la base de données d’abonnement.|  
|**error_id**|**int**|Si non égal à zéro, le nombre représente un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] message d’erreur.|  
|**timestamp**|**timestamp**|Colonne timestamp de cette table.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
