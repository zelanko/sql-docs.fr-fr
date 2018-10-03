---
title: Tables et index | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4f0b3fcf58f3f2767fbdc653327bec334545bdd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072709"
---
# <a name="tables-and-indexes"></a>Tables et index
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose la **IIndexDefinition** et **ITableDefinition** interfaces, ce qui permet aux consommateurs de créer, modifier et supprimer des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables et index. Les définitions de table et d'index valides dépendent de la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La possibilité de créer ou de supprimer des tables et des index dépend des droits d'accès [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l'utilisateur de l'application consommateur. La suppression d'une table peut être également limitée par la présence de contraintes d'intégrité référentielle déclarative ou d'autres facteurs.  
  
 La plupart des applications qui ciblent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent SQL-DMO au lieu de ces [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interfaces du fournisseur OLE DB Native Client. SQL-DMO est une collection d'objets OLE Automation qui prennent en charge toutes les fonctions d'administration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les applications ciblant plusieurs fournisseurs OLE DB utilisent ces interfaces OLE DB génériques qui sont prises en charge par les différents fournisseurs OLE DB.  
  
 Dans le jeu de propriétés spécifique au fournisseur DBPROPSET_SQLSERVERCOLUMN, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définit la propriété suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|Type : VT_BSTR<br /><br /> L/E (Lecture/Écriture) : écriture<br /><br /> Valeur par défaut : Null<br /><br /> Description : cette propriété est utilisée uniquement dans **ITableDefinition**. La chaîne spécifiée dans cette propriété est utilisée lors de la création d’une instruction [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql).<br /><br /> .|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Création de tables SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [Ajout d’une colonne à une table SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [Suppression d’une colonne d’une table SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [Suppression d’une table SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [Création d’index SQL Server](../../relational-databases/indexes/indexes.md)  
  
-   [Suppression d’un index SQL Server](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)   
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
