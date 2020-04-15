---
title: Poignées Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- handles [ODBC]
- driver handles [ODBC]
- driver manager [ODBC], handles
- handles [ODBC], about handles
ms.assetid: f663101e-a4cc-402b-b9d7-84d5e975be71
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 713c2a71ec195b75d682b97239413e98d07b5861
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300209"
---
# <a name="handles"></a>Poignées
Les poignées sont opaques, des valeurs 32 bits qui identifient un élément particulier; dans ODBC, cet article peut être un environnement, une connexion, une déclaration ou un descripteur. Lorsque l’application appelle **SQLAllocHandle**, le gestionnaire de conducteur ou le pilote crée un nouvel élément du type spécifié et renvoie sa poignée à l’application. L’application utilise plus tard la poignée pour identifier cet élément lors de l’appel des fonctions ODBC. Le gestionnaire du conducteur et le conducteur utilisent la poignée pour trouver des informations sur l’article.  
  
 Par exemple, le code suivant utilise deux poignées de relevés (*hstmtOrder* et *hstmtLine*) pour identifier les énoncés sur lesquels créer des ensembles de résultats des ordres de vente et des numéros de ligne de commande de vente. Il utilise plus tard ces poignées pour identifier les résultats définis pour obtenir des données.  
  
```  
SQLHSTMT      hstmtOrder, hstmtLine; // Statement handles.  
SQLUINTEGER   OrderID;  
SQLINTEGER    OrderIDInd = 0;  
SQLRETURN     rc;  
  
// Prepare the statement that retrieves line number information.  
SQLPrepare(hstmtLine, "SELECT * FROM Lines WHERE OrderID = ?", SQL_NTS);  
  
// Bind OrderID to the parameter in the preceding statement.  
SQLBindParameter(hstmtLine, 1, SQL_PARAM_INPUT, SQL_C_ULONG, SQL_INTEGER, 5, 0,  
               &OrderID, 0, &OrderIDInd);  
  
// Bind the result sets for the Order table and the Lines table. Bind  
// OrderID to the OrderID column in the Orders table. When each row is  
// fetched, OrderID will contain the current order ID, which will then be  
// passed as a parameter to the statement tofetch line number  
// information. Code not shown.  
  
// Create a result set of sales orders.  
SQLExecDirect(hstmtOrder, "SELECT * FROM Orders", SQL_NTS);  
  
// Fetch and display the sales order data. Code to check if rc equals  
// SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmtOrder)) != SQL_NO_DATA) {  
   // Display the sales order data. Code not shown.  
  
   // Create a result set of line numbers for the current sales order.  
   SQLExecute(hstmtLine);  
  
   // Fetch and display the sales order line number data. Code to check  
   // if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO not shown.  
   while ((rc = SQLFetch(hstmtLine)) != SQL_NO_DATA) {  
      // Display the sales order line number data. Code not shown.  
   }  
  
   // Close the sales order line number result set.  
   SQLCloseCursor(hstmtLine);  
}  
  
// Close the sales order result set.  
SQLCloseCursor(hstmtOrder);  
```  
  
 Les poignées ne sont significatives que pour le composant ODBC qui les a créés; c’est-à-dire que seul le Gestionnaire de conducteur peut interpréter les poignées driver Manager et seul un conducteur peut interpréter ses propres poignées.  
  
 Supposons, par exemple, que le conducteur attribue dans l’exemple précédent une structure pour stocker des informations sur une déclaration et retourne le pointeur à cette structure au fur et à mesure que la poignée de l’instruction. Lorsque l’application appelle **SQLPrepare**, elle passe une déclaration SQL et la poignée de l’instruction utilisée pour les numéros de ligne de commande de vente. Le conducteur envoie la déclaration SQL à la source de données, qui la prépare et renvoie un identifiant de plan d’accès. Le conducteur utilise la poignée pour trouver la structure dans laquelle stocker cet identifiant.  
  
 Plus tard, lorsque l’application appelle **SQLExecute** pour générer l’ensemble de résultats de numéros de ligne pour un ordre de vente particulier, il passe la même poignée. Le conducteur utilise la poignée pour récupérer l’identifiant du plan d’accès de la structure. Il envoie l’identifiant à la source de données pour lui indiquer quel plan exécuter.  
  
 ODBC a deux niveaux de poignées : les poignées de gestionnaire de conducteur et les poignées de conducteur. L’application utilise Driver Manager poignées lors de l’appel ODBC fonctions parce qu’il appelle ces fonctions dans le gestionnaire de conducteur. Le gestionnaire de conducteur utilise cette poignée pour trouver la poignée correspondante du conducteur et utilise la poignée du conducteur lorsqu’il appelle la fonction dans le conducteur. Pour un exemple de la façon dont les poignées du conducteur et du gestionnaire de conducteur sont utilisées, consultez [le rôle du gestionnaire de conducteur dans le processus de connexion](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Qu’il y ait deux niveaux de poignées est un artefact de l’architecture ODBC; dans la plupart des cas, il n’est pertinent ni pour l’application ni pour le conducteur. Bien qu’il n’y ait généralement aucune raison de le faire, il est possible pour l’application de déterminer les poignées du conducteur en appelant **SQLGetInfo**.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Handles d’environnement](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [Handles de connexion](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [Handles d’instruction](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [Handles de descripteur](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [Transitions d’état](../../../odbc/reference/develop-app/state-transitions.md)
