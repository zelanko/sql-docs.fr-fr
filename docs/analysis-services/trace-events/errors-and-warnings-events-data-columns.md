---
title: Erreurs et avertissements Events Data Columns | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
ms.assetid: f375d303-7aab-4c51-a955-05a2762cc4d1
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a909f39446c2a90347e8253c7fb54c1abe91c353
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="errors-and-warnings-events-data-columns"></a>Colonnes de données des événements d'erreur et d'avertissement
  La catégorie d'événement Audit de sécurité contient la classe d'événements suivante :  
  
-   Classe d’erreur  
  
 Le tableau suivant répertorie les colonnes de données de cette classe d'événements.  
  
## <a name="error-event-classdata-columns"></a>Classe Error Event—Colonnes de données  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Classe d'événements utilisée pour catégoriser les événements.|  
|StartTime|3|5|Contient l'heure de début de l'événement, le cas échéant. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|SessionType|8|8|Contient le type de l'entité qui a provoqué l'erreur.|  
|Severity|22|1|Contient le niveau de gravité d'une exception associée à l'événement d'erreur. Valeurs possibles :<br /><br /> 0 = Réussite<br /><br /> 1 = Informationnelle<br /><br /> 2 = Avertissement<br /><br /> 3 = Erreur|  
|Réussi|23|1|Contient la réussite ou l'échec de l'événement d'erreur. Valeurs possibles :<br /><br /> 0 = Échec<br /><br /> 1 = Réussite|  
|Erreur|24|1|Contient le nombre d'occurrences d'une erreur associée à l'événement d'erreur.|  
|ConnectionID|25|1|Contient l'ID de connexion unique associé à l'événement d'erreur.|  
|DatabaseName|28|8|Contient le nom de l’instance [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur laquelle l’événement d’erreur se produit.|  
|NTUserName|32|8|Contient le nom d'utilisateur Windows associé à l'événement d'erreur.|  
|NTDomainName|33|8|Contient le compte de domaine Windows associé à l'événement de connexion.|  
|ClientHostName|35|8|Contient le nom de l'ordinateur sur lequel s'exécute le client. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client.|  
|ClientProcessID|36|1|Contient l'ID de processus de l'application cliente.|  
|ApplicationName|37|8|Contient le nom de l'application cliente qui a créé la connexion au serveur. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|  
|SessionID|39|8|Contient l'ID de processus serveur (SPID) qui identifie de manière unique la session utilisateur associée à l'événement d'erreur. Le SPID correspond directement au GUID de session utilisé par XMLA (XML for Analysis).|  
|SPID|41|1|Contient l'ID de processus serveur (SPID) qui identifie de manière unique la session utilisateur associée à l'événement d'erreur. Le SPID correspond directement au GUID de session utilisé par XMLA (XML for Analysis).|  
|TextData|42|9|Contient les données texte associées à l'événement d'erreur.|  
|ServerName|43|8|Contient le nom du serveur exécutant l’instance [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur laquelle l’événement d’erreur s’est produit.|  
  
## <a name="see-also"></a>Voir aussi  
 [Catégorie d'événement Audit de sécurité](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  
