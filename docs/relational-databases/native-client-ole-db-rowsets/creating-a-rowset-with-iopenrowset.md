---
description: Créer un ensemble de lignes avec IOpenRowset (Native Client OLE DB Provider)
title: Créer un ensemble de lignes avec IOpenRowset (Native Client OLE DB Provider) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1f3fa6d0b98d46057ccea24dd37854432c21f4fb
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97463440"
---
# <a name="creating-a-rowset-with-iopenrowset-in-sql-server-native-client"></a>Création d’un ensemble de lignes avec IOpenRowset dans SQL Server Native Client
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client prend en charge la méthode **IOpenRowset :: OpenRowset** avec les restrictions suivantes :  
  
-   Une vue ou une table de base doit être spécifiée dans une structure d’ID de base de données (DBID) vers laquelle pointe le paramètre *pTableID*.  
  
-   Le membre *eKind* DBID doit indiquer DBKIND_NAME.  
  
-   Le membre *uName* DBID doit spécifier le nom d’une vue ou d’une table de base existante sous forme de chaîne de caractères Unicode.  
  
-   Le paramètre *pIndexID* de **OpenRowset** doit être Null.  
  
 Le jeu de résultats de **IOpenRowset::OpenRowset** contient un seul ensemble de lignes. Les jeux de résultats qui contiennent un seul ensemble de lignes peuvent être pris en charge par les curseurs [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La prise en charge des curseurs permet au développeur d'utiliser les mécanismes d'accès concurrentiel de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
