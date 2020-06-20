---
title: Utiliser la liaison d’ensemble de lignes (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
author: rothja
ms.author: jroth
ms.openlocfilehash: deb2c179cea2d0ea7c97385d56320075061f0686
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85018898"
---
# <a name="use-rowset-binding-odbc"></a>Utiliser une liaison d'ensembles de lignes (ODBC)
    
### <a name="to-use-column-wise-binding"></a>Pour utiliser la liaison selon les colonnes  
  
1.  Pour chaque colonne dépendante, procédez comme suit :  
  
    -   Allouez un tableau de R (ou plus) tampons de colonnes pour stocker les valeurs des données. R désigne le nombre de lignes dans l'ensemble de lignes.  
  
    -   Allouez éventuellement un tableau de R (ou plus) tampons de colonnes pour le stockage des longueurs des données.  
  
    -   Appelez [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) pour lier la valeur de données de la colonne et les tableaux de longueur des données à la colonne de l'ensemble de lignes.  
  
2.  Appelez [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) pour définir les attributs suivants :  
  
    -   Définissez SQL_ATTR_ROW_ARRAY_SIZE sur le nombre de lignes dans l'ensemble de lignes (R).  
  
    -   Définissez SQL_ATTR_ROW_BIND_TYPE sur SQL_BIND_BY_COLUMN.  
  
    -   Définissez l'attribut SQL_ATTR_ROWS_FETCHED_PTR de sorte qu'il pointe vers une variable SQLUINTEGER contenant le nombre de lignes extraites.  
  
    -   Définissez SQL_ATTR_ROWS_STATUS_PTR de sorte qu'il pointe vers un tableau [R] de variables SQLUSSMALLINT contenant les indicateurs d'état de ligne.  
  
3.  Exécution de l'instruction.  
  
4.  Chaque appel à [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) ou [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) extrait des lignes R et transfère les données dans les colonnes dépendantes.  
  
### <a name="to-use-row-wise-binding"></a>Pour utiliser la liaison selon les lignes  
  
1.  Allouez un tableau [R] de structures, où R correspond au nombre de lignes dans l'ensemble de lignes. La structure dispose d'un élément pour chaque colonne, et chaque élément a deux parties :  
  
    -   La première partie est une variable de type de données approprié destinée à contenir les données de la colonne.  
  
    -   La deuxième est une variable SQLINTEGER qui affiche l'indicateur d'état de la colonne.  
  
2.  Appelez [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) pour définir les attributs suivants :  
  
    -   Définissez SQL_ATTR_ROW_ARRAY_SIZE sur le nombre de lignes dans l'ensemble de lignes (R).  
  
    -   Définissez SQL_ATTR_ROW_BIND_TYPE conformément à la taille de la structure allouée à l'étape 1.  
  
    -   Définissez l'attribut SQL_ATTR_ROWS_FETCHED_PTR de sorte qu'il pointe vers une variable SQLUINTEGER contenant le nombre de lignes extraites.  
  
    -   Définissez SQL_ATTR_PARAMS_STATUS_PTR de sorte qu'il pointe vers un tableau [R] de variables SQLUSSMALLINT contenant les indicateurs d'état de ligne.  
  
3.  Pour chaque colonne dans le jeu de résultats, appelez [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) pour diriger les pointeurs de valeur de données et de longueur de données de colonne vers leurs variables dans le premier élément du tableau de structures alloué à l'étape 1.  
  
4.  Exécution de l'instruction.  
  
5.  Chaque appel à [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) ou [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) extrait des lignes R et transfère les données dans les colonnes dépendantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives à l’utilisation des curseurs &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md)   
 [Comment les curseurs sont implémentés](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)   
 [Utiliser des curseurs &#40;ODBC&#41;](use-cursors-odbc.md)  
  
  
