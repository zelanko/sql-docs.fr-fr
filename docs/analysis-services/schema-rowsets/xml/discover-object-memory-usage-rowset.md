---
title: Ensemble de lignes DISCOVER_OBJECT_MEMORY_USAGE | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_OBJECT_MEMORY_USAGE rowset
ms.assetid: 211cfa04-7bd6-43fe-8bd5-bfbff78bdafb
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 23243ea41463a735ce4e44a586b828af7640ec97
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="discoverobjectmemoryusage-rowset"></a>Ensemble de lignes DISCOVER_OBJECT_MEMORY_USAGE
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Fournit des informations sur les ressources de mémoire utilisée par les objets.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_OBJECT_MEMORY_USAGE** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**||Chemin d'accès au parent de l'objet actuel.|  
|**OBJECT_ID**|**DBTYPE_WSTR**||ID de l'objet tel que défini lors de la création.|  
|**OBJECT_MEMORY_SHRINKABLE**|**DBTYPE_I8**||Quantité totale de mémoire (en octets) utilisée par tous les objets réductibles appartenant directement à l'objet actuel. La valeur actuelle n'inclut pas la mémoire des objets détenus par les objets nommés appartenant à l'objet actuel.|  
|**OBJECT_MEMORY_NONSHRINKABLE**|**DBTYPE_I8**||Quantité de mémoire (en octets) de tous les objets non réductibles appartenant directement à l'objet actuel. La valeur actuelle n'inclut pas la mémoire des objets détenus par les objets nommés appartenant à l'objet actuel.|  
|**OBJECT_VERSION**|**DBTYPE_I4**||Numéro de version de métadonnées de l'objet. Ce nombre change chaque fois que l'objet est modifié.|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||Numéro de lignage des données contenues dans l'objet. Ce nombre est incrémenté chaque fois que l'objet est traité.|  
|**OBJECT_TYPE_ID**|**DBTYPE_I4**||Réservé à une utilisation interne.|  
|**OBJECT_TIME_CREATED**|**DBTYPE_DBTIMESTAMP**||Heure UTC du serveur au moment où l'objet a été créé.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_OBJECT_MEMORY_USAGE** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|Ce paramètre est facultatif.|  
|**OBJECT_ID**|**DBTYPE_WSTR**|Ce paramètre est facultatif|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
