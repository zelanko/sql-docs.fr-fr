---
title: Utilisation des curseurs (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc53253c93f5f52c6bbe00941eadbf14b65d5f64
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68206823"
---
# <a name="using-cursors-odbc"></a>Utilisation de curseurs (ODBC)
  ODBC prend en charge un modèle de curseur qui autorise :  
  
-   plusieurs types de curseurs ;  
  
-   le défilement et le positionnement dans un curseur ;  
  
-   plusieurs options de concurrence ;  
  
-   des mises à jour positionnées.  
  
 Les applications ODBC ont rarement besoin de déclarer ou d'ouvrir des curseurs. De même, elles utilisent peu souvent les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] relatives aux curseurs. ODBC ouvre automatiquement un curseur pour chaque jeu de résultats retourné par une instruction SQL. Les caractéristiques des curseurs sont contrôlées par des attributs d’instruction définis avec [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) avant l’exécution de l’instruction SQL. Les fonctions de l'API ODBC relatives au traitement des jeux de résultats prennent en charge l'ensemble des fonctionnalités des curseurs, y compris l'extraction, le défilement et les mises à jour positionnées.  
  
 Le tableau suivant compare la façon dont les scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] et les applications ODBC utilisent les curseurs.  
  
|Action|[!INCLUDE[tsql](../../includes/tsql-md.md)]|ODBC|  
|------------|------------------------|----------|  
|Définir le comportement du curseur|Spécifier par le biais de paramètres DECLARE CURSOR|Définir des attributs de curseur à l’aide de [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)|  
|Ouvrir un curseur|DÉCLARER le curseur ouvert *cursor_name*|**SQLExecDirect** ou **SQLExecute**|  
|Extraire des lignes|FETCH|**SQLFetch** ou [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)|  
|Mise à jour positionnée|Clause WHERE CURRENT OF sur UPDATE ou DELETE|**SQLSetPos**|  
|Fermer un curseur|FERMER *CURSOR_NAME* libérer|[SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)|  
  
 Les curseurs côté serveur implémentés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prennent en charge les fonctionnalités du modèle de curseur ODBC. Le pilote [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client utilise des curseurs côté serveur pour prendre en charge les fonctionnalités de curseur de l'API ODBC.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment les curseurs sont implémentés](implementation/how-cursors-are-implemented.md)  
  
-   [Types de curseurs](cursor-types.md)  
  
-   [Comportements des curseurs](cursor-behaviors.md)  
  
-   [Propriétés de curseur](properties/cursor-properties.md)  
  
-   [Détails de programmation de curseur &#40;ODBC&#41;](programming/cursor-programming-details-odbc.md)  
  
-   [Défilement et récupération (fetch) de lignes](../native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [Mises à jour positionnées &#40;ODBC&#41;](positioned-updates-odbc.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;&#41;ODBC](../native-client/odbc/sql-server-native-client-odbc.md)   
 [FERMER &#40;&#41;Transact-SQL](/sql/t-sql/language-elements/close-transact-sql)   
 [Curseurs](../../relational-databases/cursors.md)   
 [LIBÉRER &#40;&#41;Transact-SQL](/sql/t-sql/language-elements/deallocate-transact-sql)   
 [DÉCLARER un curseur &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql)   
 [RÉCUPÉRATION &#40;&#41;Transact-SQL](/sql/t-sql/language-elements/fetch-transact-sql)   
 [OPEN &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/open-transact-sql)  
  
  
