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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bdf3a1e716fd1de5354b735e353916bab863059c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73774303"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Mappage de type de données dans ITableDefinition
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Lors de la création de tables à l’aide de la fonction **ITableDefinition :: CreateTable** , le consommateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client peut spécifier des types de données dans le membre *pwszTypeName* du tableau DBCOLUMNDESC qui est passé. Si le consommateur spécifie le type de données d’une colonne par nom, le mappage des types de données OLE DB, représenté par le membre *wType* de la structure DBCOLUMNDESC, est ignoré.  
  
 Lorsque vous spécifiez de nouveaux types de données de colonne avec OLE DB des ** types de données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’aide du membre WTYPE de la structure DBCOLUMNDESC, le fournisseur Native Client OLE DB mappe OLE DB types de données comme suit.  
  
|Type de données OLE DB|SQL Server<br /><br /> type de données|Informations supplémentaires|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**Binary**, **varbinary**, **image** ou **varbinary (max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte le membre *ulColumnSize* de la structure DBCOLUMNDESC. En fonction de la valeur et de la version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , le fournisseur de OLE DB Native Client mappe le type à **image**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une colonne de type de données **Binary** , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fournisseur de OLE DB Native Client inspecte le membre *rgPropertySets* DBCOLUMNDESC. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **Binary**. Si la valeur de la propriété est VARIANT_FALSE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB mappe le type à **varbinary**. Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne SQL Server créée.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**DATETIME**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**int**||  
|DBTYPE_NUMERIC|**chiffre**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte les membres DBCOLUMDESC *bPrecision* et *bScale* pour déterminer la précision et l’échelle de la colonne **numérique** .|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **Text** ou **varchar (max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte le membre *ulColumnSize* de la structure DBCOLUMNDESC. En fonction de la valeur et de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, le fournisseur de OLE DB Native Client mappe le type à du **texte**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une colonne de type de données caractère multioctet, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fournisseur de OLE DB Native Client inspecte le membre *rgPropertySets* DBCOLUMNDESC. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **char**. Si la valeur de la propriété est VARIANT_FALSE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB mappe le type à **varchar**. Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée.|  
|DBTYPE_UDT|**UDT**|Les informations suivantes sont utilisées dans les structures **DBCOLUMNDESC** par **ITableDefinition::CreateTable** quand des colonnes UDT sont nécessaires :<br /><br /> *pwSzTypeName* est ignoré.<br /><br /> *rgPropertySets* doit inclure un jeu de propriétés **DBPROPSET_SQLSERVERCOLUMN** comme décrit dans la section sur **DBPROPSET_SQLSERVERCOLUMN**, en [utilisant des types définis par l’utilisateur](../../relational-databases/native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** ou **nvarchar (max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte le membre *ulColumnSize* de la structure DBCOLUMNDESC. En fonction de la valeur, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fournisseur de OLE DB Native Client mappe le type à **ntext**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une colonne de type de données caractère Unicode, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fournisseur de OLE DB Native Client inspecte le membre *rgPropertySets* DBCOLUMNDESC. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **nchar**. Si la valeur de la propriété est VARIANT_FALSE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client OLE DB mappe le type à **nvarchar**. Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  Lors de la création d'une table, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client mappe uniquement les valeurs d'énumération de type de données OLE DB spécifiées dans le tableau précédent. Toute tentative de création d'une table avec une colonne de tout autre type de données OLE DB génère une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
