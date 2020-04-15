---
title: Exemple sqL intégré Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294170"
---
# <a name="embedded-sql-example"></a>Exemple Embedded SQL
Le code suivant est un programme SQL simple intégré, écrit en C. Le programme illustre bon nombre, mais pas tous, des techniques SQL intégrées. Le programme invite l’utilisateur pour un numéro de commande, récupère le numéro du client, le vendeur et l’état de la commande, et affiche les informations récupérées sur l’écran.  
  
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
  
 Notez ce qui suit au sujet de ce programme :  
  
-   **Variables hôtes** Les variables hôtes sont déclarées dans une section jointe par les mots clés **BEGIN DECLARE SECTION** et END DECLARE **SECTION.** Chaque nom variable hôte est préfixé par un côlon (:) lorsqu’il apparaît dans une déclaration SQL intégrée. Le côlon permet au précompiler de distinguer entre les variables d’hôte et les objets de base de données, tels que les tables et les colonnes, qui ont le même nom.  
  
-   **Types de données** Les types de données pris en charge par un DBMS et une langue d’hôte peuvent être très différents. Cela affecte les variables hôtes parce qu’elles jouent un double rôle. D’une part, les variables hôtes sont des variables de programme, déclarées et manipulées par des énoncés linguistiques d’hôte. D’autre part, ils sont utilisés dans les relevés SQL intégrés pour récupérer les données de base de données. S’il n’existe pas de type de langue hôte correspondant à un type de données DBMS, le DBMS convertit automatiquement les données. Cependant, parce que chaque DBMS a ses propres règles et particularités associées au processus de conversion, les types variables hôtes doivent être choisis avec soin.  
  
-   **Traitement des erreurs** Le DBMS signale des erreurs de temps d’exécution au programme d’applications par l’entremise d’une zone de communications SQL, ou SQLCA. Dans l’exemple de code précédent, la première déclaration SQL intégrée est INCLUDE SQLCA. Cela indique au précompiler d’inclure la structure SQLCA dans le programme. Cela est nécessaire chaque fois que le programme traitera les erreurs retournées par le DBMS. LE WHENEVER... L’instruction GOTO indique au précompiler de générer du code de traitement des erreurs qui branche une étiquette spécifique lorsqu’une erreur se produit.  
  
-   **Sélection De Singleton** La déclaration utilisée pour retourner les données est une déclaration unique; c’est-à-dire qu’il ne renvoie qu’une seule série de données. Par conséquent, l’exemple de code ne déclare pas ou n’utilise pas de curseurs.
