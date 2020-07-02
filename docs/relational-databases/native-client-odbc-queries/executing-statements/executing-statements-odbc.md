---
title: Exécution d’instructions (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a284851d59ce1a5a8f64faa02555303adcd66092
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775930"
---
# <a name="executing-statements-odbc"></a>Exécution d'instructions (ODBC)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client offre plusieurs moyens d’exécuter des instructions SQL dans une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] base de données :  
  
-   Exécution directe  
  
-   Exécution préparée  
  
 L’exécution directe implique la génération d’une chaîne de caractères contenant une [!INCLUDE[tsql](../../../includes/tsql-md.md)] instruction et son envoi en vue d’une exécution à l’aide de la fonction **SQLExecDirect** . L'exécution préparée implique la génération d'une chaîne de caractères contenant une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] et son exécution en deux étapes. La première étape utilise la fonction [SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) pour analyser et compiler le plan d’exécution de l’instruction dans le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] . La deuxième étape utilise la fonction **SQLExecute** pour exécuter le plan d’exécution précédemment préparé. Cela permet de réduire la charge d'analyse et de compilation pour chaque exécution. L'exécution préparée est couramment utilisée par les applications pour exécuter de manière répétée la même instruction SQL paramétrable.  
  
 Les exécutions directe et préparée peuvent exécuter une instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] unique ou un lot d'instructions SQL, ou elles peuvent appeler une procédure stockée.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Exécution directe](../../../relational-databases/native-client-odbc-queries/executing-statements/direct-execution.md)  
  
-   [Exécution préparée](../../../relational-databases/native-client-odbc-queries/executing-statements/prepared-execution.md)  
  
-   [Procédures](../../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
-   [Lots d'instructions](../../../relational-databases/native-client-odbc-queries/executing-statements/batches-of-statements.md)  
  
-   [Conséquences des options ISO](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de requêtes &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
