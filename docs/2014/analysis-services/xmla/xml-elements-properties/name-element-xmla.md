---
title: Nom de l’élément (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Name Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Name
- urn:schemas-microsoft-com:xml-analysis#Name
- microsoft.xml.analysis.name
helpviewer_keywords:
- Name element
ms.assetid: cc1a93df-0b1b-4c38-9183-4f11c26fea6a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 422bd152e82a471ce0f130a26aaa12a56026419a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48127899"
---
# <a name="name-element-xmla"></a>Élément Name (XMLA)
  Contient le nom d’un membre d’attribut pour le parent [attribut](attribute-element-xmla.md) ou [traduction](translation-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Attribute> <!-- or Translation -->  
   ...  
   <Name>...</Name>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Ancêtre ou Parent :|Cardinalité|  
|[Attribute](attribute-element-xmla.md)|1-1 : élément requis qui apparaît une fois et une seule.|  
|[traduction](translation-element-xmla.md)|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Attribut](attribute-element-xmla.md), [traduction](translation-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour les éléments `Attribute`, l'élément `Name` contient le nom du membre d'attribut à insérer ou à mettre à jour lors des commandes `Insert` ou `Update` respectivement.  
  
 Pour les éléments `Translation`, l'élément `Name` contient la légende du membre d'attribut dans la langue spécifiée par l'élément `Language` de l'objet `Translation` parent. Si l'élément `Name` n'est pas spécifié ou contient une chaîne vide, la valeur de l'élément `Name` pour l'élément `Attribute` contenant l'élément `Translation` est utilisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Insérer un élément &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Élément de langage &#40;XMLA&#41;](language-element-xmla.md)   
 [Mettre à jour d’élément &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
