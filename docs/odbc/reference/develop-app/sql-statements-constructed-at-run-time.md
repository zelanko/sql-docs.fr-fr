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
manager: craigg
ms.openlocfilehash: 0573851ee93bda4aa33e8645148cf2ee66200bee
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47848097"
---
# <a name="sql-statements-constructed-at-run-time"></a>Construction d’instructions SQL au moment de l’exécution
Les applications qui effectuent des analyses ad hoc couramment construisent des instructions SQL en cours d’exécution. Par exemple, une feuille de calcul peut autoriser un utilisateur de sélectionner les colonnes à partir duquel récupérer des données :  
  
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
  
 Une autre classe d’applications couramment construit des instructions SQL en cours d’exécution sont des environnements de développement d’application. Toutefois, les instructions qu’ils construisent sont codées en dur dans l’application, qu'ils créent, où ils peuvent généralement être optimisés et testés.  
  
 Les applications qui génèrent des instructions SQL en cours d’exécution peuvent fournir une flexibilité considérable à l’utilisateur. Comme illustré dans l’exemple précédent, ce qui ne pas encore prennent en charge des opérations courantes telles que **où** clauses, **ORDER BY** clauses ou des jointures, construction d’instructions SQL en cours d’exécution est infiniment plus complexe que les instructions de codage en dur. En outre, ces applications de test est problématique, car leur permet de créer un nombre arbitraire d’instructions SQL.  
  
 Un inconvénient potentiel de construction d’instructions SQL en cours d’exécution est qu’il prend beaucoup plus de temps pour construire une instruction d’utiliser une instruction codées en dur. Heureusement, il est rarement une préoccupation. Ces applications ont tendance à être intensif de l’interface utilisateur et le temps passé par l’application construction d’instructions SQL est généralement faible par rapport à l’heure de critères d’entrée passé par l’utilisateur.
