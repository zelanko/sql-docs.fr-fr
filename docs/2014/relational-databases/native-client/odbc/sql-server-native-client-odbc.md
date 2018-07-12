---
title: SQL Server Native Client (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
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
caps.latest.revision: 45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da24388b12c83931ea2a4af9b525e5e2030f6940
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426298"
---
# <a name="sql-server-native-client-odbc"></a>SQL Server Native Client (ODBC)
  ODBC est la définition standard d'une interface de programmation d'applications (API) utilisée pour accéder aux données des bases de données relationnelles ou à accès séquentiel indexé (Indexed Sequential Access Method). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge ODBC, via le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, comme l'une des API natives pour écrire des applications C et C++ qui communiquent avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Les programmes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] écrits à l'aide du pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client communiquent avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] via les appels de fonctions C. Les versions propres à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des fonctions ODBC sont implémentées dans le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Le pilote passe les instructions SQL à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et retourne les résultats des instructions à l'application.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client est conforme à la spécification Microsoft Win32 ODBC 3.51. Le pilote prend en charge les applications écrites à l'aide de versions antérieures d'ODBC selon la manière définie dans la spécification ODBC 3.51.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Noms des sources de données et systèmes d’exploitation 64 bits](data-source-names-and-64-bit-operating-systems.md)  
  
-   [Création d’une application de pilote ODBC SQL Server Native Client](creating-a-driver-application.md)  
  
-   [Communication avec SQL Server &#40;ODBC&#41;](../../native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [L’exécution de requêtes &#40;ODBC&#41;](../../native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [Traitement des résultats &#40;ODBC&#41;](../../native-client-odbc-results/processing-results-odbc.md)  
  
-   [L’utilisation de curseurs &#40;ODBC&#41;](../../native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [Exécution de Transactions &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
-   [Gestion des erreurs et des messages](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [Exécution de procédures stockées](../../native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [Utilisation des fonctions de catalogue](using-catalog-functions.md)  
  
-   [Exécution d’opérations de copie en bloc &#40;ODBC&#41;](../../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [Gestion des colonnes texte et image](../../native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [Profilage des données de performances du pilote ODBC](profiling-odbc-driver-performance.md)  
  
-   [Paramètres table &#40;ODBC&#41;](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [Améliorations date / heure &#40;ODBC&#41;](../../native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [Types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](large-clr-user-defined-types-odbc.md)  
  
-   [Prise en charge FILESTREAM &#40;ODBC&#41;](filestream-support-odbc.md)  
  
-   [Noms de principal du service &#40;SPN&#41; dans les connexions clientes &#40;ODBC&#41;](service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [Prise en charge des colonnes éparses &#40;ODBC&#41;](sparse-columns-support-odbc.md)  
  
-   [SQL Server Native Client &#40;ODBC&#41; référence](../../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md)  
  
-   [Rubriques de procédures liées à ODBC](../../native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation de SQL Server Native Client](../sql-server-native-client-programming.md)   
 [Installation de SQL Server Native Client](../applications/installing-sql-server-native-client.md)  
  
  
