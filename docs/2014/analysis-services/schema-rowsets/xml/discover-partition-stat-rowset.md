---
title: Ensemble de lignes DISCOVER_PARTITION_STAT | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 20d339e2-f47f-437f-94d5-5b00b400356a
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 98db8d43f86cc9acaf612da8180498d22e01d037
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153809"
---
# <a name="discoverpartitionstat-rowset"></a>DISCOVER_PARTITION_STAT, ensemble de lignes
  Retourne des statistiques sur les agrégations dans une partition particulière.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_PARTITION_STAT` ensemble de lignes contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restriction|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Requis|Nom de la base de données contient la dimension.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Requis|Nom du cube ou du modèle tabulaire contenant la partition.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Requis|Nom d'un groupe de mesures dans la dimension.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Requis|Nom d'une partition.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|`AGGREGATION_NAME`|`DBTYPE_WSTR`||Nom de l'agrégation.|  
|`AGGREGATION_SIZE`|`DBTYPE_I8`||Taille de l'agrégation.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd8f-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionStat|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](xml-for-analysis-schema-rowsets.md)  
  
  