---
title: Taille de l’ensemble de lignes du curseur | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5188b87e91725e2d0e86337261fc1f915189ff19
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73784244"
---
# <a name="cursor-rowset-size"></a>Taille de l'ensemble de lignes d'un curseur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les curseurs ODBC peuvent extraire plusieurs lignes à la fois. Ils peuvent récupérer plusieurs lignes dans chaque appel à **SQLFetch** ou [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Lorsque vous utilisez une base de données client/serveur, telle que Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il est plus efficace d'extraire plusieurs lignes à la fois. Le nombre de lignes retournées sur une extraction est appelé la taille de l’ensemble de lignes et est spécifié à l’aide de la SQL_ATTR_ROW_ARRAY_SIZE de [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 Les curseurs dont la taille de l'ensemble de lignes est supérieure à 1 sont appelés « curseurs de bloc ».  
  
 Deux options s'offrent à vous pour lier des colonnes de jeu de résultats pour des curseurs de bloc :  
  
-   Liaison selon les colonnes  
  
     Chaque colonne est liée à un tableau de variables. Chaque tableau possède un nombre d'éléments égal à la taille de l'ensemble de lignes.  
  
-   Liaison selon les lignes  
  
     Un tableau est construit à l'aide de structures qui contiennent les données et d'indicateurs pour toutes les colonnes d'une ligne. Le tableau possède un nombre de structures égal à la taille de l'ensemble de lignes.  
  
 Lorsque l’une des liaisons selon les colonnes ou les lignes est utilisée, chaque appel à **SQLFetch** ou **SQLFetchScroll** remplit les tableaux liés avec les données de l’ensemble de lignes récupéré.  
  
 [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) peut également être utilisé pour récupérer des données de colonne à partir d’un curseur de bloc. Comme **SQLGetData** travaille une ligne à la fois, **SQLSetPos** doit être appelé pour définir une ligne spécifique dans l’ensemble de lignes comme ligne actuelle avant d’appeler **SQLGetData**.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client offre une optimisation à l’aide d’ensembles de lignes pour récupérer rapidement un jeu de résultats entier. Pour utiliser cette optimisation, définissez les attributs de curseur à leurs valeurs par défaut (avant uniquement, lecture seule, taille de l’ensemble de lignes = 1) au moment de l’appel de **SQLExecDirect** ou **SQLExecute** . Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client définit un jeu de résultats par défaut. Cette approche est plus efficace que les curseurs côté serveur lors du transfert de résultats au client sans défilement. Après avoir exécuté l'instruction, augmentez la taille de l'ensemble de lignes et utilisez la liaison selon les colonnes ou la liaison selon les lignes. Cela permet à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] d’utiliser un jeu de résultats par défaut pour envoyer efficacement des lignes de résultat au client, tandis que le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client extrait en continu des lignes des tampons réseau sur le client.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de curseur](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
