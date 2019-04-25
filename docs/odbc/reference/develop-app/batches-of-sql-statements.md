---
title: Lots d’instructions SQL | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09805ab73af76bc55890222fc1ffd0e1857d0f33
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62447387"
---
# <a name="batches-of-sql-statements"></a>Lots d’instructions SQL
Un lot d’instructions SQL est un groupe de deux ou plusieurs instructions SQL ou une instruction SQL unique qui a le même effet en tant que groupe de deux ou plusieurs instructions SQL. Dans certaines implémentations, l’instruction du lot entier est exécutée avant que les résultats soient disponibles. Ceci est souvent plus efficace que la soumission des instructions séparément, car le trafic réseau peut souvent être réduit et la source de données peut optimiser parfois de l’exécution d’un lot d’instructions SQL. Dans d’autres implémentations, appelant **SQLMoreResults** entraîne l’exécution de l’instruction suivante dans le lot. ODBC prend en charge les types de lots suivants :  
  
-   **Lots explicites** un *traitement explicite* est de deux ou plusieurs instructions SQL séparées par des points-virgules ( ;). Par exemple, le lot suivant d’instructions SQL ouvre une nouvelle commande. Cela nécessite l’insertion de lignes dans les commandes et les lignes des tables. Notez qu’il n’existe aucun point-virgule après la dernière instruction.  
  
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
  
-   **Procédures** si une procédure contient plusieurs instructions SQL, il est considéré comme un lot d’instructions SQL. Par exemple, l’instruction spécifiques à SQL Server suivante crée une procédure qui retourne un jeu de résultats contenant des informations concernant un client et un jeu de résultats dressant toutes les commandes ventes ouvertes pour ce client :  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     Le **CREATE PROCEDURE** instruction proprement dite n’est pas un lot d’instructions SQL. Toutefois, la procédure qu’il crée est un lot d’instructions SQL. Aucun des points-virgules ne séparent les deux **sélectionnez** instructions, car le **CREATE PROCEDURE** instruction est spécifique à SQL Server et SQL Server ne nécessite pas un point-virgule pour séparer plusieurs instructions dans un  **CREATE PROCEDURE** instruction.  
  
-   **Tableaux de paramètres** tableaux de paramètres peuvent être utilisées avec une instruction SQL paramétrée comme un moyen efficace pour effectuer des opérations en bloc. Par exemple, les tableaux de paramètres peuvent être utilisés par le code suivant **insérer** instruction pour insérer plusieurs lignes dans la table de lignes lors de l’exécution d’une seule instruction SQL :  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     Si une source de données ne prend pas en charge les tableaux de paramètres, le pilote peut les émuler en exécutant l’instruction SQL une fois pour chaque jeu de paramètres. Pour plus d’informations, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md) et [tableaux de valeurs de paramètre](../../../odbc/reference/develop-app/arrays-of-parameter-values.md), plus loin dans cette section.  
  
 Les différents types de lots ne peuvent pas être combinés de manière interopérable. Autrement dit, comment une application détermine le résultat de l’exécution d’un lot explicit qui inclut la procédure appelle, un traitement explicite qui utilise des tableaux de paramètres, et un appel de procédure qui utilise des tableaux de paramètres est spécifique au pilote.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Instructions avec génération de résultats et sans résultats](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [Exécution de lots](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [Erreurs et lots](../../../odbc/reference/develop-app/errors-and-batches.md)
