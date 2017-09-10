---
title: Ensemble de lignes DISCOVER_ENUMERATORS | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
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
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 66ad0a7e82cb1b74108a1275a9e0a7363183d051
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="discoverenumerators-rowset"></a>Ensemble de lignes DISCOVER_ENUMERATORS
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
  
  
