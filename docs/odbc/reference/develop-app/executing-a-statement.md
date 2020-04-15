---
title: Exécution d’une déclaration (en anglais) Microsoft Docs
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
ms.openlocfilehash: c3ce09809c896a4d1d9333da00367f972655f96b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305740"
---
# <a name="executing-a-statement"></a>Exécution d’une instruction
Il existe quatre façons d’exécuter une déclaration, selon le moment où ils sont compilés (préparés) par le moteur de base de données et qui les définit:  
  
-   **Exécution directe** L’application définit la déclaration SQL. Il est préparé et exécuté au moment de la course en une seule étape.  
  
-   **Exécution préparée** L’application définit la déclaration SQL. Il est préparé et exécuté au moment de l’exécution en étapes séparées. L’instruction peut être préparée une fois et exécutée plusieurs fois.  
  
-   **Procédures** L’application peut définir et compiler un ou plusieurs relevés SQL au moment du développement et stocker ces énoncés sur la source de données comme une procédure. La procédure est exécutée une ou plusieurs fois au moment de l’exécution. L’application peut énumérer les procédures stockées disponibles à l’aide de fonctions de catalogue.  
  
-   **Fonctions de catalogue** L’auteur pilote crée une fonction qui renvoie un ensemble de résultats prédéfinis. Habituellement, cette fonction soumet une déclaration SQL prédéfinie ou appelle une procédure créée à cette fin. La fonction est exécutée une ou plusieurs fois au moment de l’exécution.  
  
 Une déclaration particulière (telle qu’identifiée par sa poignée de déclaration) peut être exécutée n’importe quel nombre de fois. La déclaration peut être exécutée avec une variété de déclarations SQL différentes, ou il peut être exécuté à plusieurs reprises avec la même déclaration SQL. Par exemple, le code suivant utilise la même poignée de relevé (*hstmt1*) pour récupérer et afficher les tables dans la base de données des ventes. Il réutilise ensuite cette poignée pour récupérer les colonnes dans une table sélectionnée par l’utilisateur.  
  
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
  
 Et le code suivant montre comment une seule poignée est utilisée pour exécuter à plusieurs reprises la même instruction pour supprimer les lignes d’une table.  
  
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
  
 Pour de nombreux conducteurs, l’attribution des déclarations est une tâche coûteuse, de sorte que la réutilité de la même déclaration de cette manière est généralement plus efficace que la libération des déclarations existantes et l’attribution de nouveaux. Les applications qui créent des ensembles de résultats sur une instruction doivent prendre soin de fermer le curseur sur le résultat défini avant de réexaminer l’instruction; pour plus d’informations, voir [Closing the Cursor](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 La réutilation des déclarations oblige également la demande à éviter une limitation chez certains conducteurs du nombre d’énoncés qui peuvent être actifs en même temps. La définition exacte de « actif » est spécifique au conducteur, mais elle fait souvent référence à toute déclaration qui a été préparée ou exécutée et qui a encore des résultats disponibles. Par exemple, une fois qu’une déclaration **INSERT** a été préparée, elle est généralement considérée comme active; après qu’une déclaration **SELECT** a été exécutée et que le curseur est toujours ouvert, il est généralement considéré comme actif; après l’exécution d’une déclaration **CREATE TABLE,** elle n’est généralement pas considérée comme active.  
  
 Une application détermine le nombre d’instructions qui peuvent être actives sur une seule connexion en même temps en appelant **SQLGetInfo** avec l’option SQL_MAX_CONCURRENT_ACTIVITIES. Une application peut utiliser des déclarations plus actives que cette limite en ouvrant plusieurs connexions à la source de données ; parce que les connexions peuvent être coûteuses, cependant, l’effet sur les performances doit être pris en considération.  
  
 Les applications peuvent limiter le temps alloué à une déclaration pour exécuter avec l’attribut SQL_ATTR_QUERY_TIMEOUT déclaration. Si la période de délai expire avant que la source de données ne renvoie l’ensemble de résultats, la fonction exécutant la déclaration SQL renvoie SQLSTATE HYT00 (délai expiré). Par défaut, aucun délai d’attente n’est défini.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Exécution directe](../../../odbc/reference/develop-app/direct-execution-odbc.md)  
  
-   [Exécution préparée](../../../odbc/reference/develop-app/prepared-execution-odbc.md)  
  
-   [Procédures](../../../odbc/reference/develop-app/procedures-odbc.md)  
  
-   [Lots d’instructions SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md)  
  
-   [Exécution de fonctions de catalogue](../../../odbc/reference/develop-app/executing-catalog-functions.md)
