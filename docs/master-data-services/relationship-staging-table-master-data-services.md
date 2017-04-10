---
title: "Table de mise en lots des relations (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "table intermédiaire des relations [Master Data Services]"
  - "base de données [Master Data Services], table de relations"
ms.assetid: e19b6002-67bd-4e7d-9f19-ecb455522b1a
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# Table de mise en lots des relations (Master Data Services)
  Utilisez la table de mise en lots des relations (stg.name_Relationship) dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] pour modifier l’emplacement des membres dans une hiérarchie explicite, en fonction de la relation que les membres entretiennent les uns par rapport aux autres.  
  
##  <a name="TableColumns"></a> Colonnes de table  
 Le tableau suivant explique la fonction de chacun des champs de la table de mise en lots Relation.  
  
|Nom de la colonne|Description|Value|  
|-----------------|-----------------|-----------|  
|**ID**|Identificateur automatiquement affecté.|N'entrez pas de valeur dans ce champ. Si le lot n'a pas été traité, ce champ est vide.|  
|**RelationshipType**|Requis<br /><br /> Type de relation défini.|Les valeurs possibles sont :<br /><br /> **1** : parent<br /><br /> **2** : frère (au même niveau)|  
|**ImportStatus_ID**|Requis<br /><br /> État du processus d'importation.|Les valeurs possibles sont :<br /><br /> **0**, que vous spécifiez pour indiquer que l'enregistrement est prêt pour la mise en lots ;<br /><br /> **1**, qui est affecté automatiquement et qui indique que le processus de mise en lots pour l'enregistrement a réussi ;<br /><br /> **2**, qui est affecté automatiquement et qui indique que le processus de mise en lots pour l'enregistrement a échoué.|  
|**Batch_ID**|Requis par le service Web uniquement<br /><br /> Identificateur automatiquement affecté qui regroupe des enregistrements pour la mise en lots.<br /><br /> Si le lot n'a pas été traité, ce champ est vide.|Cet identificateur, affiché dans l'interface utilisateur [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] dans la colonne **ID** , est affecté à tous les membres du lot.|  
|**BatchTag**|Requis, sauf par le service Web<br /><br /> Nom unique du lot, jusqu'à 50 caractères.||  
|**HierarchyName**|Requis<br /><br /> Nom de hiérarchie explicite. Chaque membre consolidé ne peut appartenir qu'à une seule hiérarchie.||  
|**ParentCode**|Requis<br /><br /> Pour les relations parent-enfant, code du membre consolidé qui sera le parent du membre feuille ou consolidé enfant.<br /><br /> Pour les relations de frère, code de l'un des frères.||  
|**ChildCode**|Requis<br /><br /> Pour les relations parent-enfant, code du membre consolidé ou feuille qui sera l'enfant.<br /><br /> Pour les relations de frère, code de l'un des frères.||  
|**Ordre de tri**|Ce paramètre est facultatif<br /><br /> Entier qui indique l'ordre du membre par rapport aux autres membres sous le parent. Chaque membre enfant doit avoir un identificateur unique.||  
|**ErrorCode**|Affiche un code d'erreur. Pour tous les enregistrements dont la valeur **ImportStatus_ID** est **2**, consultez [Erreurs du processus de mise en lots &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md).||  
  
## Voir aussi  
 [Présentation : Importation de données à partir de tables &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Afficher les erreurs rencontrées lors de la mise en lots &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)   
 [Erreurs du processus de mise en lots &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md)  
  
  