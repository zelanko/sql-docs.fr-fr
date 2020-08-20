---
description: Lots d’instructions SQL
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e342fd7eaef721f8fb0033a5ae022ca8de74cda1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465931"
---
# <a name="batches-of-sql-statements"></a>Lots d’instructions SQL
Un lot d’instructions SQL est un groupe d’au moins deux instructions SQL ou une instruction SQL unique qui a le même effet qu’un groupe d’au moins deux instructions SQL. Dans certaines implémentations, la totalité de l’instruction batch est exécutée avant que les résultats ne soient disponibles. Cela est souvent plus efficace que l’envoi d’instructions séparément, car le trafic réseau peut souvent être réduit et la source de données peut parfois optimiser l’exécution d’un lot d’instructions SQL. Dans d’autres implémentations, l’appel de **SQLMoreResults** déclenche l’exécution de l’instruction suivante dans le lot. ODBC prend en charge les types de lots suivants :  
  
-   **Lots explicites** Un *lot explicite* est composé de deux ou plusieurs instructions SQL séparées par des points-virgules (;). Par exemple, le lot d’instructions SQL suivant ouvre une nouvelle commande client. Cela nécessite l’insertion de lignes dans les tables Orders et Lines. Notez qu’il n’y a pas de point-virgule après la dernière instruction.  
  
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
  
-   **Procédures** Si une procédure contient plus d’une instruction SQL, elle est considérée comme un lot d’instructions SQL. Par exemple, l’instruction suivante spécifique au SQL Server crée une procédure qui retourne un jeu de résultats contenant des informations sur un client et un jeu de résultats répertoriant toutes les commandes client ouvertes pour ce client :  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     L’instruction **CREATE PROCEDURE** proprement dite n’est pas un lot d’instructions SQL. Toutefois, la procédure qu’il crée est un lot d’instructions SQL. Aucun point-virgule ne sépare les deux instructions **Select** , car l’instruction **CREATE PROCEDURE** est spécifique à SQL Server, et SQL Server ne requiert pas de point-virgule pour séparer plusieurs instructions dans une instruction **CREATE PROCEDURE** .  
  
-   **Tableaux de paramètres** Les tableaux de paramètres peuvent être utilisés avec une instruction SQL paramétrable comme un moyen efficace d’effectuer des opérations en bloc. Par exemple, des tableaux de paramètres peuvent être utilisés avec l’instruction **Insert** suivante pour insérer plusieurs lignes dans la table de lignes lors de l’exécution d’une seule instruction SQL :  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     Si une source de données ne prend pas en charge les tableaux de paramètres, le pilote peut les émuler en exécutant l’instruction SQL une fois pour chaque jeu de paramètres. Pour plus d’informations, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md) et [tableaux de valeurs de paramètre](../../../odbc/reference/develop-app/arrays-of-parameter-values.md), plus loin dans cette section.  
  
 Les différents types de lots ne peuvent pas être mélangés de manière interopérable. Autrement dit, la façon dont une application détermine le résultat de l’exécution d’un lot explicite qui comprend des appels de procédure, un lot explicite qui utilise des tableaux de paramètres et un appel de procédure qui utilise des tableaux de paramètres est spécifique au pilote.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Instructions avec génération de résultats et sans résultats](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [Exécution de lots](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [Erreurs et lots](../../../odbc/reference/develop-app/errors-and-batches.md)
