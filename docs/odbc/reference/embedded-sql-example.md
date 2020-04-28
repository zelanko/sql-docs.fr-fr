---
title: Exemple EmbeddedSQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- embedded SQL [ODBC]
ms.assetid: b8a26e05-3c82-4c5f-8f01-9de0edb645e9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39ec504c423817c6a3e11bc954555b201b8b09c6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294170"
---
# <a name="embedded-sql-example"></a>Exemple Embedded SQL
Le code suivant est un simple programme Embedded SQL, écrit en C. Le programme illustre de nombreuses techniques SQL incorporées, mais pas toutes. Le programme invite l’utilisateur à entrer un numéro de commande, extrait le numéro de client, le vendeur et l’état de la commande, puis affiche les informations récupérées à l’écran.  
  
```cpp  
int main() {  
   EXEC SQL INCLUDE SQLCA;  
   EXEC SQL BEGIN DECLARE SECTION;  
      int OrderID;         /* Employee ID (from user)         */  
      int CustID;            /* Retrieved customer ID         */  
      char SalesPerson[10]   /* Retrieved salesperson name      */  
      char Status[6]         /* Retrieved order status        */  
   EXEC SQL END DECLARE SECTION;  
  
   /* Set up error processing */  
   EXEC SQL WHENEVER SQLERROR GOTO query_error;  
   EXEC SQL WHENEVER NOT FOUND GOTO bad_number;  
  
   /* Prompt the user for order number */  
   printf ("Enter order number: ");  
   scanf_s("%d", &OrderID);  
  
   /* Execute the SQL query */  
   EXEC SQL SELECT CustID, SalesPerson, Status  
      FROM Orders  
      WHERE OrderID = :OrderID  
      INTO :CustID, :SalesPerson, :Status;  
  
   /* Display the results */  
   printf ("Customer number:  %d\n", CustID);  
   printf ("Salesperson: %s\n", SalesPerson);  
   printf ("Status: %s\n", Status);  
   exit();  
  
query_error:  
   printf ("SQL error: %ld\n", sqlca->sqlcode);  
   exit();  
  
bad_number:  
   printf ("Invalid order number.\n");  
   exit();  
}  
```  
  
 Notez les points suivants à propos de ce programme :  
  
-   **Variables hôtes** Les variables hôtes sont déclarées dans une section délimitée par les mots clés **Begin DECLARE section** et **end DECLARE section** . Chaque nom de variable hôte est préfixé par un signe deux-points ( :) lorsqu’il apparaît dans une instruction SQL incorporée. Le signe deux-points permet au précompilateur de faire la distinction entre les variables hôtes et les objets de base de données, tels que les tables et les colonnes, qui portent le même nom.  
  
-   **Types de données** Les types de données pris en charge par un SGBD et un langage hôte peuvent être très différents. Cela affecte les variables hôtes, car elles jouent un rôle double. D’une part, les variables hôtes sont des variables de programme, déclarées et manipulées par des instructions de langage hôte. En revanche, elles sont utilisées dans les instructions SQL incorporées pour récupérer les données de la base de données. S’il n’existe aucun type de langue hôte qui correspond à un type de données SGBD, le SGBD convertit automatiquement les données. Toutefois, étant donné que chaque SGBD a ses propres règles et particularités associées au processus de conversion, les types de variables hôtes doivent être choisis avec précaution.  
  
-   **Gestion des erreurs** Le SGBD signale les erreurs d’exécution au programme d’applications par le biais d’une zone de communication SQL, ou SQLCA. Dans l’exemple de code précédent, la première instruction EmbeddedSQL est INCLUDe SQLCA. Cela indique au précompilateur d’inclure la structure SQLCA dans le programme. Cette opération est requise chaque fois que le programme traitera les erreurs retournées par le SGBD. À chaque fois... L’instruction GOTO indique au précompilateur de générer le code de gestion des erreurs qui crée une branche vers une étiquette spécifique lorsqu’une erreur se produit.  
  
-   **Singleton Select** L’instruction utilisée pour retourner les données est une instruction SELECT Singleton ; autrement dit, elle ne retourne qu’une seule ligne de données. Par conséquent, l’exemple de code ne déclare pas ou n’utilise pas de curseurs.
