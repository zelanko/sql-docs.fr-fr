---
title: Taille de l’ensemble de rames cursur (fr) Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7f799722bfae35a714e740691e2cdc53e3155063
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302865"
---
# <a name="cursor-rowset-size"></a>Taille de l'ensemble de lignes d'un curseur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les curseurs ODBC peuvent extraire plusieurs lignes à la fois. Ils peuvent récupérer plusieurs rangées dans chaque appel à **SQLFetch** ou [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Lorsque vous utilisez une base de données client/serveur, telle que Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il est plus efficace d'extraire plusieurs lignes à la fois. Le nombre de rangées retournées sur un aller chercher est appelé la taille de la ligne et est spécifié en utilisant le SQL_ATTR_ROW_ARRAY_SIZE de [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
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
  
 Lorsque la liaison de la colonne ou de la ligne est utilisée, chaque appel à **SQLFetch** ou **SQLFetchScroll** remplit les tableaux de limite avec les données du rowset récupéré.  
  
 [SQLGetData](../../../relational-databases/native-client-odbc-api/sqlgetdata.md) peut également être utilisé pour récupérer les données de colonne d’un curseur de bloc. Parce que **SQLGetData** fonctionne une rangée à la fois, **SQLSetPos** doit être appelé à définir une ligne spécifique dans le rowset que la ligne actuelle avant d’appeler **SQLGetData**.  
  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote Native Client ODBC offre une optimisation à l’aide de rames pour récupérer un ensemble de résultats entiers rapidement. Pour utiliser cette optimisation, définissez les attributs du curseur à leurs défauts (avant seulement, lu seulement, taille de rame 1) au moment **où SQLExecDirect** ou **SQLExecute** est appelé. Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote Native Client ODBC met en place un ensemble de résultats par défaut. Cette approche est plus efficace que les curseurs côté serveur lors du transfert de résultats au client sans défilement. Après avoir exécuté l'instruction, augmentez la taille de l'ensemble de lignes et utilisez la liaison selon les colonnes ou la liaison selon les lignes. Cela permet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] d’utiliser un résultat par défaut défini pour envoyer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des lignes de résultat efficacement au client, tandis que le pilote Native Client ODBC tire continuellement des rangées des tampons réseau sur le client.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de curseur](../../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
  
