---
title: "FT:Crawl Aborted, classe d’événements | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Crawl Aborted event class
ms.assetid: eead8ea6-5051-4689-ab30-4dfbfda01fb9
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fd6e356958e291ed4795ab923487919b5bb3a911
ms.lasthandoff: 04/11/2017

---
# <a name="ftcrawl-aborted-event-class"></a>FT:Crawl Aborted, classe d'événements
  La classe d’événements **FT:Crawl Aborted** indique qu’une exception s’est produite au cours d’une analyse de texte intégral. Cette erreur entraîne généralement l'arrêt de l'analyse de texte intégral. Pour plus de détails sur l'erreur, consultez le journal des événements [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ou le journal d'analyse.  
  
## <a name="ftcrawl-aborted-event-class-data-columns"></a>Colonnes de données de la classe d'événements FT:Crawl Aborted  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID de la base de données dans laquelle l'analyse de texte intégral est exécutée. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**Erreur**|**int**|Numéro d'erreur d'un événement donné. Il s’agit généralement du numéro d’erreur stocké dans la table **sysmessages** .|31|Oui|  
|**EventClass**|**int**|Type d’événement = 157.|27|Non|  
|**EventSequence**|**int**|Séquence d'un événement donné au sein de la demande.|51|Non|  
|**IsSystem**|**int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|**ObjectID**|**int**|ID attribué par le système à l'objet sur lequel l'analyse de texte intégral était exécutée lorsque l'échec a eu lieu.|22|Oui|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|**État**|**int**|Équivalent à un code d'état d'erreur.|30|Oui|  
|**TransactionID**|**bigint**|ID affecté par le système à la transaction.|4|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
