---
title: Ensemble de lignes DISCOVER_ENUMERATORS | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DISCOVER_ENUMERATORS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_ENUMERATORS rowset
ms.assetid: ddc7b13c-3135-4419-8166-eddd459167da
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0be0cb9885cf48911a31ba4181a235eae032094b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="discoverenumerators-rowset"></a>Ensemble de lignes DISCOVER_ENUMERATORS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Retourne une liste de noms, les types de données et les valeurs d’énumération d’énumérateurs pris en charge par le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML pour le fournisseur Analysis (XMLA) pour une source de données spécifique. Le fournisseur XMLA publie toutes les constantes d'énumération qu'il reconnaît.  
  
 Si vous appelez le [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) méthode avec la **DISCOVER_ENUMERATORS** valeur d’énumération dans le [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) élément, le **Discover** méthode retourne la **DISCOVER_ENUMERATORS** de lignes du schéma.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Pour chaque énumérateur, il existe plusieurs éléments, un pour chaque valeur de l'énumération. L'ensemble de lignes qui représente chaque énumérateur est en deux dimensions, et le nom de l'énumérateur peut être répété pour les éléments qui appartiennent à la même énumération.  
  
 L'ensemble de lignes **DISCOVER_ENUMERATORS** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
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
 [Ensembles de lignes de schéma XML for Analysis](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
