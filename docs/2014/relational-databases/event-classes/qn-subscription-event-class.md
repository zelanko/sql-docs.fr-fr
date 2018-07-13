---
title: QN:Subscription, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], QN:Subscription
ms.assetid: 4916167e-8541-43b4-900e-ec8e6adcbc34
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 79e75ea52d0e1ed2d80dd4e2ef9dcc2d2092e6c3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37188476"
---
# <a name="qnsubscription-event-class"></a>Classe d'événements QN:Subscription
  L'événement QN:Subscription fournit des informations sur les abonnements aux notifications.  
  
## <a name="qnsubscription-event-class-data-columns"></a>Colonnes de données de la classe d'événements QN:Subscription  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l’instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database*n’a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|DatabaseName|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|EventClass|`int`|Type d’événement = 199.|27|non|  
|EventSequence|`int`|Numéro de séquence de cet événement.|51|non|  
|EventSubClass|`nvarchar`|Type de sous-classe d’événements, qui fournit des informations complémentaires concernant chaque classe d’événements. Cette colonne peut contenir les valeurs suivantes :<br /><br /> Abonnement enregistré : indique quand l’abonnement de notification de requête a été enregistré dans la base de données.<br /><br /> Abonnement rembobinée : indiquant à quel moment le [!INCLUDE[ssDE](../../includes/ssde-md.md)] reçoit une demande d’abonnement qui correspond exactement à un abonnement existant. Dans ce cas, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] définit la valeur de délai de l’abonnement existant sur le délai spécifié dans la nouvelle demande d’abonnement.<br /><br /> Abonnement a été déclenché : indique quand un abonnement aux notifications produit un message de notification.<br /><br /> Déclenchement de l’événement a échoué avec l’erreur broker : indique quand un message de notification échoue en raison d’un [!INCLUDE[ssSB](../../includes/sssb-md.md)] erreur.<br /><br /> Échec de déclenchement sans erreur broker : indique quand un message de notification échoue mais n’est pas dû à un [!INCLUDE[ssSB](../../includes/sssb-md.md)] erreur.<br /><br /> Service Broker erreur interceptée : indique que [!INCLUDE[ssSB](../../includes/sssb-md.md)] généré une erreur dans la conversation qui utilise la notification de requête.<br /><br /> Tentative de suppression d’abonnement : indique que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] a tenté de supprimer un abonnement ayant expiré pour libérer des ressources.<br /><br /> Échoué de la suppression de l’abonnement : indique que la tentative de suppression d’un abonnement ayant expiré a échoué. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] replanifiera automatiquement la suppression de l’abonnement pour libérer des ressources.<br /><br /> Abonnement détruit : indique que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] supprimé avec succès un abonnement ayant expiré|21|Oui|  
|GroupID|`int`|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.<br /><br /> 0 = utilisateur<br /><br /> 1 = système|60|non|  
|LoginName|`nvarchar`|Nom de la connexion de l'utilisateur (soit la connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , soit les informations d'identification de connexion Windows au format DOMAINE\nom_utilisateur).|11|non|  
|LoginSID|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|`nvarchar`|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|RequestID|`int`|Identificateur de la demande contenant l'instruction.|49|Oui|  
|ServerName|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|SessionLoginName|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si une application se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et qu'elle exécute une commande en tant que Connexion2, SessionLoginName affiche « Connexion1 » et LoginName affiche « Connexion2 ». Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|SPID|`int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|StartTime|`datetime`|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TextData|`ntext`|Retourne un document XML contenant des informations spécifiques à cet événement. Ce document est conforme au schéma XML disponible sur la page [SQL Server Query Notification Profiler Event Schema](http://go.microsoft.com/fwlink/?LinkId=63331) (en anglais).| 1|Oui|  
  
  
