---
title: Élément Translation (XMLA) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Translation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Translation
- microsoft.xml.analysis.translation
- http://schemas.microsoft.com/analysisservices/2003/engine#Translation
helpviewer_keywords:
- Translation element
ms.assetid: ce962d4b-dda9-4a16-a56c-ff7a5275c48a
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 63072fae7d585f18fdc3b3bc1da5ffbef5bb9b8c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152197"
---
# <a name="translation-element-xmla"></a>Élément Translation (XMLA)
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
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|None|  
|Valeur par défaut|None|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Traductions](translations-element-xmla.md)|  
|Éléments enfants|[Language](language-element-xmla.md), [Name](name-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 A `Translation` élément définit les informations nécessaires pour associer un membre d’attribut à une traduction définie pour un attribut donné pendant un [insérer](../xml-elements-commands/insert-element-xmla.md) ou [mise à jour](../xml-elements-commands/update-element-xmla.md) commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;XMLA&#41;](xml-elements-properties.md)  
  
  