---
title: OLEDB QueryInterface, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- OLEDB QueryInterface event class
ms.assetid: f54c9ef9-3add-497c-a09b-42c4ce3c623d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b420e0b4b9c9531209f3d3227f534116e26dd206
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52763621"
---
# <a name="oledb-queryinterface-event-class"></a>OLEDB QueryInterface (classe d'événements)
  La classe d’événements **OLEDB QueryInterface** se produit quand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] émet un appel vers **QueryInterface** du fournisseur OLE DB, provenant de requêtes distribuées et de procédures stockées distantes. Ajoutez cette classe d'événements dans les traces servant à effectuer un suivi des problèmes relatifs aux requêtes distribuées et aux procédures stockées distantes.  
  
 Quand la classe **OLEDB QueryInterface** y est incluse, le total de l’espace réservé en est d’autant alourdi. Si de tels événements se produisent fréquemment, il est possible que la trace affecte de façon notable les performances. Pour minimiser l'effet d'une telle charge, limitez l'utilisation de cette classe d'événements aux traces destinées à effectuer le suivi de problèmes précis pour de brèves durées.  
  
## <a name="oledb-queryinterface-event-class-data-columns"></a>Colonnes de données de la classe d'événements OLEDB QueryInterface  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. La colonne de données est remplie si le client fournit l'ID du processus client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données **ServerName** du serveur est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|DatabaseName|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|Duration|`bigint`|Durée nécessaire pour exécuter l'événement OLE DB QueryInterface.|13|Non|  
|EndTime|`datetime`|Heure de fin de l'événement.|15|Oui|  
|Error|`int`|Numéro d'erreur d'un événement donné. Il s’agit souvent du numéro d’erreur stocké dans l’affichage catalogue **sys.messages** .|31|Oui|  
|EventClass|`int`|Type d’événement = 120.|27|Non|  
|EventSequence|`int`|Séquence de la classe d'événements du fournisseur OLE DB au sein du traitement.|51|Non|  
|EventSubClass|`int`|0=Démarrage<br /><br /> 1=Terminée|21|Non|  
|GroupID|`int`|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel le client est exécuté. La colonne de données est remplie si le client fournit le nom de l'hôte. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|LinkedServerName|`nvarchar`|Nom du serveur lié.|45|Oui|  
|LoginName|`nvarchar`|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Oui|  
|LoginSid|`image`|Identificateur de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|MethodName|`nvarchar`|Nom de la méthode appelante.|47|Non|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|`nvarchar`|Nom d'utilisateur Windows.|6|Oui|  
|ProviderName|`nvarchar`|Nom du fournisseur OLE DB.|46|Oui|  
|RequestID|`int`|ID de la demande contenant l'instruction.|49|Oui|  
|SessionLoginName|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Exemple : si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le nom d'utilisateur Login1 et exécutez une instruction sous le nom Login2, `SessionLoginName` retourne Login1 et `LoginName` retourne Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|SPID|`int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|StartTime|`datetime`|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TextData|`nvarchar`|Paramètres envoyés et reçus au sein de l'appel OLE DB.|1|Non|  
|TransactionID|`bigint`|ID affecté par le système à la transaction.|4|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Objets OLE Automation dans Transact-SQL](../stored-procedures/ole-automation-objects-in-transact-sql.md)  
  
  
