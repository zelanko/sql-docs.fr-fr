---
title: Construire des déclarations SQL pour les curseurs (fr) Microsoft Docs
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
ms.openlocfilehash: e0e422be747c2b47dacb1feb97ba6c00fa1131fc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291419"
---
# <a name="constructing-sql-statements-for-cursors"></a>Construction d'instructions SQL pour les curseurs
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote Native Client ODBC utilise des curseurs de serveur pour implémenter la fonctionnalité du curseur définie dans les spécifications ODBC. Une application ODBC contrôle le comportement du curseur en utilisant [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) pour définir différents attributs de déclaration. Voici les attributs et leurs valeurs par défaut.  
  
|Attribut|Default|  
|---------------|-------------|  
|SQL_ATTR_CONCURRENCY|SQL_CONCUR_READ_ONLY|  
|SQL_ATTR_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE|SQL_NONSCROLLABLE|  
|SQL_ATTR_CURSOR_SENSITIVITY|SQL_UNSPECIFIED|  
|SQL_ATTR_ROW_ARRAY_SIZE|1|  
  
 Lorsque ces options sont réglées à leur défaut au moment [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’exécution d’une déclaration SQL, le pilote native Client ODBC n’utilise pas de curseur serveur pour implémenter l’ensemble de résultats; au lieu de cela, il utilise un ensemble de résultat par défaut. Si l’une de ces options est modifiée par défaut au moment [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’exécution d’une déclaration SQL, le chauffeur native ODBC tente d’utiliser un curseur serveur pour implémenter l’ensemble de résultats.  
  
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
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], si une instruction SQL qui remplit l'une de ces conditions est exécutée avec un curseur côté serveur, celui-ci est converti implicitement en un jeu de résultats par défaut. Après le retour **de SQLExecDirect** ou **SQLExecute** SQL_SUCCESS_WITH_INFO, les attributs du curseur seront remis à leurs paramètres par défaut.  
  
 Les instructions SQL qui n'appartiennent à aucune des catégories précitées peuvent être exécutées avec tout paramètre d'attribut d'instruction ; elles fonctionnent aussi bien avec un jeu de résultats par défaut qu'avec un curseur côté serveur.  
  
## <a name="errors"></a>Erreurs  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 et versions ultérieures, toute tentative d'exécution d'une instruction qui produit plusieurs jeux de résultats génère SQL_SUCCESS_WITH INFO et le message suivant :  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 Les applications ODBC qui reçoivent ce message peuvent appeler [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) pour déterminer les paramètres actuels du curseur.  
  
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
 [Exécution des requêtes &#40;&#41;ODBC](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
