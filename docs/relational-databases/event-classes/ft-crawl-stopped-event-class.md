---
title: "FT:Crawl Stopped, classe d’événements | Microsoft Docs"
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
- Crawl Stopped event class
ms.assetid: dbc91bf7-687c-4083-9694-02f3e102c175
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 46a5cacd714274edb441a64a92b441e964bb9303
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="ftcrawl-stopped-event-class"></a>FT:Crawl Stopped, classe d’événements
  La classe d’événements **:Crawl Stopped** indique qu’une analyse de texte intégral (remplissage) s’est arrêtée. L'arrêt peut être dû à l'achèvement réussi d'une analyse ou à une erreur irrécupérable.  
  
## <a name="ftcrawl-stopped-event-class-data-columns"></a>Colonnes de données de la classe d'événements FT:Crawl Stopped  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|ID de la base de données dans laquelle s'est arrêtée l'analyse de texte intégral. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**EventClass**|**int**|Type d’événement = 156.|27|Non|  
|**EventSequence**|**int**|Séquence d'un événement donné au sein de la demande.|51|Non|  
|**IsSystem**|**int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|**ObjectID**|**int**|ID affecté à l'objet par le système. L'analyse de texte intégral s'est arrêtée pour l'index de texte intégral sur cet objet.|22|Oui|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.|64|Oui|  
|**SPID**|**int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|**TransactionID**|**bigint**|ID affecté par le système à la transaction.|4|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
