---
title: Type de données EmptyResult (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- EmptyResult Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EmptyResult
- olapxmla_EmptyResult
- urn:schemas-microsoft-com:xml-analysis#EmptyResult
helpviewer_keywords:
- EmptyResult data type
ms.assetid: 63818123-acbb-4220-9d60-1aa20a7326a1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dc22612f18faa91e6cd668c022f036aadb9ef176
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088541"
---
# <a name="emptyresult-data-type-xmla"></a>Type de données EmptyResult (XMLA)
  Définit un type de données dérivé qui représente un [racine](../xml-elements-properties/root-element-xmla.md) élément qui ne retourne pas de données à partir d’un [Discover](../xml-elements-methods-discover.md) ou [Execute](../xml-elements-methods-execute.md) appel de méthode.  
  
 **Espace de noms** urn:schemas-microsoft-com:xml-analysis:empty  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:empty">  
   <!-- All elements are inherited from Resultset -->  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Caractéristiques du type de données  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Types de données de base|[Jeu de résultats](resultset-data-type-xmla.md)|  
|Types de données dérivés|None|  
  
## <a name="data-type-relationships"></a>Relations du type de données  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|None|  
|Éléments enfants|None|  
|Éléments dérivés|[Racine](../xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Certaines commandes XMLA (XML for Analysis) ne sont pas supposées retourner de résultat ou ne peuvent pas retourner de résultat à cause d'une erreur. Les commandes XMLA sans résultat retournent le type de données `EmptyResult`, un espace de noms sur l'élément `root`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant représente un élément `root` retourné pour un résultat vide.  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty"/>  
</return>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données XML &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  
