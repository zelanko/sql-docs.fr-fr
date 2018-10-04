---
title: Exception, élément (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Exception Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Exception
- urn:schemas-microsoft-com:xml-analysis#Exception
- microsoft.xml.analysis.exception
helpviewer_keywords:
- Exception element
ms.assetid: 0be4cc2f-c03e-490a-a6f7-8b1ede5d09ba
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e447bda3d52ac63125f3a96769fcee2c0158494c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178539"
---
# <a name="exception-element-xmla"></a>Élément Exception (XMLA)
  Indique qu’une exception a été retournée à partir d’un [Discover](../xml-elements-methods-discover.md) ou [Execute](../xml-elements-methods-execute.md) appel de méthode.  
  
 **Namespace** http://schemas.microsoft.com/analysisservices/2003/exception  
  
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
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Racine](root-element-xmla.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 S'il se produit pendant l'exécution d'un appel de méthode `Discover` ou d'une commande XMLA dans un appel de méthode `Execute` une erreur qui empêche la méthode ou la commande de se terminer, l'élément `root` pour cette méthode ou cette commande contient un élément `Exception` et un élément `Messages`. L'élément `Exception` indique qu'une erreur a fait échouer la méthode ou la commande et l'élément `Messages` contient la liste des messages d'erreur ou d'avertissement relatifs à l'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages élément &#40;XMLA&#41;](messages-element-xmla.md)   
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
