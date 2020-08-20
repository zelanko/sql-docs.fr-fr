---
description: Exécution d’une instruction
title: Exécution d’une instruction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], executing
ms.assetid: e5f0d2ee-0453-4faf-b007-12978dd300a1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ce060c91e2500b016e824e733d8189c99334e1b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461471"
---
# <a name="executing-a-statement"></a>Exécution d’une instruction
Il existe quatre façons d’exécuter une instruction, selon le moment où elles sont compilées (préparées) par le moteur de base de données et qui les définit :  
  
-   **Exécution directe** L’application définit l’instruction SQL. Elle est préparée et exécutée au moment de l’exécution en une seule étape.  
  
-   **Exécution préparée** L’application définit l’instruction SQL. Elle est préparée et exécutée au moment de l’exécution dans des étapes distinctes. L’instruction peut être préparée une fois et exécutée plusieurs fois.  
  
-   **Procédures** L’application peut définir et compiler une ou plusieurs instructions SQL au moment du développement et stocker ces instructions sur la source de données comme une procédure. La procédure est exécutée une ou plusieurs fois au moment de l’exécution. L’application peut énumérer les procédures stockées disponibles à l’aide des fonctions de catalogue.  
  
-   **Fonctions de catalogue** Le writer de pilote crée une fonction qui retourne un jeu de résultats prédéfini. En règle générale, cette fonction envoie une instruction SQL prédéfinie ou appelle une procédure créée à cet effet. La fonction est exécutée une ou plusieurs fois au moment de l’exécution.  
  
 Une instruction particulière (identifiée par son descripteur d’instruction) peut être exécutée plusieurs fois. L’instruction peut être exécutée avec différentes instructions SQL, ou elle peut être exécutée à plusieurs reprises avec la même instruction SQL. Par exemple, le code suivant utilise le même descripteur d’instruction (*hstmt1*) pour récupérer et afficher les tables dans la base de données Sales. Il réutilise ensuite ce handle pour récupérer les colonnes d’une table sélectionnée par l’utilisateur.  
  
```  
SQLHSTMT    hstmt1;  
SQLCHAR *   Table;  
  
// Create a result set of all tables in the Sales database.  
SQLTables(hstmt1, "Sales", SQL_NTS, "sysadmin", SQL_NTS, NULL, 0, NULL, 0);  
  
// Fetch and display the table names; then close the cursor.  
// Code not shown.  
  
// Have the user select a particular table.  
SelectTable(Table);  
  
// Reuse hstmt1 to create a result set of all columns in Table.  
SQLColumns(hstmt1, "Sales", SQL_NTS, "sysadmin", SQL_NTS, Table, SQL_NTS, NULL, 0);  
  
// Fetch and display the column names in Table; then close the cursor.  
// Code not shown.  
```  
  
 Et le code suivant montre comment un seul descripteur est utilisé pour exécuter de manière répétée la même instruction afin de supprimer des lignes d’une table.  
  
```  
SQLHSTMT      hstmt1;  
SQLUINTEGER   OrderID;  
SQLINTEGER    OrderIDInd = 0;  
  
// Prepare a statement to delete orders from the Orders table.  
SQLPrepare(hstmt1, "DELETE FROM Orders WHERE OrderID = ?", SQL_NTS);  
  
// Bind OrderID to the parameter for the OrderID column.  
SQLBindParameter(hstmt1, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
                  &OrderID, 0, &OrderIDInd);  
  
// Repeatedly execute hstmt1 with different values of OrderID.  
while ((OrderID = GetOrderID()) != 0) {  
   SQLExecute(hstmt1);  
}  
```  
  
 Pour de nombreux pilotes, l’allocation d’instructions est une tâche coûteuse. par conséquent, il est généralement plus efficace de réutiliser la même instruction que de libérer des instructions existantes et d’en allouer de nouvelles. Les applications qui créent des jeux de résultats sur une instruction doivent veiller à fermer le curseur sur le jeu de résultats avant de réexécuter l’instruction. Pour plus d’informations, consultez [fermeture du curseur](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 La réutilisation des instructions oblige également l’application à éviter une limitation dans certains pilotes du nombre d’instructions qui peuvent être actives simultanément. La définition exacte de « active » est spécifique au pilote, mais elle fait souvent référence à toute instruction préparée ou exécutée et dont les résultats sont toujours disponibles. Par exemple, une fois qu’une instruction **Insert** a été préparée, elle est généralement considérée comme active ; une fois qu’une instruction **Select** a été exécutée et que le curseur est toujours ouvert, elle est généralement considérée comme active ; une fois qu’une instruction **Create table** a été exécutée, elle n’est généralement pas considérée comme active.  
  
 Une application détermine le nombre d’instructions qui peuvent être actives sur une seule connexion à la fois en appelant **SQLGetInfo** avec l’option SQL_MAX_CONCURRENT_ACTIVITIES. Une application peut utiliser des instructions plus actives que cette limite en ouvrant plusieurs connexions à la source de données ; étant donné que les connexions peuvent être onéreuses, l’effet sur les performances doit être pris en compte.  
  
 Les applications peuvent limiter la durée allouée à l’exécution d’une instruction avec l’attribut d’instruction SQL_ATTR_QUERY_TIMEOUT. Si le délai d’expiration expire avant que la source de données ne retourne le jeu de résultats, la fonction qui exécute l’instruction SQL retourne SQLSTATE HYT00 (délai d’attente expiré). Par défaut, aucun délai d’attente n’est défini.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Exécution directe](../../../odbc/reference/develop-app/direct-execution-odbc.md)  
  
-   [Exécution préparée](../../../odbc/reference/develop-app/prepared-execution-odbc.md)  
  
-   [Procédures](../../../odbc/reference/develop-app/procedures-odbc.md)  
  
-   [Lots d’instructions SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md)  
  
-   [Exécution de fonctions de catalogue](../../../odbc/reference/develop-app/executing-catalog-functions.md)
