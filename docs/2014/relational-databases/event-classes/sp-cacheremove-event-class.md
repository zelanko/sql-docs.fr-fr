---
title: SP:CacheRemove, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- SP:CacheRemove event class
ms.assetid: aaa3c5c4-2d3a-4832-a473-ce9bd4fb1c17
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db6b0933af52271698622b86b848de16ecbd7cb2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042451"
---
# <a name="spcacheremove-event-class"></a>SP:CacheRemove, classe d'événements
  La classe d'événements SP:CacheRemove indique que la procédure stockée a été supprimée du cache de plan.  
  
## <a name="spcacheremove-event-class-data-columns"></a>Colonnes de la classe d'événements SP:CacheRemove  
  
|Nom de la colonne de données|`Data type`|Description|ID de la colonne|Filtrable|  
|----------------------|-------------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. La colonne de données est remplie si le client fournit l'ID du processus client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données dans laquelle la procédure stockée est en cours d'exécution. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|DatabaseName|`nvarchar`|Nom de la base de données dans laquelle la procédure stockée est en cours d'exécution.|35|Oui|  
|EventClass|`int`|Type d’événement = 36.|27|non|  
|EventSequence|`int`|Séquence d'un événement donné au sein de la demande.|51|non|  
|EventSubClass|`int`|Type de sous-classe d'événements.<br /><br /> 1 = Compplan Remove. Un plan de requête compilé a été supprimé du cache.<br /><br /> 2 = Proc Cache Flush. Toutes les entrées ont été supprimées du cache de procédures.|21|Oui|  
|GroupID|`int`|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel le client est exécuté. La colonne de données est remplie si le client fournit le nom de l'hôte. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|LoginName|`nvarchar`|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Oui|  
|LoginSid|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|`nvarchar`|Nom d'utilisateur Windows.|6|Oui|  
|ObjectID|`int`|ID affecté par le système à la procédure stockée.|22|Oui|  
|ObjectType|`int`|Valeur représentant le type de l'objet qui intervient dans l'événement. Cette valeur correspond à la colonne type de l'affichage catalogue sys.objects. Pour connaître les valeurs, consultez [Colonne d’événements de trace ObjectType](objecttype-trace-event-column.md).|28|Oui|  
|RequestID|`int`|ID de la demande contenant l'instruction.|49|Oui|  
|ServerName|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|SessionLoginName|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant le nom Connexion1 et que vous exécutez une instruction en tant que Connexion2, SessionLoginName affiche Connexion1 et LoginName, Connexion2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|SPID|`int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|StartTime|`datetime`|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TextData|`ntext`|Texte de l'instruction SQL en cours de suppression du cache.| 1|Oui|  
|TransactionID|`bigint`|ID affecté par le système à la transaction.|4|Oui|  
|XactSequence|`bigint`|Jeton qui décrit la transaction en cours.|50|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
