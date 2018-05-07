---
title: Ensemble de lignes DISCOVER_ENUMERATORS | Documents Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4324869aec4da69731f6256148a4767b23ee6804
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="discoverenumerators-rowset"></a>Ensemble de lignes DISCOVER_ENUMERATORS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Retourne une liste des noms, types de données et valeurs d'énumération d'énumérateurs pris en charge par le fournisseur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA (XML for Analysis ) pour une source de données spécifique. Le fournisseur XMLA publie toutes les constantes d'énumération qu'il reconnaît.  
  
 Si vous appelez le [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) méthode avec la **DISCOVER_ENUMERATORS** valeur d’énumération dans le [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) élément, le **Discover** méthode retourne la **DISCOVER_ENUMERATORS** de lignes du schéma.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Pour chaque énumérateur, il existe plusieurs éléments, un pour chaque valeur de l'énumération. L'ensemble de lignes qui représente chaque énumérateur est en deux dimensions, et le nom de l'énumérateur peut être répété pour les éléments qui appartiennent à la même énumération.  
  
 L'ensemble de lignes **DISCOVER_ENUMERATORS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur| Description|  
|-----------------|--------------------|------------|-----------------|  
|**CommandBars (index)**|**DBTYPE_WSTR**||Nom de l'énumérateur qui contient un ensemble de valeurs.|  
|**EnumDescription**|**DBTYPE_WSTR**||Description localisable de l'énumérateur. Peut être **NULL**.|  
|**EnumType**|**DBTYPE_WSTR**||Type de données des valeurs de l'énumération.|  
|**ElementName**|**DBTYPE_WSTR**||Nom de l'un des éléments de valeur dans l'ensemble d'énumérateurs.<br /><br /> Exemple : **TDP**|  
|**ElementDescription**|**DBTYPE_WSTR**||(Facultatif) Description localisable de l'élément. Peut être **NULL**.|  
|**ElementValue**|**DBTYPE_WSTR**||Valeur de l'élément. Peut être **NULL**.<br /><br /> Exemple : **01**|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes **DISCOVER_ENUMERATORS** peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|**CommandBars (index)**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
