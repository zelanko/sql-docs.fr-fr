---
title: Ensemble de lignes DISCOVER_STORAGE_TABLE_COLUMNS | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 24abb88e-33a9-4ae2-829d-cdef0ff22ec1
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6ca81b54546e3ff69c42ea60484e462513443c5e
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="discoverstoragetablecolumns-rowset"></a>Ensemble de lignes DISCOVER_STORAGE_TABLE_COLUMNS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Fournit des informations au niveau des colonnes des tables de stockage utilisé par une base de données Analysis Services en cours d’exécution en mode SharePoint ou tabulaire.  
  
 **S'applique à :** modèles tabulaires  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le **DISCOVER_STORAGE_TABLE_COLUMNS** ensemble de lignes contient les colonnes suivantes.  
  
|**Nom de colonne**|**Indicateur de type**|**Restriction**|**Description**|  
|---------------------|------------------------|---------------------|---------------------|  
|**NOM_BASE_DE_DONNÉES**|**DBTYPE_WSTR**|Oui|Spécifie le nom de la base de données qui contient les tables. Si omis, le nom de la base de données active est utilisé.<br /><br /> Le **DISCOVER_STORAGE_TABLE_COLUMNS** ensemble de lignes peut être restreint à l’aide de cette colonne.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Oui|Spécifie le cube ou modèle qui contient les tables.<br /><br /> L'ensemble de lignes **DISCOVER_STORAGE_TABLES** peut être restreint à l'aide de cette colonne.|  
|**NOM_GROUPE_MESURES**|**DBTYPE_WSTR**|Oui|Nom du groupe de mesures.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Nom de la dimension.|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||Le nom de l’attribut.|  
|**TABLE_ID**|**DBTYPE_WSTR**||L’ID de la table.|  
|**COLUMN_ID**|**DBTYPE_ WSTR**||ID de la colonne. L'ID de colonne est interne au moteur d'analyse en mémoire xVelocity (VertiPaq) et est uniquement fourni à titre d'information.|  
|**COLUMN_TYPE**|**DBTYPE_WSTR**||Le type de colonne. Le type de colonne est interne au moteur d'analyse en mémoire xVelocity (VertiPaq) et est uniquement fourni à titre d'information.<br /><br /> BASIC_DATA<br /><br /> HIERARCHY_DATAID_TO_POSITION<br /><br /> HIERARCHY_POSITION_TO_DATAID<br /><br /> RELATIONSHIP|  
|**COLUMN_ENCODING**|**DBTYPE_UI8**||Entier qui représente le type d'encodage utilisé pour les données de la colonne.<br /><br /> **0**, utilisé avec **COLUMN_TYPE**: HIERARCHY_DATAID_TO_POSITION, HIERARCHY_POSITION_TO_DATAID, relation<br /><br /> **1**, utilisé avec **COLUMN_TYPE**: BASIC_DATA<br /><br /> **2**, utilisé avec **COLUMN_TYPE**: BASIC_DATA|  
|**TYPE DE DONNÉES**|**DBTYPE_WSTR**||Type de données de la colonne. Présente les valeurs possibles suivantes :<br /><br /> DBTYPE_BOOL<br /><br /> DBTYPE_CY<br /><br /> DBTYPE_DATE<br /><br /> DBTYPE_I4<br /><br /> DBTYPE_I8<br /><br /> DBTYPE_R8<br /><br /> DBTYPE_WSTR<br /><br /> Néant|  
|**ISKEY**|**DBTYPE_BOOL**||**True** si la colonne est utilisé comme une clé primaire ou étrangère ; sinon **false**.|  
|**ISUNIQUE**|**DBTYPE_BOOL**||**True** si les valeurs dans la colonne sont uniques ; sinon **false**.|  
|**ISNULLABLE**|**DBTYPE_BOOL**||**True** si la colonne est nullable ; sinon **false**.|  
|**ISROWNUMBER**|**DBTYPE_BOOL**||**True** si la colonne est une colonne de numéro de ligne. Colonnes de numéro de ligne utilisées en interne par le moteur d'analyse en mémoire xVelocity.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Le tableau suivant fournit le GUID et les valeurs de chaîne qui identifient cet ensemble de lignes.  
  
|Argument|Valeur|  
|--------------|-----------|  
|GUID|a07ccd44-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageTableColumns|  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant utilise une requête DMV pour retourner le jeu de résultats.  
  
```  
SELECT *  
FROM $System.DISCOVER_STORAGE_TABLE_COLUMNS  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes de schéma Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
