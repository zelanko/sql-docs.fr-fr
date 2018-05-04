---
title: Ensemble de lignes DISCOVER_PARTITION_DIMENSION_STAT | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: bf4626b3-4d6b-4795-bb01-df335fb9c09a
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 14ec5f539005bd736406b82f0c8eac1f49a41259
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="discoverpartitiondimensionstat-rowset"></a>DISCOVER_PARTITION_DIMENSION_STAT, ensemble de lignes
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Retourne des statistiques sur la dimension associée à une partition  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_PARTITION_DIMENSION_STAT** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restriction| Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|Requis|Nom de la base de données.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Requis|Nom du cube ou du modèle tabulaire.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|**NOM_GROUPE_MESURES**|**DBTYPE_WSTR**|Requis|Nom du groupe de mesures.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|**NOM_PARTITION**|**DBTYPE_WSTR**|Requis|Nom de la partition.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Nom de la dimension.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||Nom d'un attribut dans la dimension.|  
|**ATTRIBUTE_INDEXED**|**DBTYPE_BOOL**||Si true, indique que l'attribut est indexé ; sinon false.|  
|**ATTRIBUTE_COUNT_MIN**|**DBTYPE_I8**||Nombre minimal d'attributs.|  
|**ATTRIBUTE_COUNT_MAX**|**DBTYPE_I8**||Nombre maximal d'attributs.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd8e-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>Voir aussi  
 [XML for Analysis ensembles de lignes de schéma](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
