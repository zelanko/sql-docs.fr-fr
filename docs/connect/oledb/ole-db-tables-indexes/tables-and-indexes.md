---
title: Tables et index | Microsoft Docs
description: Création, modification et suppression de tables et d’index à l’aide d’OLE DB pilote pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- OLE DB Driver for SQL Server, tables
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 0fc8aeed348f64c17894fa3432a7a81274ffbea4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015239"
---
# <a name="tables-and-indexes"></a>Tables et index
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server expose les interfaces **IIndexDefinition** et **ITableDefinition**, ce qui permet aux consommateurs de créer, de modifier et de supprimer des tables et des index [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les définitions de table et d'index valides dépendent de la version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 La possibilité de créer ou de supprimer des tables et des index dépend des droits d'accès [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de l'utilisateur de l'application consommateur. La suppression d'une table peut être également limitée par la présence de contraintes d'intégrité référentielle déclarative ou d'autres facteurs.  
  
 La plupart des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applications ciblant utilisent SQL-DMO au lieu de ces OLE DB pilote pour les interfaces SQL Server. SQL-DMO est une collection d'objets OLE Automation qui prennent en charge toutes les fonctions d'administration de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les applications ciblant plusieurs fournisseurs OLE DB utilisent ces interfaces OLE DB génériques qui sont prises en charge par les différents fournisseurs OLE DB.  
  
 Dans le jeu de propriétés spécifique au fournisseur DBPROPSET_SQLSERVERCOLUMN, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] définit la propriété suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|Type : VT_BSTR<br /><br /> L/E (Lecture/Écriture) : écriture<br /><br /> Valeur par défaut : Null<br /><br /> Description : cette propriété est utilisée uniquement dans **ITableDefinition**. La chaîne spécifiée dans cette propriété est utilisée lors de la création d’une instruction [CREATE TABLE](../../../t-sql/statements/create-table-transact-sql.md).<br /><br /> .|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création de tables SQL Server](../../oledb/ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [Ajout d’une colonne à une table SQL Server](../../oledb/ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [Suppression d’une colonne d’une table SQL Server](../../oledb/ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [Suppression d’une table SQL Server](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [Création d’index SQL Server](../../oledb/ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [Suppression d’un index SQL Server](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation du pilote OLE DB pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
