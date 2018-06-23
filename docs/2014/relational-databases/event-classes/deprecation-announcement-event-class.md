---
title: Classe d’événements Deprecation Announcement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
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
- deprecation [SQL Server], events announced stage
- Deprecation Announcement event class
ms.assetid: 46fc578f-3c97-477f-879c-8a1b2cfd9d58
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e3f0c25031a54be1b4b3131483e3aecacf1bb683
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143059"
---
# <a name="deprecation-announcement-event-class"></a>Deprecation Announcement (classe d'événements)
  La classe d’événements **Deprecation Announcement** intervient quand vous utilisez une fonction vouée à être retirée dans une version future de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais qui sera toujours présente dans la prochaine version majeure. Pour une plus grande longévité de vos applications, évitez d’utiliser les fonctions qui font intervenir la classe d’événements **Deprecation Announcement** ou **Deprecation Final Support** .  
  
## <a name="deprecation-announcement-event-class-data-columns"></a>Colonnes de données de la classe d'événements Deprecation Announcement  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. La colonne de données est remplie si le client fournit l'ID du processus client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l'instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database* n'a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Affiche le nom de la base de données si la `ServerName` colonne de données est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|DatabaseName|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|EventClass|`int`|Type d’événement = 125.|27|non|  
|EventSequence|`int`|Séquence d'un événement donné au sein de la demande.|51|non|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel le client est exécuté. La colonne de données est remplie si le client fournit le nom de l'hôte. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IntegerData2|`int`|Décalage de fin (en octets) de l'instruction en cours d'exécution.|55|Oui|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur. 1 = système, 0 = utilisateur.|60|Oui|  
|LoginName|`nvarchar`|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows au format DOMAINE\nom_utilisateur).|11|Oui|  
|LoginSid|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|`nvarchar`|Nom d'utilisateur Windows.|6|Oui|  
|ObjectID|`int`|Numéro d'ID de la fonctionnalité déconseillée.|22|Oui|  
|ObjectName|`nvarchar`|Nom de la fonctionnalité déconseillée.|34|Oui|  
|Offset|`int`|Décalage de départ de l'instruction dans la procédure stockée ou le lot.|61|Oui|  
|RequestID|`int`|ID de la demande contenant l'instruction.|49|Oui|  
|ServerName|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|SessionLoginName|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si vous vous connectez à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et exécutez une instruction en tant que connexion2, `SessionLoginName` affiche Login1 et `LoginName` affiche Login2. Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|SPID|`int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|SqlHandle|`image`|Descripteur binaire pouvant être utilisé pour identifier les traitements ou les procédures stockées SQL.|63|Oui|  
|StartTime|`datetime`|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TextData|`ntext`|Valeur texte qui dépend de la classe d'événements capturée dans la trace.| 1|Oui|  
|TransactionID|`bigint`|ID affecté par le système à la transaction.|4|Oui|  
|XactSequence|`bigint`|Jeton qui décrit la transaction en cours.|50|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Classe d'événements Deprecation Final Support](deprecation-final-support-event-class.md)   
 [Fonctionnalités du moteur de base de données déconseillées dans SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
