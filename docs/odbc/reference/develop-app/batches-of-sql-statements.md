---
title: Lots de déclarations SQL Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC]
- SQL statements [ODBC], batches
- batches [ODBC], about batches
ms.assetid: 766488cc-450c-434c-9c88-467f6c57e17c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d68ea1c13655ca7c57ba076823f461a4b2e22055
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283509"
---
# <a name="batches-of-sql-statements"></a>Lots d’instructions SQL
Un lot de déclarations SQL est un groupe de deux déclarations SQL ou plus d’une seule déclaration SQL qui a le même effet qu’un groupe de deux ou plusieurs déclarations SQL. Dans certaines implémentations, l’ensemble de l’instruction du lot est exécuté avant que les résultats ne soient disponibles. Ceci est souvent plus efficace que de soumettre des déclarations séparément, parce que le trafic réseau peut souvent être réduit et la source de données peut parfois optimiser l’exécution d’un lot de déclarations SQL. Dans d’autres implémentations, appeler **SQLMoreResults** déclenche l’exécution de la prochaine déclaration dans le lot. ODBC prend en charge les types de lots suivants :  
  
-   **Batches explicites** Un *lot explicite* est deux ou plusieurs déclarations SQL séparées par des semi-colons (;). Par exemple, le lot suivant de relevés SQL ouvre une nouvelle commande de vente. Cela nécessite l’insertion de lignes dans les tables Ordres et Lignes. Notez qu’il n’y a pas de point-virgule après la dernière déclaration.  
  
    ```  
    INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
       VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 1, 1234, 10);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 2, 987, 8);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 3, 566, 17);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 4, 412, 500)  
    ```  
  
-   **Procédures** Si une procédure contient plus d’une déclaration SQL, il est considéré comme un lot de déclarations SQL. Par exemple, l’instruction spécifique à SQL Server suivante crée une procédure qui renvoie un ensemble de résultats contenant des informations sur un client et un ensemble de résultats énumérant toutes les commandes de vente ouvertes pour ce client :  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     La déclaration **CREATE PROCEDURE** elle-même n’est pas un lot de déclarations SQL. Cependant, la procédure qu’il crée est un lot de déclarations SQL. Aucun semi-colyle ne sépare les deux énoncés **SELECT** parce que la déclaration **CREATE PROCEDURE** est spécifique à SQL Server, et SQL Server n’exige pas que les semi-colons séparent plusieurs déclarations dans une déclaration **CREATE PROCEDURE.**  
  
-   **Tableaux de paramètres** Les ensembles de paramètres peuvent être utilisés avec un énoncé SQL paramétré comme moyen efficace d’effectuer des opérations en vrac. Par exemple, des ensembles de paramètres peuvent être utilisés avec l’instruction **INSERT** suivante pour insérer plusieurs lignes dans la table Lines tout en exécutant seulement une seule déclaration SQL :  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     Si une source de données ne prend pas en charge les ensembles de paramètres, le conducteur peut les imiter en exécutant la déclaration SQL une fois pour chaque ensemble de paramètres. Pour plus d’informations, voir [Paramètres d’énoncé et](../../../odbc/reference/develop-app/statement-parameters.md) [tableaux de valeurs de paramètres](../../../odbc/reference/develop-app/arrays-of-parameter-values.md), plus tard dans cette section.  
  
 Les différents types de lots ne peuvent pas être mélangés d’une manière interopérable. C’est-à-dire comment une application détermine le résultat de l’exécution d’un lot explicite qui comprend des appels de procédure, un lot explicite qui utilise des tableaux de paramètres, et un appel de procédure qui utilise des tableaux de paramètres est spécifique au conducteur.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Instructions avec génération de résultats et sans résultats](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [Exécution de lots](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [Erreurs et lots](../../../odbc/reference/develop-app/errors-and-batches.md)
