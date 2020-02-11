---
title: Instructions SQL construites au moment de l’exécution | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8333000c9bb806116244ac6d4f654fa195205868
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107460"
---
# <a name="sql-statements-constructed-at-run-time"></a>Construction d’instructions SQL au moment de l’exécution
Les applications qui effectuent une analyse ad hoc génèrent généralement des instructions SQL au moment de l’exécution. Par exemple, une feuille de calcul peut permettre à un utilisateur de sélectionner des colonnes à partir desquelles récupérer des données :  
  
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
  
 Une autre classe d’applications qui construit habituellement des instructions SQL au moment de l’exécution sont des environnements de développement d’applications. Toutefois, les instructions qu’elles construisent sont codées en dur dans l’application qu’elles génèrent, où elles peuvent généralement être optimisées et testées.  
  
 Les applications qui construisent des instructions SQL au moment de l’exécution peuvent offrir une flexibilité exceptionnelle à l’utilisateur. Comme vous pouvez le voir dans l’exemple précédent, qui n’a même pas pris en charge ces opérations courantes comme les clauses **Where** , les clauses **order by** ou les jointures, la construction d’instructions SQL au moment de l’exécution est beaucoup plus complexe que les instructions de codage irréversible. En outre, le test de telles applications est problématique, car il peut construire un nombre arbitraire d’instructions SQL.  
  
 L’un des inconvénients potentiels de la construction d’instructions SQL au moment de l’exécution est qu’il faut beaucoup plus de temps pour construire une instruction que d’utiliser une instruction codée en dur. Heureusement, cela est rarement un problème. Ces applications ont tendance à être gourmandes en interface utilisateur, et le temps que l’application consacre à construire des instructions SQL est généralement faible par rapport au temps passé par l’utilisateur à entrer des critères.
