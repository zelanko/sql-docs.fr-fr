---
title: SQL Server Native Client (ODBC) | Documents Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|ODBC
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, ODBC
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], ODBC
- SQL Server Native Client ODBC driver
- ODBC
- SQL Server Native Client, ODBC
- ODBC, about SQL Server Native Client ODBC driver
ms.assetid: 811d5ba3-a2b8-48c0-adbc-8c91f041f458
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0b17b4b7255a63b3c3d1b5f17f89df8d3cfcf009
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="sql-server-native-client-odbc"></a>SQL Server Native Client (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ODBC est la définition standard d'une interface de programmation d'applications (API) utilisée pour accéder aux données des bases de données relationnelles ou à accès séquentiel indexé (Indexed Sequential Access Method). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge ODBC, via le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, comme l'une des API natives pour écrire des applications C et C++ qui communiquent avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Les programmes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] écrits à l'aide du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client communiquent avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] via les appels de fonctions C. Les versions propres à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des fonctions ODBC sont implémentées dans le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Le pilote passe les instructions SQL à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et retourne les résultats des instructions à l'application.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est conforme à la spécification Microsoft Win32 ODBC 3.51. Le pilote prend en charge les applications écrites à l'aide de versions antérieures d'ODBC selon la manière définie dans la spécification ODBC 3.51.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Noms des sources de données et systèmes d’exploitation 64 bits](../../../relational-databases/native-client/odbc/data-source-names-and-64-bit-operating-systems.md)  
  
-   [Création d’une Application de pilote ODBC de SQL Server Native Client](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
-   [Communication avec SQL Server &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [L’exécution de requêtes &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [Le traitement des résultats &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
-   [À l’aide de curseurs &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [Exécution de Transactions &#40; ODBC &#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
-   [Gestion des erreurs et des messages](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [Exécution de procédures stockées](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [Utilisation des fonctions de catalogue](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  
  
-   [Exécution d’opérations de copie en bloc &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [Gestion des colonnes texte et image](../../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [Profilage des données de performances du pilote ODBC](../../../relational-databases/native-client/odbc/profiling-odbc-driver-performance.md)  
  
-   [Table-Valued paramètres &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [Date et heure améliorations &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [Les Types CLR volumineux définis par l’utilisateur &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
-   [Prise en charge FILESTREAM &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/filestream-support-odbc.md)  
  
-   [Noms principaux de service &#40; Noms principaux de service &#41; dans les connexions clientes &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [Prise en charge des colonnes éparses &#40; ODBC &#41;](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)  
  
-   [SQL Server Native Client &#40; ODBC &#41; Référence](http://msdn.microsoft.com/library/06b7edee-8636-49d9-9b5c-2c710bf4fa2d)  
  
-   [Rubriques de procédures ODBC](../../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Installation de SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
  
  
