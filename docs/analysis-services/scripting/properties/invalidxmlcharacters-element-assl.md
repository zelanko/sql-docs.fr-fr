---
title: "Élément InvalidXmlCharacters (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: InvalidXmlCharacters Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: InvalidXmlCharacters
helpviewer_keywords: InvalidXmlCharacters element
ms.assetid: 92b1210c-1075-4f2f-a2c4-dfdc6d7e5c05
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f9a13652a928b850db2891f9e11c684a53ac1010
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="invalidxmlcharacters-element-assl"></a>Élément InvalidXmlCharacters (ASSL)
  Spécifie la méthode de traitement des caractères XML dans les données sources qui ne sont pas valides.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataItem>  
   ...  
   <InvalidXmlCharacters>...</InvalidXmlCharacters>  
   ...  
</DataItem  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|*Conserver*|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes du tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Conserver*|Les caractères XML non valides sont conservés.|  
|*Supprimer*|Les caractères XML non valides sont supprimés.|  
|*Remplacer*|Les caractères XML non valides sont remplacés par des points d'interrogation (?)|  
  
 L’énumération qui correspond aux valeurs autorisées pour **InvalidXmlCharacters** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.InvalidXmlCharacters>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
