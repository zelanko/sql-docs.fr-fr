---
title: "Types d&#39;Abonn&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.subscribertypes.f1"
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Types d&#39;Abonn&#233;s
  La réplication de fusion vous permet de préciser les types d'Abonnés qu'une publication doit prendre en charge. La sélection des ensembles de types d'Abonnés définit le *niveau de compatibilité de la publication*ce qui détermine les fonctionnalités pouvant être utilisées par la publication.  
  
 Après la création d’un instantané de publication, le niveau de compatibilité peut être augmenté (rendue plus restrictif) sur le **Général** page de la **Propriétés de la Publication** boîte de dialogue ; la compatibilité au niveau ne peut être diminué.  
  
## Options  
 Sélectionnez chaque type d'Abonné que votre publication doit prendre en charge.  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
 La publication peut utiliser toutes les fonctionnalités.  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]  
 La publication requiert que les fichiers d'instantané soient au format caractère (ceci est géré automatiquement par l'Agent d'instantané). [!INCLUDE[ssEW](../../includes/ssew-md.md)] est également limité par un certain nombre de restrictions indépendantes du niveau de compatibilité.  
  
 Si cette option est sélectionnée, l'option de synchronisation Web est alors activée pour la publication en question. Pour plus d'informations sur la synchronisation Web, consultez [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
## Voir aussi  
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Référence des propriétés de & #40 ; Réplication & #41 ;](../../relational-databases/replication/properties-reference-replication.md)  
  
  