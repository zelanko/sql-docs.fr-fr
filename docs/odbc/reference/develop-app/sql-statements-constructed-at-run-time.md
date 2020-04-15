---
title: Déclarations SQL construites à l’heure de course (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- run time constructed SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], building at run time
ms.assetid: f6554486-d49c-436a-82e3-4c158d26acd8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 795335be2a2a3aab1be6dac26bf6d213161fe42e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301970"
---
# <a name="sql-statements-constructed-at-run-time"></a>Construction d’instructions SQL au moment de l’exécution
Les applications qui effectuent une analyse ad hoc construisent généralement des énoncés SQL au moment de l’exécution. Par exemple, une feuille de calcul peut permettre à un utilisateur de sélectionner des colonnes à partir desquelles récupérer des données :  
  
```  
// SQL_Statements_Constructed_at_Run_Time.cpp  
#include <windows.h>  
#include <stdio.h>  
#include <sqltypes.h>  
  
int main() {  
   SQLCHAR *Statement = 0, *TableName = 0;  
   SQLCHAR **TableNamesArray, **ColumnNamesArray = 0;  
   BOOL *ColumnSelectedArray = 0;  
   BOOL  CommaNeeded;  
   SQLSMALLINT i = 0, NumColumns = 0;  
  
   // Use SQLTables to build a list of tables (TableNamesArray[]). Let the  
   // user select a table and store the selected table in TableName.  
  
   // Use SQLColumns to build a list of the columns in the selected table  
   // (ColumnNamesArray). Set NumColumns to the number of columns in the  
   // table. Let the user select one or more columns and flag these columns  
   // in ColumnSelectedArray[].  
  
   // Build a SELECT statement from the selected columns.  
   CommaNeeded = FALSE;  
   Statement = (SQLCHAR*)malloc(8);  
   strcpy_s((char*)Statement, 8, "SELECT ");  
  
   for (i = 0 ; i = NumColumns ; i++) {  
      if (ColumnSelectedArray[i]) {  
         if (CommaNeeded)  
            strcat_s((char*)Statement, sizeof(Statement), ",");  
         else  
            CommaNeeded = TRUE;  
         strcat_s((char*)Statement, sizeof(Statement), (char*)ColumnNamesArray[i]);  
      }  
   }  
  
   strcat_s((char*)Statement, 15, " FROM ");  
   // strcat_s((char*)Statement, 100, (char*)TableName);  
  
   // Execute the statement . It will be executed once, do not prepare it.  
   // SQLExecDirect(hstmt, Statement, SQL_NTS);  
}  
```  
  
 Une autre catégorie d’applications qui construit généralement des relevés SQL au moment de l’exécution sont les environnements de développement d’applications. Cependant, les déclarations qu’ils construisent sont codées en dur dans l’application qu’ils construisent, où elles peuvent généralement être optimisées et testées.  
  
 Les applications qui construisent des relevés SQL à l’heure d’exécution peuvent offrir une flexibilité énorme à l’utilisateur. Comme on peut le voir dans l’exemple précédent, qui n’a même pas soutenu des opérations communes telles que les clauses **WHERE,** **ORDER BY** clauses, ou joint, la construction de déclarations SQL à l’heure d’exécution est beaucoup plus complexe que les déclarations de codage dur. De plus, le test de telles applications est problématique parce qu’elles peuvent construire un nombre arbitraire de relevés SQL.  
  
 Un inconvénient potentiel de la construction des déclarations SQL au moment de l’exécution est qu’il faut beaucoup plus de temps pour construire une déclaration que d’utiliser une déclaration codée en dur. Heureusement, c’est rarement une préoccupation. Ces applications ont tendance à être intensives à interface utilisateur, et le temps que passe l’application à la construction des relevés SQL est généralement faible par rapport au temps que l’utilisateur passe à entrer des critères.
