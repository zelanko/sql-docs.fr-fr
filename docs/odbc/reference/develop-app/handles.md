---
description: Poignées
title: Handles | Microsoft Docs
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
ms.openlocfilehash: 6e9d2445dbbd676e8d48be519c1649d550fd89c5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465761"
---
# <a name="handles"></a>Poignées
Les handles sont des valeurs 32 bits opaques qui identifient un élément particulier ; dans ODBC, cet élément peut être un environnement, une connexion, une instruction ou un descripteur. Lorsque l’application appelle **SQLAllocHandle**, le gestionnaire de pilotes ou le pilote crée un nouvel élément du type spécifié et retourne son descripteur à l’application. L’application utilise ensuite le descripteur pour identifier cet élément lors de l’appel de fonctions ODBC. Le gestionnaire de pilotes et le pilote utilisent le descripteur pour rechercher des informations sur l’élément.  
  
 Par exemple, le code suivant utilise deux descripteurs d’instruction (*hstmtOrder* et *hstmtLine*) pour identifier les instructions sur lesquelles créer des jeux de résultats de commandes client et de numéros de ligne de commande client. Il utilise ensuite ces descripteurs pour identifier le jeu de résultats à partir duquel extraire les données.  
  
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
  
 Les handles sont significatifs uniquement pour le composant ODBC qui les a créés. autrement dit, seul le gestionnaire de pilotes peut interpréter les handles du gestionnaire de pilotes et seul un pilote peut interpréter ses propres handles.  
  
 Par exemple, supposons que le pilote de l’exemple précédent alloue une structure pour stocker des informations sur une instruction et retourne le pointeur vers cette structure en tant que descripteur d’instruction. Lorsque l’application appelle **SQLPrepare**, elle passe une instruction SQL et le descripteur de l’instruction utilisée pour les numéros de ligne de commande client. Le pilote envoie l’instruction SQL à la source de données, qui la prépare et retourne un identificateur de plan d’accès. Le pilote utilise le descripteur pour rechercher la structure dans laquelle stocker cet identificateur.  
  
 Plus tard, quand l’application appelle **SQLExecute** pour générer le jeu de résultats de numéros de ligne pour une commande client particulière, elle passe le même handle. Le pilote utilise le descripteur pour récupérer l’identificateur de plan d’accès à partir de la structure. Elle envoie l’identificateur à la source de données pour lui indiquer le plan à exécuter.  
  
 ODBC dispose de deux niveaux de handles : les handles du gestionnaire de pilotes et les handles de pilote. L’application utilise des handles du gestionnaire de pilotes lors de l’appel de fonctions ODBC, car elle appelle ces fonctions dans le gestionnaire de pilotes. Le gestionnaire de pilotes utilise ce handle pour trouver le handle de pilote correspondant et utilise le handle de pilote lors de l’appel de la fonction dans le pilote. Pour obtenir un exemple d’utilisation des gestionnaires de pilote et de pilote, consultez [rôle du gestionnaire de pilotes dans le processus de connexion](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).  
  
 Le fait qu’il existe deux niveaux de descripteurs est un artefact de l’architecture ODBC ; dans la plupart des cas, il ne s’applique pas à l’application ou au pilote. Bien qu’il n’y ait généralement aucune raison de le faire, il est possible pour l’application de déterminer les handles de pilote en appelant **SQLGetInfo**.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Handles d’environnement](../../../odbc/reference/develop-app/environment-handles.md)  
  
-   [Handles de connexion](../../../odbc/reference/develop-app/connection-handles.md)  
  
-   [Handles d’instruction](../../../odbc/reference/develop-app/statement-handles.md)  
  
-   [Handles de descripteur](../../../odbc/reference/develop-app/descriptor-handles.md)  
  
-   [Transitions d’état](../../../odbc/reference/develop-app/state-transitions.md)
