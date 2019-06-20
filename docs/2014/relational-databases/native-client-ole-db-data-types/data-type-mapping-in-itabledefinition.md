---
title: Mappage de Type de données dans ITableDefinition | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: e561742406c173b69bfb5040c2f2f51efdf5ed64
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63201217"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Mappage de type de données dans ITableDefinition
  Lors de la création de tables à l’aide de la **ITableDefinition::CreateTable** (fonction), le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client peut spécifier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des types de données dans le *pwszTypeName* membre du tableau DBCOLUMNDESC passé. Si le consommateur spécifie le type de données d’une colonne par nom, le mappage des types de données OLE DB, représenté par le membre *wType* de la structure DBCOLUMNDESC, est ignoré.  
  
 Lorsque vous spécifiez des nouveaux types de données de colonne avec les types de données OLE DB à l’aide de la structure DBCOLUMNDESC *wType* membre, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe les types de données OLE DB comme suit.  
  
|Type de données OLE DB|SQL Server<br /><br /> type de données|Autres informations|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binary**, **varbinary**, **image** ou **varbinary(max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte le *ulColumnSize* membre de la structure DBCOLUMNDESC. Selon la valeur et la version de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **image**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une **binaire** colonne de type de données, puis le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte la DBCOLUMNDESC  *rgPropertySets* membre. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **binaire**. Si la valeur de la propriété est VARIANT_FALSE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **varbinary**. Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne SQL Server créée.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**Int**||  
|DBTYPE_NUMERIC|**numeric**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte les membres *bPrecision* et *bScale* membres pour déterminer la précision et l’échelle pour le **numérique** colonne.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **text** ou **varchar(max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte le *ulColumnSize* membre de la structure DBCOLUMNDESC. Selon la valeur et la version de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **texte**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une colonne de type de données de caractères multioctets, puis le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte la DBCOLUMNDESC *rgPropertySets*membre. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **char**. Si la valeur de la propriété est VARIANT_FALSE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **varchar**. Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée.|  
|DBTYPE_UDT|**UDT**|Les informations suivantes sont utilisées dans `DBCOLUMNDESC` structures par **ITableDefinition::CreateTable** lorsque les colonnes UDT sont requises :<br /><br /> -   *pwSzTypeName* est ignoré.<br />-   *rgPropertySets* doit inclure un `DBPROPSET_SQLSERVERCOLUMN` propriété est définie comme décrit dans la section sur `DBPROPSET_SQLSERVERCOLUMN`, dans [Defined Types](../native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**nchar**, **nvarchar**, **ntext** ou **nvarchar(max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte le *ulColumnSize* membre de la structure DBCOLUMNDESC. Selon la valeur, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **ntext**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une colonne de type données de caractères Unicode, puis le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte la DBCOLUMNDESC *rgPropertySets*membre. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **nchar**. Si la valeur de la propriété est VARIANT_FALSE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **nvarchar**. Dans les deux cas, le membre *ulColumnSize* de DBCOLUMNDESC détermine la largeur de la colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] créée.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  Lors de la création d'une table, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client mappe uniquement les valeurs d'énumération de type de données OLE DB spécifiées dans le tableau précédent. Toute tentative de création d'une table avec une colonne de tout autre type de données OLE DB génère une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  
