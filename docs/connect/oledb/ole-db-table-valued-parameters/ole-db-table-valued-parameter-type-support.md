---
title: Support des types de paramètre table (pilote OLE DB)
description: Prise en charge des types de paramètre table OLE DB
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 453609d2d5633b6270ab565a2da50a98c909e86a
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87244136"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>Prise en charge du type de paramètre table OLE DB
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cet article décrit la prise en charge du type OLE DB pour les paramètres table.  
  
## <a name="table-valued-parameter-rowset-object"></a>Objet d'ensemble de lignes de paramètre table  
 Vous pouvez créer un objet d'ensemble de lignes spécialisé pour des paramètres table. Vous créez l’objet d’ensemble de lignes de paramètre table à l’aide de ITableDefinitionWithConstraints::CreateTableWithConstraints ou IOpenRowset::OpenRowset. Pour ce faire, définissez le membre *eKind* du paramètre *pTableID* sur DBKIND_GUID_NAME, et fournissez CLSID_ROWSET_INMEMORY comme membre *guid*. Le nom de type de serveur pour le paramètre table doit être spécifié dans le membre *pwszName* de *pTableID* lors de l’utilisation de IOpenRowset::OpenRowset. L'objet d'ensemble de lignes de paramètre table se comporte comme un objet OLE DB Driver pour SQL Server normal.  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtype_table"></a>DBTYPE_TABLE  
 DBTYPE_TABLE est un nouveau type qui représente un type de table. Ce type spécifie des paramètres table dans différentes interfaces OLE DB où un DBTYPE est requis.  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 DBTYPE_TABLE a le même format que DBTYPE_IUNKNOWN. Il s’agit d’un pointeur vers un objet du tampon de données. Pour une spécification complète dans les liaisons, le consommateur remplit la mémoire tampon DBOBJECT, avec *iid* défini sur l’une des interfaces d’objet d’ensemble de lignes (IID_IRowset). Si aucun DBOBJECT n’est spécifié dans les liaisons, IID_IRowset est supposé.  
  
 Les conversions vers et à partir de DBTYPE_TABLE pour tout autre type ne sont pas prises en charge. IConvertType::CanConvert retourne S_FALSE pour les conversions non prises en charge, pour toute demande autre qu’une conversion DBTYPE_TABLE en DBTYPE_TABLE. Cela suppose DBCONVERTFLAGS_PARAMETER sur l’objet Command.  
  
## <a name="methods"></a>Méthodes  
 Pour plus d’informations sur les méthodes de OLE DB qui prennent en charge les paramètres table, consultez [Prise en charge des types de paramètre table OLE DB &#40;Méthodes&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md).  
  
## <a name="properties"></a>Propriétés  
 Pour plus d’informations sur les propriétés de OLE DB qui prennent en charge les paramètres table, consultez [Prise en charge des types de paramètre table OLE DB &#40;Propriétés&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
