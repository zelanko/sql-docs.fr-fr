---
title: Ensemble de lignes DISCOVER_KEYWORDS (XMLA) | Microsoft Docs
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
- DISCOVER_KEYWORDS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_KEYWORDS rowset
ms.assetid: 99945e53-3a1b-4d7b-9aff-712977db8b2d
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a8be22c5132ed85ecb515ccadce20ecd593818a2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241549"
---
# <a name="discoverkeywords-rowset-xmla"></a>Ensemble de lignes DISCOVER_KEYWORDS (XMLA)
  Retourne des informations sur les mots clés réservés par le fournisseur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA).  
  
 Si vous appelez le [Discover](../../xmla/xml-elements-methods-discover.md) méthode avec le `DISCOVER_KEYWORDS` valeur d’énumération dans le [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) élément, le `Discover` méthode retourne la `DISCOVER_KEYWORDS` ensemble de lignes.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_KEYWORDS` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`Keyword`|`DBTYPE_WSTR`||Liste de tous les mots clés réservés par un fournisseur.<br /><br /> Exemple : `AND`|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_KEYWORDS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`Keyword`|`DBTYPE_WSTR`|Facultatif.|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis Schema Rowsets](xml-for-analysis-schema-rowsets.md)   
 [DISCOVER_LITERALS, ensemble de lignes](discover-literals-rowset.md)  
  
  
