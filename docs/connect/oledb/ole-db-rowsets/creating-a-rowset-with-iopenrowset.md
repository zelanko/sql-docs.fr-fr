---
title: Création d’un ensemble de lignes avec IOpenRowset | Microsoft Docs
description: Création d’un ensemble de lignes avec IOpenRowset, interface de pilote OLE DB pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 08ed7ed1d56ccd5ef6887387ea9ba53eed2c5df9
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032079"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Création d'un ensemble de lignes avec IOpenRowset
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server prend en charge la **IOpenRowset::OpenRowset** méthode avec les restrictions suivantes :  
  
-   Une table de base ou une vue doit être spécifiée dans une structure d'ID de base de données (DBID) vers laquelle pointe le paramètre pTableID *.  
  
-   Le membre eKind* de la structure DBID doit indiquer DBKIND_NAME.  
  
-   Le membre uName* de la structure DBID doit spécifier le nom d'une table de base ou d'une vue existante sous forme de chaîne de caractères Unicode.  
  
-   Le paramètre pIndexID *de OpenRowset* doit être NULL.  
  
 Le jeu de résultats de IOpenRowset::OpenRowset** contient un ensemble de lignes unique. Les jeux de résultats qui contiennent un ensemble de lignes unique peuvent être pris en charge par les curseurs [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La prise en charge des curseurs permet au développeur d'utiliser les mécanismes d'accès concurrentiel de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a> Voir aussi  
 [Ensembles de lignes](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
