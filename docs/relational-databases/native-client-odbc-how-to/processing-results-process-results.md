---
title: Résultats des processus (ODBC) Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: de9adbcc2d89895a4162b5c7f7b2921f024d03e7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300399"
---
# <a name="processing-results---process-results"></a>Traitement des résultats - Traiter les résultats
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Le traitement des résultats d’une demande ODBC consiste d’abord à déterminer les caractéristiques de l’ensemble de résultats, puis à récupérer les données en variables de programme en utilisant [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) ou [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md).  
  
### <a name="to-process-results"></a>Pour traiter des résultats  
  
1.  Récupérez les informations du jeu de résultats.  
  
2.  Si des colonnes dépendantes sont utilisées, pour chaque colonne à lier, appelez [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md) pour lier une mémoire tampon de programme à la colonne.  
  
3.  Pour chaque ligne de l'ensemble de résultats :  
  
    -   Appelez [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) pour obtenir la ligne suivante.  
  
    -   Si les colonnes dépendantes sont utilisées, utilisez les données à présent disponibles dans les mémoires tampons des colonnes dépendantes.  
  
    -   Si des colonnes indépendantes sont utilisées, appelez [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) une ou plusieurs fois pour obtenir les données pour les colonnes indépendantes après la dernière colonne dépendante. Les appels à **SQLGetData** doivent être dans l’ordre croissant des numéros de colonnes.  
  
    -   Appelez plusieurs fois **SQLGetData** pour obtenir des données à partir d'une colonne text ou image.  
  
4.  Quand [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) signale la fin du jeu de résultats en retournant SQL_NO_DATA, appelez [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) pour déterminer si un autre jeu de résultats est disponible.  
  
    -   S'il retourne SQL_SUCCESS, un autre jeu de résultats est disponible.  
  
    -   S'il retourne SQL_NO_DATA, aucun autre jeu de résultats n'est disponible.  
  
    -   S’il retourne SQL_SUCCESS_WITH_INFO ou SQL_ERROR, appelez [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) pour déterminer si la sortie à partir d’une instruction PRINT ou RAISERROR est disponible.  
  
         Si des paramètres d'instruction liés sont utilisés pour les paramètres de sortie ou la valeur de retour d'une procédure stockée, utilisez les données à présent disponibles dans les mémoires tampons de paramètres liés. Par ailleurs, quand des paramètres liés sont utilisés, chaque appel à [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) ou à [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) aura exécuté l’instruction SQL *S* fois, où *S* est le nombre d’éléments présents dans le tableau de paramètres liés. Cela signifie qu’il y aura des ensembles de résultats *S* à traiter, où chaque ensemble de résultats comprend tous les ensembles de résultats, paramètres de sortie, et les codes de retour habituellement retournés par une seule exécution de la déclaration SQL.  
  
    > [!NOTE]  
    >  Lorsqu'un jeu de résultats contient des lignes calculées, chaque ligne calculée est rendue disponible comme un jeu de résultats distinct. Ces jeux de résultats calculés sont intercalés au sein des lignes normales et séparent les lignes normales en plusieurs jeux de résultats.  
  
5.  Vous pouvez également appeler [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) avec SQL_UNBIND pour libérer tous les tampons de colonnes liées éventuels.  
  
6.  Si un autre jeu de résultats est disponible, allez à l’étape 1.  

> [!NOTE]  
>  Pour annuler le traitement d’un jeu de résultats avant que [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) ne retourne SQL_NO_DATA, appelez [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md).  
  
## <a name="see-also"></a>Voir aussi  
[Récupérer l’information sur les ensembles de résultats &#40;&#41;ODBC](../../relational-databases/native-client-odbc-how-to/processing-results-retrieve-result-set-information.md)   
  
  
