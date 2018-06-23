---
title: Colonnes de données des événements de commande | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Command Events event category
ms.assetid: 7169f1e2-c6be-4d8c-b147-25719b84bc2c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 290c9ca23a71c43d16f29e0bd0e6d1f595b6df14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038423"
---
# <a name="command-events-data-columns"></a>Colonnes de données des événements de commande
  Le tableau ci-dessous répertorie les colonnes de données de chaque classe d'événements de la catégorie d'événement **Événements de commande** .  
  
 La catégorie d'événement **Événements de commande** contient les classes d'événements suivantes :  
  
-   [Command Begin](#bkmk_1)  
  
-   [Command End](#bkmk_2)  
  
 Les tableaux suivants répertorient les colonnes de données de chacune de ces classes d'événements.  
  
##  <a name="bkmk_1"></a> Classe Command Begin—Colonnes de données  
  
|Colonne de données|Description|  
|-----------------|-----------------|  
|ConnectionID|Contient l'ID de connexion unique associé à l'événement de commande.|  
|TextData|Contient les données texte associées à l'événement de commande.|  
|ServerName|Contient le nom de l'instance [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur laquelle l'événement de commande s'est produit.|  
|CurrentTime|Contient l'heure actuelle de l'événement de commande.|  
|DatabaseName|Contient le nom de la base de données dans laquelle la commande est exécutée.|  
|EventSubclass|Contient la classe d'événements dans l'événement de commande. Valeurs possibles :<br /><br /> 0 : Create<br />1 : Alter<br />2 : Delete<br />3 : Process<br />4 : DesignAggregations<br />5 : WBInsert<br />6 : WBUpdate<br />7 : WBDelete<br />8 : Backup<br />9 : Restore<br />10 : MergePartitions<br />11 : Subscribe<br />12 : Batch<br />13 : BeginTransaction<br />14 : CommitTransaction<br />15 : RollbackTransaction<br />16 : GetTransactionState<br />17 : Cancel<br />18 : Synchronize<br />19 : Import80MiningModels<br />20 : Attach<br />21 : Detach<br />22 : SetAuthContext<br />23 : ImageLoad<br />24 : ImageSave<br />10000 : Other|  
|NTUserName|Contient le nom d'utilisateur Windows associé à l'événement de commande. Le nom d'utilisateur a la forme canonique. engineering.microsoft.com/software/user, par exemple.|  
|RequestProperties|Contient les propriétés de demande XMLA (XML for Analysis) associées à l'événement de commande.|  
|SPID|Contient l’ID de processus serveur (SPID) qui identifie de manière unique la session utilisateur associée à l’événement de commande. Le SPID correspond directement au GUID de session utilisé par XMLA.|  
|StartTime|Contient l'heure de début (si disponible) de l'événement de commande.|  
|SessionType|Contient l'entité qui a provoqué l'opération.|  
|NTDomainName|Contient le compte de domaine Windows associé à l'événement d'autorisation de l'objet.|  
|ClientProcessID|Contient l'ID de processus client unique associé à l'événement de commande.|  
  
##  <a name="bkmk_2"></a> Classe Command End—Colonnes de données  
  
|Colonne de données|Description|  
|-----------------|-----------------|  
|ConnectionID|Contient l'ID de connexion unique associé à l'événement de commande.|  
|TextData|Contient les données texte associées à l'événement de commande.|  
|ServerName|Contient le nom de l'instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sur laquelle l'événement de commande s'est produit.|  
|CurrentTime|Contient l'heure actuelle de l'événement de commande. Pour le filtrage, les formats sont *YYYY*-*MM*-*DD* et *YYYY*-*MM*-*DD HH*:*MM*:*SS*.|  
|DatabaseName|Contient le nom de la base de données dans laquelle la commande est exécutée.|  
|Duration|Contient le délai approximatif entre l'événement de début de commande et de fin de commande.|  
|EndTime|Contient l'heure de fin de l'événement de commande. Pour le filtrage, les formats sont *YYYY*-*MM*-*DD* et *YYYY*-*MM*-*DD HH*:*MM*:*SS*.|  
|EventSubclass|Contient la classe d'événements dans l'événement de commande. Valeurs possibles :<br /><br /> 0 : Create<br />1 : Alter<br />2 : Delete<br />3 : Process<br />4 : DesignAggregations<br />5 : WBInsert<br />6 : WBUpdate<br />7 : WBDelete<br />8 : Backup<br />9 : Restore<br />10 : MergePartitions<br />11 : Subscribe<br />12 : Batch<br />13 : BeginTransaction<br />14 : CommitTransaction<br />15 : RollbackTransaction<br />16 : GetTransactionState<br />17 : Cancel<br />18 : Synchronize<br />19 : Import80MiningModels<br />20 : Attach<br />21 : Detach<br />22 : SetAuthContext<br />23 : ImageLoad<br />24 : ImageSave<br />10000 : Other|  
|NTCanonicalUserName|Contient le nom d'utilisateur Windows associé à l'événement de commande. Le nom d'utilisateur a la forme canonique. engineering.microsoft.com/software/user, par exemple.|  
|NTUserName|Contient le compte d'utilisateur Windows associé à l'événement de commande.|  
|SPID|Contient l'ID de processus serveur (SPID) qui identifie de manière unique la session utilisateur associée à l'événement de commande. Le SPID correspond directement au GUID de session utilisé par XMLA.|  
|StartTime|Contient l'heure de début (si disponible) de l'événement de fin de commande.|  
|CPUTime|Contient le temps processeur (en millisecondes) utilisé par le processus entre l'événement de début de commande et l'événement de fin de commande.|  
|Error|Contient le numéro d'erreur de toute erreur associée à l'événement de commande.|  
|Severity|Contient le niveau de gravité d'une exception associée à l'événement de commande. Valeurs possibles :<br /><br /> 0 = Réussite<br /><br /> 1 = Informationnelle<br /><br /> 2 = Avertissement<br /><br /> 3 = Erreur|  
|Réussi|Contient la réussite ou l'échec de l'événement de commande. Valeurs possibles :<br /><br /> 0 = Échec<br /><br /> 1 = Réussite|  
|SessionType|Contient l'entité ayant provoqué l'opération associée à l'événement de commande.|  
|NTDomainName|Contient le compte de domaine Windows associé à l'événement de commande.|  
|ClientProcessID|Contient l'ID de processus client unique associé à l'événement de commande.|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements de commande, catégorie d’événement](command-events-event-category.md)  
  
  