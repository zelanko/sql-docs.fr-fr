---
title: Élément d’instruction (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 49238b50457a586bbf23cc75ee454003c57ac04e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979161"
---
# <a name="statement-element-xmla"></a>Élément Statement (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contient une requête ou une instruction à transmettre à l’aide de la **Execute** méthode à une instance d’Analysis Services.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <Statement>...</Statement>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques d’éléments  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|String|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Commandee](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Le **instruction** commande exécute une requête ou une instruction sur le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] prend en charge les langages suivants :  
  
-   MDX (Multidimensional Expressions)  
  
-   DMX (Data Mining Extensions)  
  
-   Un sous-ensemble de SQL (Structured Query Language)  
  
## <a name="see-also"></a>Voir aussi
 [Commandes &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
