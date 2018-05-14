---
title: Clé d’élément (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3971abfd4c5bbcc90d43d0f427353f24967b0c5d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="key-element-xmla"></a>Élément Key (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient une valeur de clé de membre pour un membre d'attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Keys>  
   ...  
   <Key>...</Key>  
   ...  
</Keys>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Tout|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Clés](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le type de données utilisé par cet élément doit correspondre au type de données de la colonne clé appropriée de l'attribut spécifié. Si les éléments **Key** ne sont pas spécifiés pour un élément **Attribute** parent, les éléments **AttributeName** et **Name** spécifiés dans l'élément **Attribute** parent sont utilisés pour identifier le membre d'attribut à modifier.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément attribute & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)   
 [Élément AttributeName & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)   
 [Supprimer l’élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [Insérer un élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Élément KeyColumn & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)   
 [Mettre à jour, élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Où, élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
