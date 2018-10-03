---
title: Ensemble de lignes DISCOVER_DIMENSION_STAT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 639f8cd7-3b43-40d5-8b84-552daf60d484
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 39ae0bed8c0e0ff7eb272062b79b870dfb31157e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094979"
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
  
  
