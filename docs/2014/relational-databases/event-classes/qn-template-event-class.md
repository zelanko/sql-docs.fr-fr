---
title: QN:Template, classe d’événements | Microsoft Docs
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
- event classes [SQL Server], QN:Template
ms.assetid: 9f752040-5901-42e1-8fdc-105528d9960a
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: adc7d7a6700373227d5508cbd77e4101a0051ba9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37268985"
---
# <a name="qntemplate-event-class"></a>Classe d'événements QN:Template
  L'événement QN:Template fournit des informations sur l'utilisation interne des modèles de requête. Ces derniers sont les mécanismes que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] emploie pour partager les définitions d’une requête en vue des notifications. Ils sont créés en même temps que les tables de paramètres. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] crée un événement de ce type quand un modèle de requête est créé, utilisé ou détruit.  
  
## <a name="qntemplate-event-class-data-columns"></a>Colonnes de données de classe d'événements QN:Template  
  
|Colonne de données|Type|Description|Numéro de colonne|Filtrable|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|Nom de l'application cliente qui a créé la connexion à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|10|Oui|  
|ClientProcessID|`int`|ID affecté par l'ordinateur hôte au processus dans lequel s'exécute l'application cliente. Cette colonne de données est remplie si l'ID du processus du client est fourni par le client.|9|Oui|  
|DatabaseID|`int`|ID de la base de données spécifiée par l’instruction USE *database* ou celui de la base de données par défaut si aucune instruction USE *database*n’a été spécifiée pour une instance donnée. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] affiche le nom de la base de données si la colonne de données ServerName est capturée dans la trace et que le serveur est disponible. Déterminez la valeur pour une base de données à l'aide de la fonction DB_ID.|3|Oui|  
|DatabaseName|`nvarchar`|Nom de la base de données dans laquelle l'instruction de l'utilisateur est exécutée.|35|Oui|  
|EventClass|`int`|Type d’événement = 201.|27|non|  
|EventSequence|`int`|Numéro de séquence de cet événement.|51|non|  
|EventSubClass|`nvarchar`|Type de sous-classe d’événements, qui fournit des informations complémentaires concernant chaque classe d’événements. Cette colonne peut contenir les valeurs suivantes :<br /><br /> Template created : indique qu’un modèle de notification de requête a été créé dans la base de données.<br /><br /> Template matched : indique qu’un modèle de notification de requête est réutilisé.<br /><br /> Template dropped : indique qu’un modèle de notification de requête est supprimé de la base de données.|21|Oui|  
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
  
  
