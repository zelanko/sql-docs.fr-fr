---
title: Degree of Parallelism (7.0 Insert), classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Degree of Parallelism event class
ms.assetid: 6753ef30-890f-47a3-b0b6-8abb184e1d83
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 56a87741b104a49f98a3cba05dc65d911774774d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62662897"
---
# <a name="degree-of-parallelism-70-insert-event-class"></a>Classe d'événements Degree of Parallelism (7.0 Insert)
  La classe d’événements **Degree of Parallelism (7.0 Insert)** se produit lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécute une instruction SELECT, INSERT, UPDATE ou DELETE.  
  
 Lorsque cette classe d'événements est incluse dans une trace, la surcharge impliquée peut sensiblement entraver les performances si ces événements se produisent fréquemment. Pour minimiser l'effet d'une telle charge, limitez l'utilisation de cette classe d'événements aux traces destinées à effectuer le suivi de problèmes précis pour de brèves durées.  
  
## <a name="degree-of-parallelism-70-insert-event-class-data-columns"></a>Colonnes de données de la classe d'événements Degree of Parallelism (7.0 Insert)  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|**BinaryData**|**image**|Nombre d'UC utilisées pour effectuer le processus sur la base des valeurs suivantes :<br /><br /> 0x00000000: Indique un plan en série en cours d’exécution en série.<br /><br /> 0 x 01000000 indique un plan parallèle en cours d’exécution en série.<br /><br /> > = 0 x 02000000 : Indique un plan parallèle en cours d’exécution en parallèle.|2|Non|  
|**ClientProcessID**|**Int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|**DatabaseID**|**Int**|ID de la base de données spécifiée par l'instruction de base de données USE ou celui de la base de données par défaut si aucune instruction de base de données USE n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**DatabaseName**|**nvarchar**|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|**Classe d'événements**|**Int**|Type d’événement = 28.|27|Non|  
|**EventSequence**|**Int**|Séquence d'un événement donné au sein de la demande.|51|Non|  
|**EventSubClass**|**Int**|Indique l'instruction exécutée en fonction des valeurs suivantes :<br /><br /> 1 = Sélectionner<br /><br /> 2 = Insérer<br /><br /> 3 = Mettre à jour<br /><br /> 4 = Supprimer|21|Non|  
|**GroupID**|**Int**|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|**HostName**|**nvarchar**|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**Integer Data**|**Int**|Quantité de mémoire d'espace de travail, en kilo-octets, accordée à la requête pour réaliser des opérations de hachage, de tri ou de création d'index. La mémoire est acquise lors de l'exécution, au fil des besoins.|25|Oui|  
|**IsSystem**|**Int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|**LoginName**|**nvarchar**|Nom de la connexion de l’utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d’identification de connexion Windows au format DOMAINE\\*nom_utilisateur*).|11|Oui|  
|**LoginSid**|**image**|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|**nvarchar**|Nom d'utilisateur Windows.|6|Oui|  
|**RequestID**|**Int**|Identification de la demande à l'origine de la requête de texte intégral.|49|Oui|  
|**ServerName**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**Int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**datetime**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|**TransactionID**|**bigint**|ID affecté par le système à la transaction.|4|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql)  
  
  
