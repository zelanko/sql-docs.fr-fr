---
title: Élément exception (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e5b9847f1328fb0f0c7b6c1503708ca0b75b585c
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="exception-element-xmla"></a>Élément Exception (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Indique qu’une exception a été retournée par un [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) ou [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) appel de méthode.  
  
 **espace de noms** `http://schemas.microsoft.com/analysisservices/2003/exception`  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<root>  
   ...  
   <Exception />  
   ...  
</root>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[racine](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 S'il se produit pendant l'exécution d'un appel de méthode **Discover** ou d'une commande XMLA dans un appel de méthode **Execute** une erreur qui empêche la méthode ou la commande de se terminer, l'élément **root** pour cette méthode ou cette commande contient un élément **Exception** et un élément **Messages** . L'élément **Exception** indique qu'une erreur a fait échouer la méthode ou la commande et l'élément **Messages** contient la liste des messages d'erreur ou d'avertissement relatifs à l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément de messages &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)   
 [Propriétés & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
