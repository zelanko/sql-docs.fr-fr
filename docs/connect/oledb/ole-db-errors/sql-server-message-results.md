---
title: Résultats des messages SQL Server (OLE DB pilote)
description: Découvrez les instructions Transact-SQL qui ne génèrent pas ou peu d’ensembles de lignes OLE DB Driver pour SQL Server et les valeurs de retour attendues.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dc3701313f920eead650435ca40538ad8a4b6ef0
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862505"
---
# <a name="sql-server-message-results"></a>Résultats des messages SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Les instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] suivantes ne génèrent pas ou peu d’ensembles de lignes OLE DB Driver pour SQL Server de lignes affectées lors de l’exécution :  
  
-   PRINT  
  
-   RAISERROR avec une gravité égale ou inférieure à 10  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Ces instructions retournent un ou plusieurs messages d'information ou entraînent le renvoi par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de messages d'information au lieu de résultats sous forme d'ensemble de lignes ou de nombre. En cas d'exécution réussie, OLE DB Driver pour SQL Server renvoie S_OK, et les messages sont disponibles pour le consommateur OLE DB Driver pour SQL Server.  
  
 OLE DB Driver pour SQL Server retourne S_OK et possède un ou plusieurs messages d'information disponibles après l'exécution de plusieurs instructions [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou après l'exécution par le consommateur d'une fonction membre OLE DB Driver pour SQL Server.  
  
Le contrôle serveur consommateur OLE DB Driver pour SQL Server est autorisé à spécifier dynamiquement le texte de la requête. Le contrôle serveur consommateur doit vérifier les interfaces d’erreur après _chaque_ exécution de la fonction membre. Il doit toujours effectuer ces vérifications, quelle que soit la valeur du code de retour, indiquant si une référence d’interface à un `IRowset` ou `IMultipleResults` est retournée, quel que soit le nombre de lignes affectées.
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](../../oledb/ole-db-errors/errors.md)  
  
  
