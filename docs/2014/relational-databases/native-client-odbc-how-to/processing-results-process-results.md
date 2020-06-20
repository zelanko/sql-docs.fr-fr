---
title: Traiter les résultats (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
author: rothja
ms.author: jroth
ms.openlocfilehash: 3fddbc96086f13fbc8321f2b3424f1c6c2507df1
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039669"
---
# <a name="process-results-odbc"></a>Traiter des résultats (ODBC)
    
### <a name="to-process-results"></a>Pour traiter des résultats  
  
1.  Récupérez les informations du jeu de résultats.  
  
2.  Si des colonnes dépendantes sont utilisées, pour chaque colonne à lier, appelez [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) pour lier une mémoire tampon de programme à la colonne.  
  
3.  Pour chaque ligne de l'ensemble de résultats :  
  
    -   Appelez [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) pour obtenir la ligne suivante.  
  
    -   Si les colonnes dépendantes sont utilisées, utilisez les données à présent disponibles dans les mémoires tampons des colonnes dépendantes.  
  
    -   Si des colonnes indépendantes sont utilisées, appelez [SQLGetData](../native-client-odbc-api/sqlgetdata.md) une ou plusieurs fois pour obtenir les données pour les colonnes indépendantes après la dernière colonne dépendante. Les appels à `SQLGetData` doivent être dans l’ordre de plus en plus élevé du numéro de colonne.  
  
    -   Appelez plusieurs fois `SQLGetData` pour obtenir des données à partir d'une colonne text ou image.  
  
4.  Quand [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) signale la fin du jeu de résultats en retournant SQL_NO_DATA, appelez [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) pour déterminer si un autre jeu de résultats est disponible.  
  
    -   S'il retourne SQL_SUCCESS, un autre jeu de résultats est disponible.  
  
    -   S'il retourne SQL_NO_DATA, aucun autre jeu de résultats n'est disponible.  
  
    -   S’il retourne SQL_SUCCESS_WITH_INFO ou SQL_ERROR, appelez [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) pour déterminer si la sortie à partir d’une instruction PRINT ou RAISERROR est disponible.  
  
         Si des paramètres d'instruction liés sont utilisés pour les paramètres de sortie ou la valeur de retour d'une procédure stockée, utilisez les données à présent disponibles dans les mémoires tampons de paramètres liés. Par ailleurs, quand des paramètres liés sont utilisés, chaque appel à [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) ou à [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) aura exécuté l’instruction SQL *S* fois, où *S* est le nombre d’éléments présents dans le tableau de paramètres liés. Cela signifie qu’il y aura *S* jeux de résultats à traiter, où chaque jeu de résultats comprend tous les jeux de résultats, les paramètres de sortie et les codes de retour habituellement retournés par une exécution unique de l’instruction SQL.  
  
    > [!NOTE]  
    >  Lorsqu'un jeu de résultats contient des lignes calculées, chaque ligne calculée est rendue disponible comme un jeu de résultats distinct. Ces jeux de résultats calculés sont intercalés au sein des lignes normales et séparent les lignes normales en plusieurs jeux de résultats.  
  
5.  Vous pouvez également appeler [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) avec SQL_UNBIND pour libérer tous les tampons de colonnes liées éventuels.  
  
6.  Si un autre jeu de résultats est disponible, allez à l’étape 1.  
  
> [!NOTE]  
>  Pour annuler le traitement d’un jeu de résultats avant que [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) ne retourne SQL_NO_DATA, appelez [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives au traitement des résultats &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
