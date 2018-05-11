---
title: Élément de langage (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 66b14ca19b6c86d6fb959ff462a0cd0d5118843b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="language-element-xmla"></a>Élément Language (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient l’identificateur de paramètres régionaux (LCID) pour le parent [traduction](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Translation>  
   ...  
   <Language>...</Language>  
   ...  
</Translation>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Entier|  
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Traduction](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Le **langage** élément spécifie le LCID utilisé par le parent **traduction** élément pour assigner le **nom** élément du parent **traduction** élément à un membre d’attribut, pour la langue spécifiée, pendant une **insérer** ou **mise à jour** commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Insérer un élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Nom d’élément &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md)   
 [Mettre à jour, élément & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
