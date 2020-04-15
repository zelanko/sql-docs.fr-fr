---
title: Mappage de type de données dans ITableDefinition | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- SQL Server Native Client OLE DB provider, data types
- ITableDefinition interface
- DBCOLUMNDESC structure
- data types [OLE DB]
- CreateTable function
- OLE DB, data types
ms.assetid: 13292d1f-c17e-4d11-bf98-3460a10cbb18
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d3e828efa513db1ace272e59379f77d063220290
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297027"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Mappage de type de données dans ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Lors de la création de tableaux en utilisant la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonction **ITableDefinition::CreateTable,** le consommateur fournisseur de fournisseur native Client OLE DB peut spécifier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les types de données dans le membre *pwszTypeName* du tableau DBCOLUMNDESC qui est passé. Si le consommateur spécifie le type de données d’une colonne par nom, le mappage des types de données OLE DB, représenté par le membre *wType* de la structure DBCOLUMNDESC, est ignoré.  
  
 Lorsque vous spécifiez de nouveaux types de données de colonne avec des types [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données OLE DB à l’aide du membre *wType* de la structure DBCOLUMNDESC, le fournisseur de DB OLE de client autochtone cartographie les types de données OLE DB comme suit.  
  
|Type de données OLE DB|SQL Server<br /><br /> type de données|Informations supplémentaires|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** ou **varbinary(max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client inspecte le membre *ulColumnSize* de la structure DBCOLUMNDESC. Basé sur la valeur, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version de l’instance, le fournisseur native De DB OLE client cartographie le type à **l’image**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] maximale d’une colonne de type de données **binaires,** alors le fournisseur de DB OLE native De client inspecte le membre DBCOLUMNDESC *rgPropertySets.* Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB cartographie le type à **binaire**. Si la valeur de la propriété est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VARIANT_FALSE, le fournisseur de DB OLE de client autochtone cartographie le type au **varbinaire.** Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne SQL Server créée.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**UNIQUEIDENTIFIER**||  
|DBTYPE_I2|**SMALLINT**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**Numérique**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client inspecte les membres DBCOLUMDESC *bPrecision* et *bScale* pour déterminer la précision et l’échelle de la colonne **numérique.**|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**Flotteur**||  
|DBTYPE_STR|**char**, **varchar**, **text** ou **varchar(max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client inspecte le membre *ulColumnSize* de la structure DBCOLUMNDESC. Basé sur la valeur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version de l’instance, le fournisseur native OLE DB carte le type de **texte**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une colonne de type de caractère multioctet, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native OLE DB inspecte le membre DBCOLUMNDESC *rgPropertySets.* Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone cartographie le type à **char**. Si la valeur de la propriété est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VARIANT_FALSE, le fournisseur de DB OLE de client autochtone cartographie le type à **varchar.** Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée.|  
|DBTYPE_UDT|**Udt**|Les informations suivantes sont utilisées dans les structures **DBCOLUMNDESC** par **ITableDefinition::CreateTable** quand des colonnes UDT sont nécessaires :<br /><br /> *pwSzTypeName* est ignoré.<br /><br /> *rgPropertySets* doit inclure une propriété **DBPROPSET_SQLSERVERCOLUMN** définie comme décrit dans la section sur **DBPROPSET_SQLSERVERCOLUMN**, dans [Utilisation de types définis par l’utilisateur](../../relational-databases/native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**TINYINT**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** ou **nvarchar(max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client inspecte le membre *ulColumnSize* de la structure DBCOLUMNDESC. Basé sur la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valeur, le fournisseur native De DB OLE de client cartographie le type à **ntext**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’une colonne de données de caractère Unicode, le fournisseur native OLE DB inspecte le membre DBCOLUMNDESC *rgPropertySets.* Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client cartographie le type à **nchar**. Si la valeur de la propriété est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] VARIANT_FALSE, le fournisseur de DB OLE de client autochtone cartographie le type à **nvarchar**. Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée.|  
|DBTYPE_XML|**Xml**||  
  
> [!NOTE]  
>  Lors de la création d'une table, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client mappe uniquement les valeurs d'énumération de type de données OLE DB spécifiées dans le tableau précédent. Toute tentative de création d'une table avec une colonne de tout autre type de données OLE DB génère une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
