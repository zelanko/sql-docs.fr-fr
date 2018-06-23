---
title: Mappage de Type de données dans ITableDefinition | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c09ac0e561f06236a9580ae7a84ed892ca1fcd31
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044937"
---
# <a name="data-type-mapping-in-itabledefinition"></a>Mappage de type de données dans ITableDefinition
  Lors de la création de tables à l’aide de la **ITableDefinition::CreateTable** (fonction), la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client peut spécifier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types de données dans le *pwszTypeName* membre du tableau DBCOLUMNDESC passé. Si le consommateur Spécifie le type de données d’une colonne par son nom, mappage, représenté par de type de données OLE DB le *wType* membre de la structure DBCOLUMNDESC, est ignoré.  
  
 Lorsque vous spécifiez des nouveaux types de données de colonne avec les types de données OLE DB à l’aide de la structure DBCOLUMNDESC *wType* membre, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif mappe les types de données OLE DB comme suit.  
  
|Type de données OLE DB|SQL Server<br /><br /> type de données|Autres informations|  
|----------------------|------------------------------|----------------------------|  
|DBTYPE_BOOL|**bit**||  
|DBTYPE_BYTES|**binaire**, **varbinary**, **image,** ou **varbinary (max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte le *ulColumnSize* membre de la structure DBCOLUMNDESC. En fonction de la valeur et la version de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **image**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’un **binaire** colonne de type de données, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte la structure DBCOLUMNDESC  *rgPropertySets* membre. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **binaire**. Si la valeur de la propriété est VARIANT_FALSE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **varbinary**. Dans les deux cas, la structure DBCOLUMNDESC *ulColumnSize* détermine la largeur de la colonne SQL Server créée.|  
|DBTYPE_CY|**money**||  
|DBTYPE_DBTIMESTAMP|**datetime**||  
|DBTYPE_GUID|**uniqueidentifier**||  
|DBTYPE_I2|**smallint**||  
|DBTYPE_I4|**Int**||  
|DBTYPE_NUMERIC|**numeric**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte les membres *bPrecision* et *bScale* membres pour déterminer la précision et l’échelle pour le **numérique** colonne.|  
|DBTYPE_R4|**real**||  
|DBTYPE_R8|**float**||  
|DBTYPE_STR|**char**, **varchar**, **texte,** ou **varchar (max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte le *ulColumnSize* membre de la structure DBCOLUMNDESC. En fonction de la valeur et la version de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **texte**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une colonne de type de données de caractères multioctets, puis le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte la DBCOLUMNDESC *rgPropertySets*membre. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **char**. Si la valeur de la propriété est VARIANT_FALSE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **varchar**. Dans les deux cas, la structure DBCOLUMNDESC *ulColumnSize* détermine la largeur de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonne créée.|  
|DBTYPE_UDT|**UDT**|Les informations suivantes sont utilisées dans `DBCOLUMNDESC` par les structures **ITableDefinition::CreateTable** lorsque les colonnes UDT sont requises :<br /><br /> -   *pwSzTypeName* est ignoré.<br />-   *rgPropertySets* doit inclure un `DBPROPSET_SQLSERVERCOLUMN` propriété est définie comme décrit dans la section sur `DBPROPSET_SQLSERVERCOLUMN`, dans [Defined Types](../native-client/features/using-user-defined-types.md).|  
|DBTYPE_UI1|**tinyint**||  
|DBTYPE_WSTR|**NCHAR**, **nvarchar**, **ntext,** ou **nvarchar (max)**|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte le *ulColumnSize* membre de la structure DBCOLUMNDESC. Selon la valeur, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **ntext**.<br /><br /> Si la valeur de *ulColumnSize* est inférieure à la longueur maximale d’une colonne de type données de caractères Unicode, puis le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client inspecte la DBCOLUMNDESC *rgPropertySets*membre. Si DBPROP_COL_FIXEDLENGTH est VARIANT_TRUE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **nchar**. Si la valeur de la propriété est VARIANT_FALSE, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client mappe le type à **nvarchar**. Dans les deux cas, la structure DBCOLUMNDESC *ulColumnSize* détermine la largeur de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonne créée.|  
|DBTYPE_XML|**XML**||  
  
> [!NOTE]  
>  Lors de la création d'une table, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client mappe uniquement les valeurs d'énumération de type de données OLE DB spécifiées dans le tableau précédent. Toute tentative de création d'une table avec une colonne de tout autre type de données OLE DB génère une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  