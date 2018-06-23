---
title: Classe d’événements QN:Dynamics | Microsoft Docs
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
- event classes [SQL Server], QN:Dynamics
ms.assetid: 3c1ffa0c-c9e5-40a6-a26b-28339f60ebc3
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0187f27bd7375b22cd703c6e7caa818cc3a7dd38
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044520"
---
# <a name="qndynamics-event-class"></a>Classe d'événements QN:Dynamics
  La classe d'événements QN:Dynamics fournit des informations sur l'activité d'arrière-plan que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] effectue pour la prise en charge des notifications de requête. Dans le [!INCLUDE[ssDE](../../includes/ssde-md.md)], un thread d’arrière-plan surveille les délais d’abonnement, les abonnements en attente à déclencher et la destruction de la table de paramètres.  
  
## <a name="qndynamics-event-class-data-columns"></a>Colonnes de données de la classe d'événements QN:Dynamics  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l’instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database*n’a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|DatabaseName|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|EventClass|`int`|Type d'événement = 202|27|non|  
|EventSequence|`int`|Numéro de séquence de cet événement.|51|non|  
|EventSubClass|`nvarchar`|Type de sous-classe d’événements, qui fournit des informations complémentaires concernant chaque classe d’événements. Cette colonne peut contenir les valeurs suivantes :<br /><br /> Horloge a commencé : indique que le thread d’arrière-plan dans le [!INCLUDE[ssDE](../../includes/ssde-md.md)] que les planifications tables de paramètres expirés pour le nettoyage a démarré.<br /><br /> Horloge exécuter terminé : indique que le thread d’arrière-plan dans le [!INCLUDE[ssDE](../../includes/ssde-md.md)] que les planifications tables de paramètres expirés pour le nettoyage est terminé.<br /><br /> Tâche de nettoyage maître de démarrage : indique le démarrage du nettoyage (garbage collection) pour supprimer les données d’abonnement de notification de requête expirées.<br /><br /> Tâche de nettoyage Master terminé : indique quand se termine le nettoyage (garbage collection) pour supprimer les données d’abonnement de notification de requête expirées.<br /><br /> Tâche de nettoyage Master ignorée : indique que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n’a pas effectué le nettoyage (garbage collection) pour supprimer les données d’abonnement de notification de requête expirées.|21|Oui|  
|GroupID|`int`|ID du groupe de charges de travail où l'événement Trace SQL se déclenche.|66|Oui|  
|HostName|`nvarchar`|Nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client. Pour déterminer le nom de l'hôte, utilisez la fonction HOST_NAME.|8|Oui|  
|IsSystem|`int`|Indique si l'événement s'est produit sur un processus système ou sur un processus utilisateur.<br /><br /> 0 = utilisateur<br /><br /> 1 = système|60|non|  
|LoginName|`nvarchar`|Nom de connexion de l’utilisateur (connexion de sécurité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou informations d’identification de connexion Windows sous la forme *DOMAINE\nom_utilisateur*).|11|non|  
|LoginSID|`image`|Numéro d'identification de sécurité (SID) de l'utilisateur connecté. Vous pouvez trouver ces informations dans l'affichage catalogue sys.server_principals. Chaque connexion possède un SID unique au niveau du serveur.|41|Oui|  
|NTDomainName|`nvarchar`|Domaine Windows auquel appartient l'utilisateur.|7|Oui|  
|NTUserName|`nvarchar`|Nom de l'utilisateur propriétaire de la connexion ayant généré l'événement.|6|Oui|  
|RequestID|`int`|Identificateur de la demande contenant l'instruction.|49|Oui|  
|ServerName|`nvarchar`|Nom de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracée.|26|non|  
|SessionLoginName|`nvarchar`|Nom de connexion de l'utilisateur à l'origine de la session. Par exemple, si une application se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au moyen de Login1 et qu'elle exécute une commande en tant que Connexion2, SessionLoginName affiche « Connexion1 » et LoginName affiche « Connexion2 ». Cette colonne affiche à la fois les connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et Windows.|64|Oui|  
|SPID|`int`|ID de la session au cours de laquelle l'événement s'est produit.|12|Oui|  
|StartTime|`datetime`|Heure à laquelle a débuté l'événement, si elle est connue.|14|Oui|  
|TextData|`ntext`|Retourne un document XML contenant des informations spécifiques à cet événement. Ce document est conforme au schéma XML disponible sur la page [SQL Server Query Notification Profiler Event Schema](http://go.microsoft.com/fwlink/?LinkId=63331) (en anglais).| 1|Oui|  
  
  