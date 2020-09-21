---
title: Créer un ensemble de lignes avec IOpenRowset (pilote OLE DB) | Microsoft Docs
description: Découvrez comment OLE DB Driver pour SQL Server prend en charge la méthode IOpenRowset::OpenRowset pour retourner un ensemble de lignes avec les restrictions relatives à son utilisation.
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a39ff5a60f13a25c271be61d4db20a604364420
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862259"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Création d'un ensemble de lignes avec IOpenRowset
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server prend en charge la méthode **IOpenRowset::OpenRowset** avec les restrictions suivantes :  
  
-   Une vue ou une table de base doit être spécifiée dans une structure d’ID de base de données (DBID) vers laquelle pointe le paramètre *pTableID*.  
  
-   Le membre *eKind* DBID doit indiquer DBKIND_NAME.  
  
-   Le membre *uName* DBID doit spécifier le nom d’une vue ou d’une table de base existante sous forme de chaîne de caractères Unicode.  
  
-   Le paramètre *pIndexID* de **OpenRowset** doit être Null.  
  
 Le jeu de résultats de **IOpenRowset::OpenRowset** contient un seul ensemble de lignes. Les jeux de résultats qui contiennent un seul ensemble de lignes peuvent être pris en charge par les curseurs [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La prise en charge des curseurs permet au développeur d'utiliser les mécanismes d'accès concurrentiel de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
