---
title: Ensemble de lignes DISCOVER_SCHEMA_ROWSETS | Microsoft Docs
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
- DISCOVER_SCHEMA_ROWSETS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_SCHEMA_ROWSETS rowset
ms.assetid: e5012aa0-6ef8-497f-96c1-2772e2394f62
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fa16f7ff677efd8e39367b9e618bdc95d778b405
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37220239"
---
# <a name="discoverschemarowsets-rowset"></a>Ensemble de lignes DISCOVER_SCHEMA_ROWSETS
  Retourne les noms, restrictions, description et autres informations pour toutes les valeurs d'énumération et toutes les valeurs d'énumération supplémentaires spécifiques au fournisseur prises en charge par le fournisseur [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA (XML for Analysis).  
  
 Si vous appelez le [Discover](../../xmla/xml-elements-methods-discover.md) méthode avec le `DISCOVER_SCHEMA_ROWSETS` valeur d’énumération dans le [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) élément, le `Discover` méthode retourne la `DISCOVER_SCHEMA_ROWSETS` ensemble de lignes.  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes DISCOVER_SCHEMA_ROWSETS contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Longueur|Description|  
|-----------------|--------------------|------------|-----------------|  
|`SchemaName`|`DBTYPE_WSTR`||Nom du schéma ou de la requête. Cette requête retourne les valeurs de l'énumération *RequestTypes* .|  
|`SchemaGuid`|`DBTYPE_GUID`||GUID du schéma.|  
|`Restrictions`|`DBTYPE_HCHAPTER`||Tableau des restrictions prises en charge par le fournisseur.|  
|`Description`|`DBTYPE_WSTR`||Description localisable du schéma.|  
|`RestrictionsMask`|`DBTYPE_UI8`|||  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
 Pour un fournisseur qui prend en charge trois restrictions pour l'ensemble de lignes de schéma DBSCHEMA_MEMBERS, le tableau `Restrictions` peut retourner le résultat suivant. Les éléments du résultat font référence aux noms de colonne dans le schéma.  
  
```  
<Restrictions>  
      <CATALOG_NAME type="string" />   
      <SCHEMA_NAME type="string" />   
      <CUBE_NAME type="string" />   
</Restrictions>  
```  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 Le `DISCOVER_SCHEMA_ROWSETS` ensemble de lignes peut être restreint sur les colonnes répertoriées dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`SchemaName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  
