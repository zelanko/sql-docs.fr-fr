---
title: Mappage de type de données dans ITableDefinition (pilote OLE DB) | Microsoft Docs
description: Découvrez comment un contrôle serveur consommateur OLE DB Driver pour SQL Server peut spécifier des types de données SQL Server lors de la création de tables à l’aide de la méthode ITableDefinition::CreateTable.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- OLE DB Driver for SQL Server, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fecca9ed46ea35fe45868b8c618b3514f0b04abd
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860125"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Mappage de type de données dans ITableDefinition
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Lors de la création de tables avec la fonction **ITableDefinition::CreateTable**, le consommateur du pilote OLE DB pour SQL Server peut spécifier des types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans le membre *pwszTypeName* du tableau DBCOLUMNDESC qui est passé. Si le consommateur spécifie le type de données d’une colonne par nom, le mappage des types de données OLE DB, représenté par le membre *wType* de la structure DBCOLUMNDESC, est ignoré.  
  
 Lors de la spécification de nouveaux types de données de colonne avec des types de données OLE DB avec le membre *wType* de la structure DBCOLUMNDESC, le pilote OLE DB pour SQL Server mappe les types de données OLE DB comme suit.  
  
|Type de données OLE DB|SQL Server<br /><br /> type de données|Informations supplémentaires|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** ou **varbinary(max)**|Le fournisseur OLE DB Driver pour SQL Server inspecte le membre *ulColumnSize* de la structure DBCOLUMNDESC. Selon la valeur et la version de l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le fournisseur OLE DB Driver pour SQL Server mappe le type à **image**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une colonne de type de données **binary**, le pilote OLE DB pour SQL Server inspecte le membre *rgPropertySets* de DBCOLUMNDESC. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le fournisseur OLE DB Driver pour SQL Server mappe le type à **binary**. Si la valeur de la propriété est VARIANT_FALSE, le fournisseur OLE DB Driver pour SQL Server mappe le type à **varbinary**. Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne SQL Server créée.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime2**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_I8|**bigint**||
|DBTYPE_NUMERIC|**numeric**|Le pilote OLE DB pour SQL Server inspecte les membres *bPrecision* et *bScale* de DBCOLUMDESC pour déterminer la précision et l’échelle pour la colonne **numeric**.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **text** ou **varchar(max)**|Le fournisseur OLE DB Driver pour SQL Server inspecte le membre *ulColumnSize* de la structure DBCOLUMNDESC. Selon la valeur et la version de l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le fournisseur OLE DB Driver pour SQL Server mappe le type à **text**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une colonne avec un type de données de caractères multi-octets, le pilote OLE DB pour SQL Server inspecte le membre *rgPropertySets* de DBCOLUMNDESC. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le fournisseur OLE DB Driver pour SQL Server mappe le type à **char**. Si la valeur de la propriété est VARIANT_FALSE, le fournisseur OLE DB Driver pour SQL Server mappe le type à **varchar**. Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] créée.|  
|DBTYPE_UDT|**UDT**|Les informations suivantes sont utilisées dans les structures **DBCOLUMNDESC** par **ITableDefinition::CreateTable** quand des colonnes UDT sont nécessaires :<br /><br /> *pwSzTypeName* est ignoré.<br /><br /> *rgPropertySets* doit inclure une propriété **DBPROPSET_SQLSERVERCOLUMN** définie comme décrit dans la section sur **DBPROPSET_SQLSERVERCOLUMN**, dans [Utilisation de types définis par l’utilisateur](../../oledb/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_VARIANT|**sql_variant**||
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** ou **nvarchar(max)**|Le fournisseur OLE DB Driver pour SQL Server inspecte le membre *ulColumnSize* de la structure DBCOLUMNDESC. Selon la valeur, le fournisseur OLE DB Driver pour SQL Server mappe le type à **ntext**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une colonne avec un type de données de caractères Unicode, le pilote OLE DB pour SQL Server inspecte le membre *rgPropertySets* de DBCOLUMNDESC. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le fournisseur OLE DB Driver pour SQL Server mappe le type à **nchar**. Si la valeur de la propriété est VARIANT_FALSE, le fournisseur OLE DB Driver pour SQL Server mappe le type à **nvarchar**. Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] créée.|  
|DBTYPE_XML|**XML**||  

> [!NOTE]  
>  Lors de la création d’une table, le pilote OLE DB pour SQL Server mappe seulement les valeurs d’énumération des types de données OLE DB spécifiées dans le tableau précédent. Toute tentative de création d'une table avec une colonne de tout autre type de données OLE DB génère une erreur.  

## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
