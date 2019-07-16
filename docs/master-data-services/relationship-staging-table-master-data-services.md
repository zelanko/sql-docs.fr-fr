---
title: Table de mise en lots des relations (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 04/01/2016
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- relationships staging table [Master Data Services]
- database [Master Data Services], relationships table
ms.assetid: e19b6002-67bd-4e7d-9f19-ecb455522b1a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 77d4bd0bfab8b2c1a7337cae1f5d96300b7f3625
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67910004"
---
# <a name="relationship-staging-table-master-data-services"></a>Table de mise en lots des relations (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Utilisez la table de mise en lots des relations (stg.name_Relationship) dans la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] pour modifier l’emplacement des membres dans une hiérarchie explicite, en fonction de la relation que les membres entretiennent les uns par rapport aux autres.  
  
##  <a name="TableColumns"></a> Colonnes de table  
 Le tableau suivant explique la fonction de chacun des champs de la table de mise en lots Relation.  
  
|Nom de la colonne|Description|Value|  
|-----------------|-----------------|-----------|  
|**ID**|Identificateur automatiquement affecté.|N'entrez pas de valeur dans ce champ. Si le lot n'a pas été traité, ce champ est vide.|  
|**RelationshipType**|Obligatoire<br /><br /> Type de relation défini.|Les valeurs possibles sont les suivantes :<br /><br /> **1**: parent<br /><br /> **2**: frère (au même niveau)|  
|**ImportStatus_ID**|Obligatoire<br /><br /> État du processus d'importation.|Les valeurs possibles sont les suivantes :<br /><br /> **0**, que vous spécifiez pour indiquer que l'enregistrement est prêt pour la mise en lots ;<br /><br /> **1**, qui est affecté automatiquement et qui indique que le processus de mise en lots pour l'enregistrement a réussi ;<br /><br /> **2**, qui est affecté automatiquement et qui indique que le processus de mise en lots pour l'enregistrement a échoué.|  
|**Batch_ID**|Requis par le service Web uniquement<br /><br /> Identificateur automatiquement affecté qui regroupe des enregistrements pour la mise en lots.<br /><br /> Si le lot n'a pas été traité, ce champ est vide.|Cet identificateur, affiché dans l'interface utilisateur [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] dans la colonne **ID** , est affecté à tous les membres du lot.|  
|**BatchTag**|Requis, sauf par le service Web<br /><br /> Nom unique du lot, jusqu'à 50 caractères.||  
|**HierarchyName**|Obligatoire<br /><br /> Nom de hiérarchie explicite. Chaque membre consolidé ne peut appartenir qu'à une seule hiérarchie.||  
|**ParentCode**|Obligatoire<br /><br /> Pour les relations parent-enfant, code du membre consolidé qui sera le parent du membre feuille ou consolidé enfant.<br /><br /> Pour les relations de frère, code de l'un des frères.||  
|**ChildCode**|Obligatoire<br /><br /> Pour les relations parent-enfant, code du membre consolidé ou feuille qui sera l'enfant.<br /><br /> Pour les relations de frère, code de l'un des frères.||  
|**Ordre de tri**|Facultatif<br /><br /> Entier qui indique l'ordre du membre par rapport aux autres membres sous le parent. Chaque membre enfant doit avoir un identificateur unique.||  
|**ErrorCode**|Affiche un code d'erreur. Pour tous les enregistrements dont la valeur **ImportStatus_ID** est **2**, consultez [Erreurs du processus de mise en lots &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md).||  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble : importation de données à partir de tables &#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)   
 [Afficher les erreurs rencontrées lors de la mise en lots &#40;Master Data Services&#41;](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)   
 [Erreurs du processus de mise en lots &#40;Master Data Services&#41;](../master-data-services/staging-process-errors-master-data-services.md)  
  
  
