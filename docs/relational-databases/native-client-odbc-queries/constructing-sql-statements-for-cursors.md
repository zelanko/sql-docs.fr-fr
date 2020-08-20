---
description: Construction d'instructions SQL pour les curseurs
title: Construction d’instructions SQL pour les curseurs | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], statement construction
- ODBC applications, cursors
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
- statements [ODBC], cursors
ms.assetid: 134003fd-9c93-4f5c-a988-045990933b80
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a67f2a7ed3d01ee3a98356efc4c15cf2865ee154
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470389"
---
# <a name="constructing-sql-statements-for-cursors"></a>Construction d'instructions SQL pour les curseurs
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client utilise des curseurs de serveur pour implémenter la fonctionnalité de curseur définie dans la spécification ODBC. Une application ODBC contrôle le comportement des curseurs à l’aide de [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) pour définir différents attributs d’instruction. Voici les attributs et leurs valeurs par défaut.  
  
|Attribut|Default|  
|---------------|-------------|  
|SQL_ATTR_CONCURRENCY|SQL_CONCUR_READ_ONLY|  
|SQL_ATTR_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE|SQL_NONSCROLLABLE|  
|SQL_ATTR_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_ATTR_ROW_ARRAY_SIZE|1|  
  
 Lorsque ces options sont définies sur leurs valeurs par défaut au moment de l’exécution d’une instruction SQL, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client n’utilise pas de curseur côté serveur pour implémenter le jeu de résultats ; à la place, il utilise un jeu de résultats par défaut. Si l’une de ces options est modifiée par rapport aux valeurs par défaut au moment de l’exécution d’une instruction SQL, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC de native client tente d’utiliser un curseur côté serveur pour implémenter le jeu de résultats.  
  
 Les jeux de résultats par défaut prennent en charge toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. Il n'y a pas de restrictions concernant les types d'instructions SQL qui peuvent être exécutés lors de l'utilisation d'un jeu de résultats par défaut.  
  
 Les curseurs côté serveur ne prennent pas en charge toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)]. Les curseurs côté serveur ne prennent pas en charge les instructions SQL qui génèrent plusieurs jeux de résultats.  
  
 Les types d'instructions suivants ne sont pas pris en charge par les curseurs côté serveur :  
  
-   Lots  
  
     Les instructions SQL construites à partir de plusieurs instructions SQL SELECT individuelles, par exemple :  
  
    ```  
    SELECT * FROM Authors; SELECT * FROM Titles  
    ```  
  
-   Procédures stockées avec plusieurs instructions SELECT  
  
     Instructions SQL qui exécutent une procédure stockée contenant plusieurs instructions SELECT. Cela inclut les instructions SELECT qui remplissent des paramètres ou des variables.  
  
-   Mots clés  
  
     Instructions SQL contenant les mots clés FOR BROWSE ou INTO.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si une instruction SQL qui remplit l'une de ces conditions est exécutée avec un curseur côté serveur, celui-ci est converti implicitement en un jeu de résultats par défaut. Une fois que **SQLExecDirect** ou **SQLExecute** a renvoyé SQL_SUCCESS_WITH_INFO, les paramètres par défaut des attributs de curseur sont redéfinis.  
  
 Les instructions SQL qui n'appartiennent à aucune des catégories précitées peuvent être exécutées avec tout paramètre d'attribut d'instruction ; elles fonctionnent aussi bien avec un jeu de résultats par défaut qu'avec un curseur côté serveur.  
  
## <a name="errors"></a>Erreurs  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 et versions ultérieures, toute tentative d'exécution d'une instruction qui produit plusieurs jeux de résultats génère SQL_SUCCESS_WITH INFO et le message suivant :  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 Les applications ODBC qui reçoivent ce message peuvent appeler [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) pour déterminer les paramètres de curseur actuels.  
  
 Toute tentative d'exécution d'une procédure avec plusieurs instructions SELECT lors de l'utilisation de curseurs côté serveur génère l'erreur suivante :  
  
```  
SqlState: 42000  
pfNative: 16937  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               A server cursor is not allowed on a stored procedure  
               with more than one SELECT statement in it. Use a  
               default result set or client cursor.  
```  
  
 Toute tentative d'exécution d'un lot avec plusieurs instructions SELECT lors de l'utilisation de curseurs côté serveur génère l'erreur suivante :  
  
```  
SqlState: 42000  
pfNative: 16938  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               sp_cursoropen. The statement parameter can only  
               be a single SELECT statement or a single stored   
               procedure.  
```  
  
 Les applications ODBC qui reçoivent ces erreurs doivent réinitialiser tous les attributs d'instructions de curseur à leurs valeurs par défaut avant d'essayer d'exécuter l'instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de requêtes &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
