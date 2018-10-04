---
title: À l’aide de jeux de résultats par défaut SQL Server | Microsoft Docs
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
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137929"
---
# <a name="using-sql-server-default-result-sets"></a>Utilisation de jeux de résultats SQL Server par défaut
  Les attributs de curseur ODBC par défaut sont les suivants :  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Chaque fois que ces attributs sont définis sur leurs valeurs par défaut, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client utilise un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] par défaut du jeu de résultats. Les jeux de résultats par défaut peuvent être utilisés pour toute instruction SQL prise en charge par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et s'avèrent la méthode de transfert la plus efficace d'un jeu de résultats entier au client.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] introduction du support pour les jeux de résultats actifs multiples (MARS) ; les applications peuvent désormais avoir plus d’un jeu de résultats de la valeur par défaut active par connexion. MARS n'est pas activé par défaut.  
  
 Avant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], les jeux de résultats par défaut ne prenaient pas en charge plusieurs instructions actives sur la même connexion. Une fois qu'une instruction SQL était exécutée sur une connexion, le serveur n'acceptait pas de commandes (sauf une demande d'annulation du reste du jeu de résultats) du client sur cette connexion tant que toutes les lignes du jeu de résultats n'avaient pas été traitées. Pour annuler le reste d’un jeu de résultats partiellement traité, appelez [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) ou [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) avec la *fOption* paramètre défini sur SQL_CLOSE. Pour terminer un jeu de résultats partiellement traité et le test de la présence d’un autre jeu de résultats, appelez [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md). Si une application ODBC tente une commande sur un handle de connexion avant un jeu de résultats par défaut a été entièrement traité, l’appel génère SQL_ERROR et un appel à **SQLGetDiagRec** retourne :  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les curseurs sont implémentés](how-cursors-are-implemented.md)  
  
  
