---
title: Nom d’élément (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4f19696ae5eea630a6fe879b603b72c4e955b1ac
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="name-element-xmla"></a>Élément Name (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
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
|[Attribut](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|1-1 : élément requis qui apparaît une fois et une seule.|  
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
 [Insérer un élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Élément de langage &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md)   
 [Mettre à jour, élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
