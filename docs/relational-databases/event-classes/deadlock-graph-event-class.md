---
title: "Classe d&#39;&#233;v&#233;nements Deadlock Graph | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Deadlock Graph (classe d'événements)"
ms.assetid: 20f92233-c912-4382-8993-8e2e23d03fbe
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Classe d&#39;&#233;v&#233;nements Deadlock Graph
  La classe d’événements **Deadlock Graph** fournit une description XML d’un interblocage. Cette classe a lieu en même temps que la classe d’événements **Lock:Deadlock**.  
  
## Colonnes de la classe d'événements Deadlock Graph  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|Type d’événement = 148.|27|Non|  
|**EventSequence**|**int**|Séquence d'un événement donné au sein de la demande.|51|Non|  
|**IsSystem**|**int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur. Cette valeur est toujours égale à 1 pour cet événement.|60|Oui|  
|**LoginName**|**nvarchar**|Nom de la connexion de l’utilisateur (soit la connexion de sécurité [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], soit les informations d’identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur). Cette valeur est toujours l'utilisateur du système pour cet événement.|11|Oui|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur. Cette valeur est toujours le SID de l'utilisateur du système pour cet événement.|41|Oui|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure de détection du blocage.|14|Oui|  
|**TextData**|**ntext**|Description XML du blocage.|1|Oui|  
|**TransactionID**|**bigint**|Non utilisé.|4|Oui|  
  
## Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Classe d'événements Lock:Deadlock](../../relational-databases/event-classes/lock-deadlock-event-class.md)  
  
  