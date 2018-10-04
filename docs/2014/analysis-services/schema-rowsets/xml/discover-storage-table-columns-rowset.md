---
title: Ensemble de lignes DISCOVER_STORAGE_TABLE_COLUMNS | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 24abb88e-33a9-4ae2-829d-cdef0ff22ec1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 240230784860e9484ebc03ba6740eaf5d56387fa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089069"
---
# <a name="discoverstoragetablecolumns-rowset"></a>Ensemble de lignes DISCOVER_STORAGE_TABLE_COLUMNS
  Fournit des informations au niveau de la colonne concernant les tables de stockage utilisées par une base de données Analysis Services exécutée en mode SharePoint ou tabulaire.  
  
 **S'applique à :** modèles tabulaires  
  
## <a name="rowset-columns"></a>Colonnes de l'ensemble de lignes  
 Le `DISCOVER_STORAGE_TABLE_COLUMNS` ensemble de lignes contient les colonnes suivantes.  
  
|**Nom de colonne**|**Indicateur de type**|**Restriction**|**Description**|  
|---------------------|------------------------|---------------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Oui|Spécifie le nom de la base de données qui contient les tables. Si omis, le nom de la base de données active est utilisé.<br /><br /> Le `DISCOVER_STORAGE_TABLE_COLUMNS` ensemble de lignes peut être restreint à l’aide de cette colonne.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Oui|Spécifie le cube ou modèle qui contient les tables.<br /><br /> Le `DISCOVER_STORAGE_TABLES` ensemble de lignes peut être restreint à l’aide de cette colonne.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Oui|Nom du groupe de mesures.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Nom de la dimension.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Le nom de l’attribut.|  
|`TABLE_ID`|`DBTYPE_WSTR`||L’ID de la table.|  
|`COLUMN_ID`|`DBTYPE_ WSTR`||ID de la colonne. L'ID de colonne est interne au moteur d'analyse en mémoire xVelocity (VertiPaq) et est uniquement fourni à titre d'information.|  
|`COLUMN_TYPE`|`DBTYPE_WSTR`||Le type de colonne. Le type de colonne est interne au moteur d'analyse en mémoire xVelocity (VertiPaq) et est uniquement fourni à titre d'information.<br /><br /> -BASIC_DATA<br />-HIERARCHY_DATAID_TO_POSITION<br />-HIERARCHY_POSITION_TO_DATAID<br />-LA RELATION|  
|`COLUMN_ENCODING`|`DBTYPE_UI8`||Entier qui représente le type d'encodage utilisé pour les données de la colonne.<br /><br /> -   **0**, utilisé avec `COLUMN_TYPE`: HIERARCHY_DATAID_TO_POSITION, HIERARCHY_POSITION_TO_DATAID, relation<br />-   **1**, utilisé avec `COLUMN_TYPE`: BASIC_DATA<br />-   **2**, utilisé avec `COLUMN_TYPE`: BASIC_DATA|  
|`DATATYPE`|`DBTYPE_WSTR`||Type de données de la colonne. a les valeurs possibles suivantes :<br /><br /> -DBTYPE_BOOL<br />-DBTYPE_CY<br />-DBTYPE_DATE<br />-DBTYPE_I4<br />-DBTYPE_I8<br />-DBTYPE_R8<br />-DBTYPE_WSTR<br />-N/A|  
|`ISKEY`|`DBTYPE_BOOL`||`True` si la colonne est utilisée comme une clé primaire ou étrangère sinon `false`.|  
|`ISUNIQUE`|`DBTYPE_BOOL`||`True` si les valeurs dans la colonne sont uniques ; sinon `false`.|  
|`ISNULLABLE`|`DBTYPE_BOOL`||`True` si la colonne est nullable ; sinon `false`.|  
|`ISROWNUMBER`|`DBTYPE_BOOL`||`True` si la colonne est une colonne de numéro de ligne. Colonnes de numéro de ligne utilisées en interne par le moteur d'analyse en mémoire xVelocity.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilisation d'ADOMD.NET pour retourner l'ensemble de lignes  
 Lorsque vous utilisez ADOMD.NET et l'ensemble de lignes de schéma pour récupérer des métadonnées, vous pouvez utiliser un GUID ou une chaîne pour référencer un objet d'ensemble de lignes de schéma dans la méthode GetSchemaDataSet. Pour plus d'informations, consultez [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
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
 [Ensembles de lignes de schéma Analysis Services](../analysis-services-schema-rowsets.md)  
  
  
