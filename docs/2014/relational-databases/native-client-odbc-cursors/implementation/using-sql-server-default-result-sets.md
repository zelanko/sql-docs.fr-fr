---
title: Utilisation d’SQL Server jeux de résultats par défaut | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d7101cf4775e5280c22cc27ecae009410d231d5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62511684"
---
# <a name="using-sql-server-default-result-sets"></a>Utilisation de jeux de résultats SQL Server par défaut
  Les attributs de curseur ODBC par défaut sont les suivants :  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Chaque fois que ces attributs sont définis sur leurs valeurs par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] défaut, le pilote ODBC native [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client utilise un jeu de résultats par défaut. Les jeux de résultats par défaut peuvent être utilisés pour toute instruction SQL prise en charge par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et s'avèrent la méthode de transfert la plus efficace d'un jeu de résultats entier au client.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]a introduit la prise en charge de MARS (Multiple Active Result Sets); les applications peuvent désormais avoir plusieurs jeux de résultats par défaut actifs par connexion. MARS n'est pas activé par défaut.  
  
 Avant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], les jeux de résultats par défaut ne prenaient pas en charge plusieurs instructions actives sur la même connexion. Une fois qu'une instruction SQL était exécutée sur une connexion, le serveur n'acceptait pas de commandes (sauf une demande d'annulation du reste du jeu de résultats) du client sur cette connexion tant que toutes les lignes du jeu de résultats n'avaient pas été traitées. Pour annuler le reste d’un jeu de résultats partiellement traité, appelez [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) ou [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) avec le paramètre *fOption* défini sur SQL_CLOSE. Pour terminer un jeu de résultats partiellement traité et tester la présence d’un autre jeu de résultats, appelez [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md). Si une application ODBC tente une commande sur un handle de connexion avant qu’un jeu de résultats par défaut ait été complètement traité, l’appel génère SQL_ERROR et un appel à **SQLGetDiagRec** retourne :  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les curseurs sont implémentés](how-cursors-are-implemented.md)  
  
  
