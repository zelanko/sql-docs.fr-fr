---
title: Audit Fulltext, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 95e4c5fd-e16f-446e-b42b-105495a8f39a
author: stevestein
ms.author: sstein
ms.openlocfilehash: aa74d8aa90b677fe7ccd5fe2619e51506a0abe17
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053257"
---
# <a name="audit-fulltext-event-class"></a>Audit Fulltext, classe d'événements
  La classe d’événements **Audit Fulltext** se produit lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se connecte au processus de démon de filtre de texte intégral et communique avec lui.  
  
## <a name="audit-fulltext-event-class-data-columns"></a>Colonnes de données de la classe d'événements Audit Fulltext  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**Error**|**int**|Numéro de l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si cet événement signale une erreur.|31|Oui|  
|**EventSequence**|**int**|Séquence d'un événement donné au sein de la demande.|51|Non|  
|**EventSubClass**|**int**|Type de connexion utilisé par le compte de connexion. 1 = Non regroupé, 2 = Regroupé.|21|Oui|  
|**IsSystem**|**int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|**Success**|**int**|1 = réussite. 0 = échec. Exemple : 1 indique la réussite de la vérification d'autorisations, 0 l'échec de cette vérification.|23|Oui|  
|**TargetLoginName**|**int**|Pour les actions qui ciblent une connexion (l'ajout d'une nouvelle connexion, par exemple), le nom de la connexion ciblée.|42|Oui|  
|**TargetLoginSid**|**int**|Pour les actions qui ciblent une connexion (l'ajout d'une nouvelle connexion, par exemple), numéro d'identification de sécurité (SID) de la connexion ciblée.|43|Oui|  
|**TextData**|**ntext**|Informations de texte sur l'événement en texte intégral. Généralement ce champ fournit des informations sur la connexion entre le processus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le processus de démon de filtre de texte intégral|1|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
