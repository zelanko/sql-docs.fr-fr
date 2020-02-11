---
title: CursorUnprepare, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- CursorUnprepare event class
ms.assetid: 34055a2f-7d0f-4e13-a62e-7ee5b6c23b86
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: aac3a20511012e0a058fff6988c793c4f51d594d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62663393"
---
# <a name="cursorunprepare-event-class"></a>CursorUnprepare (classe d'événements)
  La classe d’événements **CursorUnprepare** fournit des informations sur les événements d’inpréparation de curseur qui se produisent dans les curseurs d’interface de programmation d’applications (API). Les événements d’inpréparation de curseur [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] se produisent lorsque le ignore un plan d’exécution.  
  
 Incluez la classe d’événements **CursorUnprepare** dans des traces qui enregistrent les performances des curseurs. Quand la classe d’événements **CursorUnprepare** est incluse dans une trace, l’importance de la charge induite dépend de la fréquence d’utilisation des curseurs sur la base de données pendant la trace. Si les curseurs sont largement utilisés, la trace peut altérer considérablement les performances.  
  
## <a name="cursorunprepare-event-class-data-columns"></a>Colonnes de la classe d'événements CursorUnprepare  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie des valeurs transmises par l'application et non pas du nom affiché du programme.|10|Oui|  
|**ClientProcessID**|**int**|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. La colonne de données est remplie si le client fournit l'ID du processus client.|9|Oui|  
|**DatabaseID**|**int**|ID de la base de données spécifiée par l'instruction USE ou celui de la base de données par défaut si aucune instruction USE n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]affiche le nom de la base de données si la colonne de données **ServerName** est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|**DatabaseName**|**nvarchar**|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|**EventClass**|**int**|Type d’événement enregistré = 77|27|Non|  
|**EventSequence**|**int**|Séquence de traitement de la classe d’événements **CursorUnprepare** .|51|Non|  
|**GroupID**|**int**|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|**Traitée**|**Tiers**|Identifie le handle préparé en cours d'annulation de préparation.|33|Oui|  
|**Nom d’hôte**|**nvarchar**|Nom de l'ordinateur sur lequel le client est exécuté. La colonne de données est remplie si le client fournit le nom de l'hôte. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|**IsSystem**|**int**|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|**LoginName**|**nvarchar**|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Oui|  
|**LoginSid**|**image**|Identificateur de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l’affichage catalogue **sys. server_principals** . Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|**NTDomainName**|**nvarchar**|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|**NTUserName**|**nvarchar**|Nom d'utilisateur Windows.|6|Oui|  
|**Identifi**|**int**|Identification de la demande qui a annulé la préparation du curseur.|49|Oui|  
|**Nom du serveur**|**nvarchar**|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|Non|  
|**SessionLoginName**|**nvarchar**|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et que vous exécutez une commande en tant que Login2, **SessionLoginName** affiche Login1 et **LoginName** affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|**SPID**|**int**|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|**StartTime**|**DATETIME**|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|**TransactionID**|**bigint**|ID affecté par le système à la transaction.|4|Oui|  
|**XactSequence**|**bigint**|Jeton qui décrit la transaction en cours.|50|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
