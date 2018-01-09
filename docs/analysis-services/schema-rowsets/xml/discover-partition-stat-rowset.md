---
title: Ensemble de lignes DISCOVER_PARTITION_STAT | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 20d339e2-f47f-437f-94d5-5b00b400356a
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 649475fa5fd1a4e0bb2a6c734f916270ac7f9a64
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="discoverpartitionstat-rowset"></a>DISCOVER_PARTITION_STAT, ensemble de lignes
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Retourne des statistiques sur les agrégations dans une partition particulière.  
  
 **S'applique à :** modèles tabulaires, modèles multidimensionnels  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_PARTITION_STAT** contient les colonnes suivantes.  
  
|Nom de colonne|Indicateur de type|Restriction|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**NOM_BASE_DE_DONNÉES**|**DBTYPE_WSTR**|Requis|Nom de la base de données contient la dimension.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Requis|Nom du cube ou du modèle tabulaire contenant la partition.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|**NOM_GROUPE_MESURES**|**DBTYPE_WSTR**|Requis|Nom d'un groupe de mesures dans la dimension.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|**NOM_PARTITION**|**DBTYPE_WSTR**|Requis|Nom d'une partition.<br /><br /> Cette colonne est requise dans la liste de restriction.|  
|**AGGREGATION_NAME**|**DBTYPE_WSTR**||Nom de l'agrégation.|  
|**AGGREGATION_SIZE**|**DBTYPE_I8**||Taille de l'agrégation.|  
  
 Cet ensemble de lignes de schéma n'est pas trié.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd8f-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionStat|  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma XML for Analysis](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
