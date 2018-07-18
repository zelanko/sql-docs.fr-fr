---
title: Classe d’événements QN:Parameter Table | Microsoft Docs
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
- event classes [SQL Server], QN:Parameter Table
ms.assetid: 292da1ed-4c7e-4bd2-9b84-b9ee09917724
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5681c630cc3c45d0f2de06d3b5baa981bebe8c85
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37184656"
---
# <a name="qnparameter-table-event-class"></a>Classe d'événements QN:Parameter Table
  L'événement QN:Parameter Table fournit des informations sur les opérations requises pour créer et supprimer les tables internes chargées de stocker les informations de paramètre et maintenir les nombres de références de ces tables. Il signale également l'activité interne pour réinitialiser le nombre d'utilisations d'une table de paramètres.  
  
## <a name="qnparameter-table-event-class-data-columns"></a>Colonnes de données de la classe d'événements QN:Parameter Table  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l’instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database*n’a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|DatabaseName|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|EventClass|`Int`|Type d’événement = 200.|27|non|  
|EventSequence|`int`|Numéro de séquence de cet événement.|51|non|  
|EventSubClass|`nvarchar`|Type de sous-classe d’événements, qui fournit des informations complémentaires concernant chaque classe d’événements. Cette colonne peut contenir les valeurs suivantes :<br /><br /> Table créée : indique une table de paramètres a été créée dans la base de données.<br /><br /> Tentative de drop table : indique que la base de données a tenté de supprimer automatiquement une table de paramètres inutilisée pour libérer des ressources.<br /><br /> Échoué de la tentative de drop table : indique que la base de données a tenté de supprimer une table de paramètres inutilisée mais a échoué. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] replanifie alors automatiquement la suppression de la table de paramètres afin de libérer des ressources.<br /><br /> Table déposée : indique que la base de données a correctement supprimé une table de paramètres.<br /><br /> Table épinglé : indique que la table de paramètres est marquée pour l’utilisation actuelle par le traitement interne.<br /><br /> Table unpinned : indique que la table de paramètres est libre. Le traitement interne de la table est terminé.<br /><br /> Nombre d’utilisateurs incrémenté : indique que le nombre d’abonnements de notification de requête qui font référence à une table de paramètres a augmenté.<br /><br /> Nombre d’utilisateurs décrémentées : indique que le nombre d’abonnements de notification de requête qui font référence à une table de paramètres a diminué.<br /><br /> Réinitialisation du compteur LRU : indique que le nombre d’utilisations de la table de paramètres a été réinitialisé.<br /><br /> Tâche de nettoyage de démarrage : indique à quel moment le nettoyage de tous les abonnements dans cette table de paramètres a débuté. Ceci se produit au démarrage de la base de données ou lorsqu'une table sous-jacente des abonnements de la table de paramètres est supprimée.<br /><br /> Tâche de nettoyage terminé : indique quand le nettoyage de tous les abonnements dans cette table de paramètres est terminé.|21|Oui|  
|GroupID|`int`|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.<br /><br /> 0 = utilisateur<br /><br /> 1 = système|60|non|  
|LoginName|`nvarchar`|Nom de connexion de l’utilisateur (connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou informations d’identification de connexion Windows sous la forme *DOMAINE*\\*nom_utilisateur*).|11|non|  
|LoginSID|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|`nvarchar`|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|RequestID|`int`|Identificateur de la demande contenant l'instruction.|49|Oui|  
|ServerName|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|SessionLoginName|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si une application se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et qu'elle exécute une commande en tant que Connexion2, SessionLoginName affiche « Connexion1 » et LoginName affiche « Connexion2 ». Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|SPID|`int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|StartTime|`datetime`|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TextData|`ntext`|Retourne un document XML contenant des informations spécifiques à cet événement. Ce document est conforme au schéma XML disponible sur la page [SQL Server Query Notification Profiler Event Schema](http://go.microsoft.com/fwlink/?LinkId=63331) (en anglais).| 1|Oui|  
  
  
