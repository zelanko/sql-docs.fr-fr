---
title: SYSSUBSCRIPTIONS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- syssubscriptions_TSQL
- syssubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syssubscriptions system table
ms.assetid: 106c1707-e0e0-49b4-ba50-25380c40fab2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 251dbb143c1b5aa150cc094ce67943dd0139ee6d
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305013"
---
# <a name="syssubscriptions-transact-sql"></a>syssubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque abonnement de la base de données. Cette table est stockée dans la base de données de publication.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**Int**|ID unique d'un article|  
|**srvid**|**smallint**|ID de serveur de l’abonné.|  
|**dest_db**|**sysname**|Nom de la base de données de destination|  
|**status**|**tinyint**|État de l’abonnement :<br /><br /> **0** = inactif.<br /><br /> **1** = abonné.<br /><br /> **2** = actif.|  
|**sync_type**|**tinyint**|Type de synchronisation initiale :<br /><br /> **1** = automatique.<br /><br /> **2** = aucun|  
|**login_name**|**sysname**|Nom d’accès utilisé lors de l’ajout de l’abonnement|  
|**subscription_type**|**Int**|Type d’abonnement :<br /><br /> 0 = Par envoi de données (push) - l'agent de distribution s'exécute sur le serveur de distribution.<br /><br /> 1 = Par extraction de données (pull) - l'agent de distribution s'exécute sur l'Abonné.|  
|**distribution_jobid**|**binary(16)**|ID du travail de l'Agent de distribution|  
|**timestamp**|**timestamp**|Cachet temporel|  
|**update_mode**|**tinyint**|Mode de mise à jour :<br /><br /> **0** = lecture seule.<br /><br /> **1** = mise à jour immédiate.|  
|**loopback_detection**|**bit**|S'applique aux abonnements qui font partie d'une topologie de réplication transactionnelle bidirectionnelle. La détection de boucle détermine si l'Agent de distribution renvoie à l'Abonné les transactions émanant de ce dernier :<br /><br /> **0** = renvoie.<br /><br /> **1** = n’est pas renvoyé.|  
|**queued_reinit**|**bit**|Indique si l'article est marqué pour l'initialisation ou la réinitialisation. La valeur **1** indique que l’article souscrit est marqué pour l’initialisation ou la réinitialisation.|  
|**nosync_type**|**tinyint**|Type d'initialisation de l'abonnement :<br /><br /> **0** = automatique (instantané)<br /><br /> **1** = prise en charge de la réplication uniquement<br /><br /> **2** = initialiser avec la sauvegarde<br /><br /> **3** = initialiser à partir du numéro séquentiel dans le journal (LSN)<br /><br /> Pour plus d’informations, consultez le paramètre **\@sync_type** de [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md).|  
|**srvname**|**sysname**|Nom de l'Abonné.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables &#40;de réplication Transact&#41;-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
