---
title: Exécution de requêtes (ODBC) | Microsoft Docs
description: Une application ODBC peut exécuter des instructions sur une instance de SQL Server en initialisant un handle de connexion et en se connectant à une source de données.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, executing queries
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
- SQL Server Native Client ODBC driver, queries
- queries [ODBC]
ms.assetid: d935bcba-8ce6-4159-8395-6c86431602ad
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1324ea8ab9f186726c965685a7261f78cabf5bc2
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97438402"
---
# <a name="executing-queries-odbc"></a>Exécution de requêtes (ODBC)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Après qu'une application ODBC a initialisé un handle de connexion et s'est connectée avec une source de données, elle alloue un ou plusieurs descripteurs d'instruction sur le handle de connexion. L’application peut ensuite exécuter [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des instructions sur le descripteur d’instruction. La séquence générale des événements lors de l'exécution d'une instruction SQL est :  
  
1.  Définition des attributs de l'instruction requis.  
  
2.  Construction de l'instruction.  
  
3.  Exécution de l'instruction.  
  
4.  Extraction des jeux de résultats éventuels.  
  
 Après qu'une application a extrait toutes les lignes dans tous les jeux de résultats retournés par l'instruction SQL, elle peut exécuter une autre requête sur le même descripteur d'instruction. Si une application détermine qu’il n’est pas nécessaire d’extraire toutes les lignes d’un jeu de résultats particulier, elle peut annuler le reste du jeu de résultats en appelant [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) ou [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
 Si, dans une application ODBC, vous devez exécuter plusieurs fois la même instruction SQL avec des données différentes, utilisez un marqueur de paramètre dénoté par un point d'interrogation (?) dans la construction d'une instruction SQL :  
  
```  
INSERT INTO MyTable VALUES (?, ?, ?)  
```  
  
 Chaque marqueur de paramètre peut ensuite être lié à une variable de programme en appelant [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md).  
  
 Après l'exécution de toutes les instructions SQL et le traitement de leurs jeux de résultats, l'application libère le descripteur d'instruction.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge plusieurs descripteurs d’instruction par handle de connexion. Les transactions sont gérées au niveau de la connexion, afin que tout le travail effectué sur tous les descripteurs d'instruction sur un handle de connexion unique soit géré dans le cadre de la même transaction.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Allocation d'un descripteur d'instruction](../../relational-databases/native-client-odbc-queries/allocating-a-statement-handle.md)  
  
-   [Construction d’une instruction SQL &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/constructing-an-sql-statement-odbc.md)  
  
-   [Construction d'instructions SQL pour les curseurs](../../relational-databases/native-client-odbc-queries/constructing-sql-statements-for-cursors.md)  
  
-   [Utilisation de paramètres d'instruction](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
-   [Exécution d’instructions &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
-   [Libération d'un descripteur d'instruction](../../relational-databases/native-client-odbc-queries/freeing-a-statement-handle.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  
