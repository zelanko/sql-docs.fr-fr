---
title: "Audit Fulltext, classe d’événements | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: event-classes
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95e4c5fd-e16f-446e-b42b-105495a8f39a
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d1f0164eb5310d65a2048a65848ee641b2d489db
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2018
---
# <a name="audit-fulltext-event-class"></a>Audit Fulltext, classe d'événements
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
La classe d’événements **Audit Fulltext** se produit lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connecte au processus de démon de filtre de texte intégral et communique avec lui.  
  
## <a name="audit-fulltext-event-class-data-columns"></a>Colonnes de données de la classe d'événements Audit Fulltext  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**Erreur**|**Int**|Numéro de l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si cet événement signale une erreur.|31|Oui|  
|**EventSequence**|**Int**|Séquence d'un événement donné au sein de la demande.|51|non|  
|**EventSubClass**|**Int**|Type de connexion utilisé par le compte de connexion. 1 = Non regroupé, 2 = Regroupé.|21|Oui|  
|**IsSystem**|**Int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**Int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|**Réussi**|**Int**|1 = réussite. 0 = échec. Exemple : 1 indique la réussite de la vérification d'autorisations, 0 l'échec de cette vérification.|23|Oui|  
|**TargetLoginName**|**Int**|Pour les actions qui ciblent une connexion (l'ajout d'une nouvelle connexion, par exemple), le nom de la connexion ciblée.|42|Oui|  
|**TargetLoginSid**|**Int**|Pour les actions qui ciblent une connexion (l'ajout d'une nouvelle connexion, par exemple), numéro d'identification de sécurité (SID) de la connexion ciblée.|43|Oui|  
|**TextData**|**ntext**|Informations de texte sur l'événement en texte intégral. Généralement ce champ fournit des informations sur la connexion entre le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le processus de démon de filtre de texte intégral| 1|Oui|  
  
## <a name="see-also"></a> Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
