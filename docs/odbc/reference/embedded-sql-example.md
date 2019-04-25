---
title: Embedded SQL exemple | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eef8c87a152795d4756d05ba8a279a0d12cbc38c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62628613"
---
# <a name="embedded-sql-example"></a>Exemple Embedded SQL
Le code suivant est un simple programme SQL incorporé, écrit en C. Le programme illustre des techniques SQL nombreuses, mais pas tout, de l’élément incorporé. Le programme invite l’utilisateur à un numéro de commande récupère le numéro de client, le vendeur et l’état de la commande et affiche les informations récupérées à l’écran.  
  
```  
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
  
 Notez les points suivants concernant ce programme :  
  
-   **Héberger des Variables** les variables de l’hôte sont déclarées dans une section délimitée par le **BEGIN DECLARE SECTION** et **END DECLARE SECTION** mots clés. Chaque nom de variable d’hôte est préfixé par un signe deux-points ( :)) lorsqu’il apparaît dans une instruction SQL incorporée. Le signe deux-points permet le précompilateur faire la distinction entre les variables de l’hôte et des objets de base de données, tels que des tables et des colonnes qui ont le même nom.  
  
-   **Types de données** les types de données pris en charge par un système SGBD et un langage hôte peuvent être très différentes. Cela affecte les variables de l’hôte, car ils jouent un rôle en double. D’une part, les variables hôtes sont des variables de programme, déclaré et manipulées par les instructions de langage hôte. En revanche, ils sont utilisés dans les instructions SQL incorporées pour récupérer des données de base de données. S’il n’existe aucun type de langage hôte qui correspond à un type de données SGBD, le SGBD convertit automatiquement les données. Toutefois, étant donné que chaque SGBD a ses propres règles et les spécificités liées au processus de conversion, les types de variables d’hôte doivent être choisies avec soin.  
  
-   **Gestion des erreurs** le SGBD signale des erreurs d’exécution du programme d’applications via une zone de communication SQL ou SQLCA. Dans l’exemple de code précédent, la première instruction SQL incorporée est INCLUDE SQLCA. Cela indique le précompilateur pour inclure la structure SQLCA dans le programme. Cela est nécessaire chaque fois que le programme traite les erreurs retournées par le SGBD. Le WHENEVER... GOTO (instruction) indique le précompilateur pour générer le code de gestion des erreurs qui effectue un branchement vers une étiquette spécifique lorsqu’une erreur se produit.  
  
-   **Singleton sélectionnez** l’instruction utilisée pour renvoyer les données est une instruction SELECT singleton ; autrement dit, elle retourne une seule ligne de données. Par conséquent, l’exemple de code ne déclarer ni utiliser des curseurs.
