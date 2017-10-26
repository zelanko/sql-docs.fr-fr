---
title: "Nom d’élément (XMLA) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Name Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Name
- urn:schemas-microsoft-com:xml-analysis#Name
- microsoft.xml.analysis.name
helpviewer_keywords:
- Name element
ms.assetid: cc1a93df-0b1b-4c38-9183-4f11c26fea6a
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5251f22e39932f49fa4c512b8c5b76a2bf0e7af9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="name-element-xmla"></a>Élément Name (XMLA)
  Contient le nom d’un membre d’attribut pour le parent [attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) ou [traduction](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md) élément.  
  
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
|Type de données et longueur|Chaîne|  
|Valeur par défaut|Aucune|  
|Cardinalité|Consultez le tableau ci-dessous.|  
  
|Ancêtre ou parent|Cardinalité|  
|------------------------|-----------------|  
|[Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|1-1 : élément requis qui apparaît une fois et une seule.|  
|[Traduction](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [traduction](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Pour **attribut** éléments, le **nom** élément contient le nom du membre d’attribut à insérer ou mis à jour au cours du, respectivement, la **insérer** ou **mise à jour** commande.  
  
 Pour **traduction** éléments, le **nom** élément contient la légende du membre d’attribut, dans la langue spécifiée par la **langage** élément du parent **traduction** objet. Si le **nom** élément n’est pas spécifié ou contient une chaîne vide, la valeur de la **nom** , élément pour les **attribut** élément qui contient le **traduction** élément est utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Insérer un élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Élément de langage &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md)   
 [Mettre à jour, élément &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Propriétés &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

