---
title: Ensemble de lignes DISCOVER_PROPERTIES | Microsoft Docs
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
- DISCOVER_PROPERTIES
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_PROPERTIES rowset
ms.assetid: 3e2b50e2-3855-4091-8b02-4968e8e57d4c
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc02dd29ee02ad4d1730a6af72c5df3c3fee1c55
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271835"
---
# <a name="discoverproperties-rowset"></a>Ensemble de lignes DISCOVER_PROPERTIES
  Retourne une liste d'informations et de valeurs sur les propriétés standard et spécifiques au fournisseur prises en charge par le fournisseur XML for Analysis (XMLA) [!INCLUDE[msCoName](../../../includes/msconame-md.md)] pour la source de données spécifiée. Les propriétés non prises en charge ne sont pas répertoriées dans le jeu de résultats retourné.  
  
 Si vous appelez le [Discover](../../xmla/xml-elements-methods-discover.md) méthode avec le `DISCOVER_PROPERTIES` valeur d’énumération dans le [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) élément, le `Discover` méthode retourne la `DISCOVER_PROPERTIES` ensemble de lignes...  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_PROPERTIES` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Type|Longueur|Description|  
|-----------------|----------|------------|-----------------|  
|`PropertyName`|`DBTYPE_WSTR`||Nom de la propriété.|  
|`PropertyDescription`|`DBTYPE_WSTR`||Description (texte) localisable de la propriété. Peut retourner `NULL`.|  
|`PropertyType`|`DBTYPE_WSTR`||Type de données XML de la propriété.<br /><br /> Peut retourner `NULL`.|  
|`PropertyAccessType`|`DBTYPE_WSTR`||Accès pour la propriété. La valeur peut être `Read`, `Write` ou `ReadWrite`.|  
|`IsRequired`|`DBTYPE_BOOL`||Valeur booléenne qui indique si une propriété est obligatoire.<br /><br /> True si une propriété est obligatoire ; false dans le cas contraire.<br /><br /> Peut retourner `NULL`.|  
|`Value`|`DBTYPE_WSTR`||Valeur actuelle de la propriété.<br /><br /> Peut retourner `NULL`.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="restriction-columns"></a>Colonnes de restriction  
 L'ensemble de lignes `DISCOVER_PROPERTIES` peut être restreint sur la colonne répertoriée dans le tableau suivant.  
  
|Nom de colonne|Indicateur de type|État de la restriction|  
|-----------------|--------------------|-----------------------|  
|`PropertyName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  
