---
title: Définir les options de curseur (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 60b97e8b52d985aeb9ba97f95e39c5e94d3188fa
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009457"
---
# <a name="set-cursor-options-odbc"></a>Définir des options de curseur (ODBC)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Pour définir des options de curseur, appelez [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) pour définir ou [SQLGetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) afin d’afficher les options d’instruction qui contrôlent le comportement du curseur.  
  
|*Attribut*|Spécifie|  
|-----------------|---------------|  
|SQL_ATTR_CURSOR_TYPE|Type de curseur avant uniquement, statique, dynamique ou de jeu de clés|  
|SQL_ATTR_CONCURRENCY|Option de contrôle concurrentiel de lecture seule, verrouillage, optimiste avec horodateurs ou optimiste avec valeurs|  
|SQL_ATTR_ROW_ARRAY_SIZE|Nombre de lignes extraites à chaque extraction|  
|SQL_ATTR_CURSOR_SENSITIVITY|Curseur qui affiche ou masque les mises à jour des lignes de curseur effectuées par d'autres connexions|  
|SQL_ATTR_CURSOR_SCROLLABLE|Curseur qu'il est possible de faire défiler vers l'avant et vers l'arrière|  
  
 Les valeurs par défaut de ces attributs (avant uniquement, lecture seule, taille d'ensemble de lignes de 1) n'utilisent pas de curseurs côté serveur. Pour utiliser des curseurs côté serveur, au moins l'un de ces attributs doit être défini à une valeur autre que la valeur par défaut et l'instruction qui est exécutée doit être une instruction SELECT unique ou une procédure stockée qui contient une instruction SELECT unique. Lors de l'utilisation de curseurs côté serveur, les instructions SELECT ne peuvent pas utiliser de clauses non prises en charge par les curseurs côté serveur : COMPUTE, COMPUTE BY, FOR BROWSE et INTO.  
  
 Vous pouvez contrôler le type de curseur utilisé en définissant SQL_ATTR_CURSOR_TYPE et SQL_ATTR_CONCURRENCY, ou en définissant SQL_ATTR_CURSOR_SENSITIVITY et SQL_ATTR_CURSOR_SCROLLABLE. Vous ne devez pas combiner les deux méthodes de spécification de comportement du curseur.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant alloue un descripteur d'instruction, définit un type de curseur dynamique avec accès concurrentiel optimiste de contrôle de version de ligne, puis exécute une instruction SELECT.  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant alloue un descripteur d'instruction, définit un curseur déroulant SENSITIVE, puis exécute une instruction SELECT.  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives à l’exécution de requêtes &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
