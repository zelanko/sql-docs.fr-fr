---
title: Ensemble de lignes DISCOVER_PARTITION_DIMENSION_STAT | Documents Microsoft
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
ms.assetid: bf4626b3-4d6b-4795-bb01-df335fb9c09a
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 798fa10d608db06da3a45041df25c11047dc7a7f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041492"
---
# <a name="discoverpartitiondimensionstat-rowset"></a>DISCOVER_PARTITION_DIMENSION_STAT, ensemble de lignes
  Retourne des statistiques sur la dimension associée à une partition  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_PARTITION_DIMENSION_STAT` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restriction|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Requis|Nom de la base de données.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Requis|Nom du cube ou du modèle tabulaire.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Requis|Nom du groupe de mesures.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Requis|Nom de la partition.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Nom de la dimension.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Nom d'un attribut dans la dimension.|  
|`ATTRIBUTE_INDEXED`|`DBTYPE_BOOL`||Si true, indique que l'attribut est indexé ; sinon false.|  
|`ATTRIBUTE_COUNT_MIN`|`DBTYPE_I8`||Nombre minimal d'attributs.|  
|`ATTRIBUTE_COUNT_MAX`|`DBTYPE_I8`||Nombre maximal d'attributs.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd8e-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  