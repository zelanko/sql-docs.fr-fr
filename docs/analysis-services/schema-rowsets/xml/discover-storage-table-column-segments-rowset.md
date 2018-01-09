---
title: Ensemble de lignes DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
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
ms.assetid: 3e514715-9fe6-4e6a-accb-4149ffd7e0bf
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 878568721816c90e202727dc3e516370f9c3ee56
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="discoverstoragetablecolumnsegments-rowset"></a>Ensemble de lignes DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Fournit des informations au niveau de la colonne et du segment sur les tables de stockage utilisé par une base de données Analysis Services en cours d’exécution tabulaire ou [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] mode. Cet ensemble de lignes est utilisé principalement pour le dépannage et l'analyse.  
  
 **S'applique à :** modèles tabulaires  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 L'ensemble de lignes **DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS** contient les colonnes suivantes.  
  
|**Nom de colonne**|**Indicateur de type**|**Restriction**|**Description**|  
|---------------------|------------------------|---------------------|---------------------|  
|**NOM_BASE_DE_DONNÉES**|**DBTYPE_WSTR**|Oui|Spécifie la base de données tabulaire.<br /><br /> L'ensemble de lignes **DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS** peut être restreint à l'aide de cette colonne. Si omis, le nom de la base de données active est utilisé.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Oui|Nom du modèle.<br /><br /> L'ensemble de lignes **DISCOVER_STORAGE_TABLES** peut être restreint à l'aide de cette colonne.|  
|**NOM_GROUPE_MESURES**|**DBTYPE_WSTR**|Oui|Nom du groupe de mesures.|  
|**NOM_PARTITION**|**DBTYPE_WSTR**|Oui|Nom de la partition.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Nom de la dimension.|  
|**TABLE_ID**|**DBTYPE_WSTR**||ID interne du segment de table.|  
|**COLUMN_ID**|**DBTYPE_WSTR**||ID interne de la colonne.|  
|**_NOMBRE DE SEGMENT**|**DBTYPE_I8**||Nombre ordinal du segment de table.|  
|**TABLE_PARTTION_NUMBER**|**DBTYPE_I8**||Nombre ordinal de la partition.|  
|**RECORDS_COUNT**|**DBTYPE_I8**||Nombre d'enregistrements dans la partition.|  
|**ALLOCATED_SIZE**|**DBTYPE_UI8**||Taille allouée en octets au segment de colonne.|  
|**USED_SIZE**|**DBTYPE_UI8**||Taille en octets utilisée par le segment de colonne.|  
|**COMPRESSION_TYPE**|**DBTYPE_WSTR**||Type de compression appliqué au segment de colonne. Cette valeur est destinée uniquement à une utilisation interne et de support technique. Microsoft ne publie pas de valeurs valides ou de descriptions pour cette colonne.|  
|**BITS_COUNT**|**DBTYPE_I8**||Nombre de bits.|  
|**BOOKMARK_BITS_COUNT**|**DBTYPE_I8**||Nombre de bits de signet.|  
|**VERTIPAQ_STATE**|**DBTYPE_WSTR**||État de compression VertiPaq pour ce segment de colonne. Les valeurs possibles sont les suivantes :<br /><br /> SKIPPED – la compression VertiPaq a été ignorée.<br /><br /> COMPLETED – la compression VertiPaq s'est terminée correctement.<br /><br /> TIMEBOXED - un délai a été imparti pour la compression VertiPaq.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd45-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageSegments|  
  
## <a name="example"></a> Exemple  
 La requête suivante retourne les segments de la table stockage associés à l'attribut de modèle LastName, dans la base de données actuelle.  
  
```  
SELECT DISTINCT TABLE_ID, COLUMN_ID   
FROM $system.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS  
WHERE COLUMN_ID = 'LastName'  
ORDER BY TABLE_ID  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
