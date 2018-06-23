---
title: Lots d’instructions | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- statements [ODBC], batches
- batches [ODBC]
- ODBC applications, statements
- multiple statements, batches
- SQLMoreResults function
- SQLExecDirect function
ms.assetid: 057d7c1c-1428-4780-9447-a002ea741188
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2ebe40de44765e974a63fc0eb6282ae0b979b607
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141275"
---
# <a name="batches-of-statements"></a>Lots d'instructions
  Un lot de [!INCLUDE[tsql](../../../includes/tsql-md.md)] instructions contient plusieurs instructions, séparées par un point-virgule ( ;), intégrées dans une chaîne unique passée à **SQLExecDirect** ou [fonction SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360). Exemple :  
  
```  
SQLExecDirect(hstmt,   
    "SELECT * FROM Authors; SELECT * FROM Titles",  
    SQL_NTS);  
```  
  
 Les lots peuvent se révéler plus efficaces que la soumission des instructions séparément car le trafic réseau est souvent réduit. Utilisez [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) pour vous positionner sur le prochain jeu de résultats lorsque s’est terminé avec le jeu de résultats actuel.  
  
 Les lots peuvent toujours être utilisés lorsque les attributs de curseur ODBC sont définis sur les valeurs par défaut d'un curseur avant uniquement en lecture seule avec une taille d'ensemble de lignes de 1.  
  
 Si un lot est exécuté lors de l'utilisation de curseurs côté serveur contre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le curseur côté serveur est converti implicitement en un jeu de résultats par défaut. **SQLExecDirect** ou **SQLExecute** retourne SQL_SUCCESS_WITH_INFO et un appel à **SQLGetDiagRec** retourne :  
  
```  
szSqlState = "01S02", pfNativeError = 0  
szErrorMsg = "[Microsoft][SQL Server Native Server Native Client]Cursor type changed."  
```  
  
## <a name="see-also"></a>Voir aussi  
 [L’exécution d’instructions &#40;ODBC&#41;](executing-statements-odbc.md)  
  
  