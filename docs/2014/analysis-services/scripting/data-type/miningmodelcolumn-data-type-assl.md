---
title: Type de données MiningModelColumn (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MiningModelColumn Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningModelColumn
helpviewer_keywords:
- MiningModelColumn data type
ms.assetid: de8bf815-43b4-4983-bdb9-b67e8563be0e
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6943acb9e15e1133da5aba8c49e0a14f3c61377c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045248"
---
# <a name="miningmodelcolumn-data-type-assl"></a>Type de données MiningModelColumn (ASSL)
  Définit un type de données primitif qui représente des informations sur une colonne dans un [MiningModel](../objects/miningmodel-element-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningModelColumn>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</<Description>  
      <SourceColumnID>...</SourceColumnID>  
            <Usage>...</Usage>  
            <Translations>...</Translations>  
      <Columns>...</Columns>  
      <ModelingFlags>...</ModelingFlags>  
      <Annotations>...</Annotations>  
</MiningModelColumn>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|None|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|[Annotations](../collections/annotations-element-assl.md), [colonnes](../collections/columns-element-assl.md), [Description](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [ModelingFlags](../collections/modelingflags-element-assl.md), [nom](../properties/name-element-assl.md) , [SourceColumnID](../properties/sourcecolumnid-element-assl.md), [traductions](../collections/translations-element-assl.md), [l’utilisation](../properties/usage-element-dimensionattribute-assl.md)|  
|Éléments dérivés|[Colonne](../objects/column-element-assl.md) ([colonnes](../collections/columns-element-assl.md), collection de [MiningModel](../objects/miningmodel-element-assl.md))|  
  
## <a name="remarks"></a>Notes  
 L’élément correspondant dans le modèle d’objet objets AMO (Analysis Management) est <xref:Microsoft.AnalysisServices.MiningModelColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données de script langage XML Analysis Services &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  