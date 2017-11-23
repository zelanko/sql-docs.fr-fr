---
title: dbo.sysalerts (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 10/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysalerts
- sysalerts_TSQL
- dbo.sysalerts_TSQL
- sysalerts
dev_langs: TSQL
helpviewer_keywords: sysalerts system table
ms.assetid: a2c2f50d-61f3-4951-996a-add5ad092cc2
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a28a1152ec3dd85c8bee11c4ef9b73ed3928db27
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysalerts-transact-sql"></a>dbo.sysalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque alerte. Une alerte est un message envoyé en réponse à un événement. Elle peut transmettre des messages au-delà de l'environnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sous la forme d'un message électronique ou d'un radiomessage. Une alerte peut également générer une tâche.  Cette table est stockée dans le **msdb** base de données.
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identification de l'alerte|  
|**nom**|**sysname**|Nom de l’alerte.|  
|**event_source**|**nvarchar (100)**|Source de l'événement : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**event_category_id**|**int**|Réservé pour un usage ultérieur.|  
|**event_id**|**int**|Réservé pour un usage ultérieur.|  
|**message_id**|**int**|Utilisateur définis par l’ID de message ou une référence à **sysmessages** message qui déclenche cette alerte.|  
|**niveau de gravité**|**int**|Gravité de l'erreur qui déclenche cette alerte.|  
|**activé**|**tinyint**|État de l'alerte :<br /><br /> **0** = désactivé.<br /><br /> **1** = activé.|  
|**délai_entre_réponses**|**int**|Délai d'attente, en secondes, entre les notifications de cette alerte.|  
|**date_dernière_occurrence**|**int**|Dernière occurrence (date) de l'alerte.|  
|**heure_dernière_occurrence**|**int**|Dernière occurrence (heure) de l'alerte.|  
|**date_dernière_réponse**|**int**|Dernière notification (date) de l'alerte.|  
|**heure_dernière_réponse**|**int**|Dernière notification (heure) de l'alerte.|  
|**message_notification**|**nvarchar(512)**|Informations complémentaires envoyées avec l'alerte.|  
|**include_event_description**|**tinyint**|Masque de bits indiquant si la description de l’événement est envoyée par courrier électronique, radiomessagerie ou Net send. Consultez le tableau ci-dessous pour les valeurs.|  
|**database_name**|**nvarchar(512)**|Base de données dans laquelle cette alerte doit se produire pour déclencher cette alerte.|  
|**motclé_description_événement**|**nvarchar (100)**|Modèle auquel doit correspondre l'erreur pour déclencher l'alerte.|  
|**occurrence_count**|**int**|Nombre d'occurrences de cette alerte.|  
|**date_réinitialisation_compte**|**int**|Nombre de jours (date) sera réinitialisée à **0**.|  
|**heure_réinitialisation_compte**|**int**|Heure du nombre de jours sera réinitialisée à **0**.|  
|**job_id**|**uniqueidentifier**|Identificateur du travail exécuté lorsque l'alerte se produit.|  
|**has_notification**|**int**|Nombre d'opérateurs avertis par courrier électronique lorsque l'alerte a lieu.|  
|**indicateurs**|**int**|Réservé.|  
|**argument condition_performances**|**nvarchar(512)**|Réservé.|  
|**code catégorie**|**int**|Réservé.|  
  
 ## <a name="remarks"></a>Notes

Le tableau suivant montre les valeurs pour le masque de bits include_event_description. La valeur décimale est retournée par dbo.sysalerts. 

|decimal | binary | Signification |
|------|------|------|
|0 |0000 |Aucun message |
|1 |0001 |Messagerie |
|2 |0010 |récepteur de radiomessagerie |
|3 |0011 |récepteur de radiomessagerie et par courrier électronique |
|4 |0100 |Envoi réseau |
|5 |0101 |Courrier électronique et net send |
|6 |0110 |Récepteur de radiomessagerie et net send |
|7 |0111 |Courrier électronique, radiomessagerie et net send |
  
