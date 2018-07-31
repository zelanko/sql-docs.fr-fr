---
title: Mappage de Type de données dans les ensembles de lignes et des paramètres | Microsoft Docs
description: Mappage de types de données dans les ensembles de lignes et les paramètres
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-types
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- DBTYPE_SQLVARIANT data type
- OLE DB Driver for SQL Server, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: c9c6d56cdbbbcd9b35b09f405154497a5fa3bc8f
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39108791"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>Mappage de type de données dans les ensembles de lignes et les paramètres
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dans les ensembles de lignes et en tant que valeurs de paramètre, le pilote OLE DB pour SQL Server représente les données de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en utilisant les types de données OLE DB définis suivants, indiqués dans les fonctions **IColumnsInfo::GetColumnInfo** et **ICommandWithParameters::GetParameterInfo**.  
  
|Type de données SQL Server|Type de données OLE DB|  
|--------------------------|----------------------|  
|**bigint**|DBTYPE_I8|  
|**binaire**|DBTYPE_BYTES|  
|**bit**|DBTYPE_BOOL|  
|**char**|DBTYPE_STR|  
|**datetime**|DBTYPE_DBTIMESTAMP|  
|**datetime2**|DBTYPE_DBTIME2|  
|**decimal**|DBTYPE_NUMERIC|  
|**float**|DBTYPE_R8|  
|**image**|DBTYPE_BYTES|  
|**Int**|DBTYPE_I4|  
|**money**|DBTYPE_CY|  
|**nchar**|DBTYPE_WSTR|  
|**ntext**|DBTYPE_WSTR|  
|**numeric**|DBTYPE_NUMERIC|  
|**nvarchar**|DBTYPE_WSTR|  
|**real**|DBTYPE_R4|  
|**smalldatetime**|DBTYPE_DBTIMESTAMP|  
|**smallint**|DBTYPE_I2|  
|**smallmoney**|DBTYPE_CY|  
|**sql_variant**|DBTYPE_VARIANT, DBTYPE_SQLVARIANT|  
|**sysname**|DBTYPE_WSTR|  
|**texte**|DBTYPE_STR|  
|**timestamp**|DBTYPE_BYTES|  
|**tinyint**|DBTYPE_UI1|  
|**UDT**|DBTYPE_UDT|  
|**uniqueidentifier**|DBTYPE_GUID|  
|**varbinary**|DBTYPE_BYTES|  
|**varchar**|DBTYPE_STR|  
|**XML**|DBTYPE_XML|  
  
 Le pilote OLE DB pour SQL Server prend en charge les conversions demandées par le consommateur de données comme indiqué dans l’illustration.  
  
 Les objets **sql_variant** peuvent contenir des données de n’importe quel type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], sauf text, ntext, image, varchar(max), nvarchar(max), varbinary(max), xml, timestamp et les types CLR (Common Language Runtime) du Microsoft .NET Framework définis par l’utilisateur. sql_variant ne peut pas être le type de données de base sous-jacent d'une instance de données sql_variant. Par exemple, la colonne peut contenir des valeurs **smallint** pour certaines lignes, des valeurs **float** pour d’autres lignes et des valeurs **char**/**nchar** dans le reste.  
  
> [!NOTE]  
>  Le type de données **sql_variant** est similaire au type de données Variant dans Microsoft Visual Basic® et à DBTYPE_VARIANT, DBTYPE_SQLVARIANT dans OLE DB.  
  
 Quand des données **sql_variant** sont extraites en tant que DBTYPE_VARIANT, elles sont placées dans une structure VARIANT dans la mémoire tampon. Cependant, les sous-types dans la structure VARIANT peuvent ne pas être mappés aux sous-types définis dans le type de données **sql_variant**. Les données **sql_variant** doivent ensuite être extraites en tant que DBTYPE_SQLVARIANT pour que tous les sous-types correspondent.  
  
## <a name="dbtypesqlvariant-data-type"></a>Type de données DBTYPE_SQLVARIANT  
 Pour prendre en charge le type de données **sql_variant**, le pilote OLE DB pour SQL Server expose un type de données spécifique au fournisseur appelé DBTYPE_SQLVARIANT. Quand des données **sql_variant** sont extraites en tant que DBTYPE_SQLVARIANT, elles sont stockées dans une structure SSVARIANT spécifique au fournisseur. La structure SSVARIANT contient tous les sous-types qui correspondent aux sous-types du type de données **sql_variant**.  
  
 La propriété de session SSPROP_ALLOWNATIVEVARIANT doit également avoir la valeur TRUE.  
  
## <a name="provider-specific-property-sspropallownativevariant"></a>Propriété SSPROP_ALLOWNATIVEVARIANT spécifique au fournisseur  
 Pour extraire des données, vous pouvez spécifier explicitement le type de données à retourner pour une colonne ou un paramètre. **IColumnsInfo** permet également d’obtenir les informations sur les colonnes et d’utiliser ces informations pour effectuer la liaison. Quand **IColumnsInfo** est utilisé pour obtenir des informations sur les colonnes en vue d’effectuer une liaison, si la propriété de session SSPROP_ALLOWNATIVEVARIANT a la valeur FALSE (valeur par défaut), DBTYPE_VARIANT est retourné pour les colonnes **sql_variant**. Si la propriété SSPROP_ALLOWNATIVEVARIANT a la valeur FALSE, DBTYPE_SQLVARIANT n'est pas pris en charge. Si la propriété SSPROP_ALLOWNATIVEVARIANT a la valeur TRUE, le type de colonne est retourné en tant que DBTYPE_SQLVARIANT, auquel cas la mémoire tampon contiendra la structure SSVARIANT. Pour extraire des données **sql_variant** en tant que DBTYPE_SQLVARIANT, la propriété de session SSPROP_ALLOWNATIVEVARIANT doit être définie sur TRUE.  
  
 La propriété SSPROP_ALLOWNATIVEVARIANT est une propriété de session et fait partie du jeu de propriétés DBPROPSET_SQLSERVERSESSION spécifique au fournisseur.  
  
 DBTYPE_VARIANT s'applique à tous les autres fournisseurs OLE DB.  
  
## <a name="sspropallownativevariant"></a>SSPROP_ALLOWNATIVEVARIANT  
 SSPROP_ALLOWNATIVEVARIANT est une propriété de session et fait partie du jeu de propriétés DBPROPSET_SQLSERVERSESSION.  
  
|||  
|-|-|  
|SSPROP_ALLOWNATIVEVARIANT|Type : VT_BOOL<br /><br /> Lecture/écriture : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : détermine si les données sont extraites en tant que DBTYPE_VARIANT ou DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE : le type de colonne est retourné en tant que DBTYPE_SQLVARIANT, auquel cas la mémoire tampon contient la structure SSVARIANT.<br /><br /> VARIANT_FALSE : le type de colonne est retourné en tant que DBTYPE_VARIANT et la mémoire tampon a la structure VARIANT.|  
  
## <a name="see-also"></a> Voir aussi  
 [Types de données &#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  
