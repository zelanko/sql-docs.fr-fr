---
title: Création d’un ensemble de lignes avec IOpenRowset | Microsoft Docs
description: Création d’un ensemble de lignes avec IOpenRowset, interface de pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 1450bac50120d81c4bf8e2ac3ae96ab85eb9b5b6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728473"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Création d'un ensemble de lignes avec IOpenRowset
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server prend en charge la **IOpenRowset::OpenRowset** méthode avec les restrictions suivantes :  
  
-   Une vue ou une table de base doit être spécifiée dans une structure d’ID de base de données (DBID) vers laquelle pointe le paramètre *pTableID*.  
  
-   Le membre *eKind* DBID doit indiquer DBKIND_NAME.  
  
-   Le membre *uName* DBID doit spécifier le nom d’une vue ou d’une table de base existante sous forme de chaîne de caractères Unicode.  
  
-   Le paramètre *pIndexID* de **OpenRowset** doit être Null.  
  
 Le jeu de résultats de **IOpenRowset::OpenRowset** contient un seul ensemble de lignes. Les jeux de résultats qui contiennent un seul ensemble de lignes peuvent être pris en charge par les curseurs [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La prise en charge des curseurs permet au développeur d'utiliser les mécanismes d'accès concurrentiel de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a> Voir aussi  
 [Ensembles de lignes](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
