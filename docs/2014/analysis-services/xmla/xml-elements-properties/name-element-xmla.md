---
title: Nom d’élément (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: d3ae469cc1a02a02dc2bdb2ff7d6db7f75a46a69
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143766"
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
|[Traduction](translation-element-xmla.md)|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Attribut](attribute-element-xmla.md), [traduction](translation-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Pour les éléments `Attribute`, l'élément `Name` contient le nom du membre d'attribut à insérer ou à mettre à jour lors des commandes `Insert` ou `Update` respectivement.  
  
 Pour les éléments `Translation`, l'élément `Name` contient la légende du membre d'attribut dans la langue spécifiée par l'élément `Language` de l'objet `Translation` parent. Si l'élément `Name` n'est pas spécifié ou contient une chaîne vide, la valeur de l'élément `Name` pour l'élément `Attribute` contenant l'élément `Translation` est utilisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Insérer l’élément &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Élément de langage &#40;XMLA&#41;](language-element-xmla.md)   
 [Mettre à jour d’élément &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  