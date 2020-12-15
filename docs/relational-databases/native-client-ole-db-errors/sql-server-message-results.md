---
description: SQL Server Native Client les résultats du message
title: SQL Server les résultats des messages (fournisseur Native Client OLE DB)
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7fe5f2711334f371831bc76d60b5b74ef6b9a417
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97467630"
---
# <a name="sql-server-native-client-message-results"></a>SQL Server Native Client les résultats du message
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Les [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions suivantes ne génèrent pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB les ensembles de lignes de fournisseur ou un nombre de lignes affectées lors de l’exécution :  
  
-   PRINT  
  
-   RAISERROR avec une gravité égale ou inférieure à 10  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Ces instructions retournent un ou plusieurs messages d'information ou entraînent le renvoi par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de messages d'information au lieu de résultats sous forme d'ensemble de lignes ou de nombre. En cas de réussite de l’exécution, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne S_OK et les messages sont disponibles pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client retourne S_OK et un ou plusieurs messages d’information sont disponibles à la suite de l’exécution de nombreuses [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions ou de l’exécution du consommateur d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonction membre du fournisseur OLE DB Native Client.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client qui autorise la spécification dynamique du texte de la requête doit vérifier les interfaces d’erreur après chaque exécution de fonction membre, quelle que soit la valeur du code de retour, la présence ou l’absence d’une référence d’interface **IRowset** ou **IMultipleResults** retournée, ou un nombre de lignes affectées.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../relational-databases/native-client-ole-db-errors/errors.md)  
  
  
