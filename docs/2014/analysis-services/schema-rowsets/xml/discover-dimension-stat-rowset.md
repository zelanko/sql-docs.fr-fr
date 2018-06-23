---
title: Ensemble de lignes DISCOVER_DIMENSION_STAT | Documents Microsoft
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
ms.assetid: 639f8cd7-3b43-40d5-8b84-552daf60d484
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c00442ffcc7af38a24ce0fcb035aad515d9942f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042095"
---
# <a name="discoverdimensionstat-rowset"></a>DISCOVER_DIMENSION_STAT, ensemble de lignes
  Fournit des informations sur une dimension, y compris le nom de la base de données qui le contient, le nom de dimension, ses attribut, et le nombre des membres pour chaque attribut. Dans un modèle tabulaire, cela correspond aux colonnes dans une table et au nombre de valeurs dans chaque colonne.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_DIMENSION_STAT` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restriction|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Requis|Nom de la base de données contient la dimension.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`|Requis|Nom de la dimension.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Nom d'un attribut dans la dimension.|  
|`ATTRIBUTE_COUNT`|`DBTYPE_I8`||Nombre de valeurs dans l'attribut nommé. Pour un modèle tabulaire, la valeur est toujours identique au nombre de lignes dans la table.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd90-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  