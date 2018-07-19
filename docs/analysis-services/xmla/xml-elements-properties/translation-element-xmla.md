---
title: Élément Translation (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8b6c50664cdce599128be9f0ad15a10e33b77ec6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38047183"
---
# <a name="translation-element-xmla"></a>Élément Translation (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Définit une traduction pour un membre d'attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Translations>  
   ...  
   <Translation>  
      <Language>...</Language>  
      <Name>...</Name>  
   </Translation>  
   ...  
</Translations>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques d’éléments  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Traductions](../../../analysis-services/xmla/xml-elements-properties/translations-element-xmla.md)|  
|Éléments enfants|[Language](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md), [Name](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Un élément **Translation** définit les informations nécessaires pour associer un membre d'attribut à une traduction définie pour un attribut au cours d'une commande [Insert](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md) ou [Update](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md) .  
  
## <a name="see-also"></a>Voir aussi
 [Propriétés &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
