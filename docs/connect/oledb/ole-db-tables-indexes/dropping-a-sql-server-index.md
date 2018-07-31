---
title: Suppression d’un Index SQL Server | Microsoft Docs
description: Suppression d’un index sql server à l’aide de OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 1fe0c84dd2ca025e84b87d0aaf614347882cc457
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39107741"
---
# <a name="dropping-a-sql-server-index"></a>Suppression d'un index SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server expose la **IIndexDefinition::DropIndex** (fonction). Cela permet aux consommateurs de supprimer un index d’une table [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Le pilote OLE DB pour SQL Server expose certains [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des contraintes PRIMARY KEY et UNIQUE en tant qu’index. Le propriétaire de la table, le propriétaire de la base de données et certains membres munis de rôles d’administration peuvent modifier une table [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en supprimant une contrainte. Par défaut, seul le propriétaire de la table peut supprimer un index existant. Le succès ou l’échec de la fonction **DropIndex** ne dépend pas uniquement des droits d’accès de l’utilisateur de l’application, mais également du type d’index indiqué.  
  
 Les consommateurs spécifient le nom de table en tant que chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pTableID*. Le membre *eKind* de *pTableID* doit être DBKIND_NAME.  
  
 Les consommateurs spécifient le nom d’index comme une chaîne de caractères Unicode dans le membre *pwszName* de l’union *uName* dans le paramètre *pIndexID*. Le membre *eKind* de *pIndexID* doit être DBKIND_NAME. Le pilote OLE DB pour SQL Server ne prend pas en charge la fonctionnalité OLE DB qui permet de supprimer tous les index d’une table lorsque *pIndexID* a la valeur Null. Si *pIndexID* a la valeur Null, E_INVALIDARG est retourné.  
  
## <a name="see-also"></a> Voir aussi  
 [Tables et index](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  
