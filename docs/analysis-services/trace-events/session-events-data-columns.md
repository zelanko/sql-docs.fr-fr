---
title: "Colonnes de données d’événements session | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Session Events event category
ms.assetid: 35853451-6768-4a02-8b8f-81a8ae37a333
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cb85851bd0c05de09120fa2403c1e47bf0da9a75
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="session-events-data-columns"></a>Colonnes de données des événements de session
  La catégorie d'événement Événements de session contient les classes d'événements suivantes :  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|41|Connexion existante|Connexion utilisateur existante.|  
|42|Existing Session|Session existante.|  
|43|Session Initialize|Initialisation de session.|  
  
 Le tableau suivant répertorie les colonnes de données de cette classe d'événements.  
  
## <a name="existing-connection"></a>Connexion existante  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|CurrentTime|2|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|StartTime|3|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|ConnectionID|25|1|ID de connexion unique.|  
|NTUserName|32|8|Nom d'utilisateur Windows.|  
|NTDomainName|33|8|Domaine Windows auquel appartient l'utilisateur.|  
|ClientHostName|35|8|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client.|  
|ClientProcessID|36|1|ID de processus de l'application cliente.|  
|ApplicationName|37|8|Nom de l'application cliente qui a créé la connexion au serveur. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|  
|SPID|41|1|ID de processus serveur. Cela identifie de façon unique une session utilisateur. Le SPID correspond directement au GUID de session utilisé par XML/A.|  
|ServerName|43|8|Nom du serveur produisant l'événement.|  
  
## <a name="existing-session"></a>Existing Session  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|CurrentTime|2|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|StartTime|3|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|Duration|5|2|Durée (en millisecondes) de l'événement.|  
|CPUTime|6|2|Temps processeur (en millisecondes) utilisé par l'événement.|  
|ConnectionID|25|1|ID de connexion unique.|  
|DatabaseName|28|8|Nom de la base de données dans laquelle l'instruction de l'utilisateur s'exécute.|  
|NTUserName|32|8|Nom d'utilisateur Windows.|  
|NTDomainName|33|8|Domaine Windows auquel appartient l'utilisateur.|  
|ClientHostName|35|8|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client.|  
|ClientProcessID|36|1|ID de processus de l'application cliente.|  
|ApplicationName|37|8|Nom de l'application cliente qui a créé la connexion au serveur. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|  
|NTCanonicalUserName|40|8|Nom d'utilisateur sous forme canonique. Par exemple, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID de processus serveur. Cela identifie de façon unique une session utilisateur. Le SPID correspond directement au GUID de session utilisé par XML/A.|  
|TextData|42|9|Données texte associées à l'événement.|  
|ServerName|43|8|Nom du serveur produisant l'événement.|  
|RequestProperties|45|9|Propriétés de requête XMLA.|  
  
## <a name="session-initialize"></a>Session Initialize  
  
|||||  
|-|-|-|-|  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|CurrentTime|2|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|StartTime|3|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|ConnectionID|25|1|ID de connexion unique.|  
|DatabaseName|28|8|Nom de la base de données dans laquelle l'instruction de l'utilisateur s'exécute.|  
|NTUserName|32|8|Nom d'utilisateur Windows.|  
|NTDomainName|33|8|Domaine Windows auquel appartient l'utilisateur.|  
|ClientHostName|35|8|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client.|  
|ClientProcessID|36|1|ID de processus de l'application cliente.|  
|ApplicationName|37|8|Nom de l'application cliente qui a créé la connexion au serveur. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|  
|NTCanonicalUserName|40|8|Nom d'utilisateur sous forme canonique. Par exemple, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID de processus serveur. Cela identifie de façon unique une session utilisateur. Le SPID correspond directement au GUID de session utilisé par XML/A.|  
|TextData|42|9|Données texte associées à l'événement.|  
|ServerName|43|8|Nom du serveur produisant l'événement.|  
|RequestProperties|45|9|Propriétés de requête XMLA.|  
  
## <a name="see-also"></a>Voir aussi  
 [Catégorie d'événement Audit de sécurité](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  

