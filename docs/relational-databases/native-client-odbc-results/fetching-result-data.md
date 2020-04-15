---
title: Obtenir des données sur les résultats (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLFetchScroll function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- data types [ODBC], fetching
- SQLBindCol function
- result sets [ODBC], fetching
- fetching [ODBC]
- ODBC data types, fetching
- SQLFetch function
- SQL Server Native Client ODBC driver, data types
- SQLGetData function
ms.assetid: b289c7fb-5017-4d7e-a2d3-19401e9fc4cd
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e1d9fdfcd7bcc4f86afacc75dff5b40b77bb7b2a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304610"
---
# <a name="fetching-result-data"></a>Extraction des données de résultat
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Une application ODBC offre trois options pour l'extraction des données de résultat.  
  
 La première option est basée sur [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md). Avant d’aller chercher l’ensemble de résultats, l’application utilise **SQLBindCol** pour lier chaque colonne dans le résultat réglé à une variable de programme. Une fois que les colonnes ont été liées, le conducteur transfère les données de la ligne actuelle dans les variables liées aux colonnes de jeu de résultat chaque fois que l’application appelle **SQLFetch** ou [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Le pilote gère les conversions de données si la colonne du jeu de résultats et la variable de programme possèdent des types de données différents. Si l’application a SQL_ATTR_ROW_ARRAY_SIZE définie supérieure à 1, elle peut lier les colonnes de résultat à des tableaux de variables, qui seront toutes remplies à chaque appel à **SQLFetchScroll**.  
  
 La deuxième option est basée sur [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). L’application n’utilise pas **SQLBindCol** pour lier les colonnes de jeu de résultats aux variables du programme. Après chaque appel à **SQLFetch**, l’application appelle **SQLGetData** une fois pour chaque colonne dans l’ensemble de résultat. **SQLGetData** demande au conducteur de transférer des données d’une colonne de résultat spécifique à une variable de programme spécifique et spécifie les types de données de la colonne et de la variable. Le pilote peut ainsi convertir des données si la colonne de résultat et la variable de programme possèdent des types de données différents. **Texte**, **ntext**, et les colonnes **d’image** sont généralement trop grandes pour s’adapter dans une variable de programme, mais peuvent encore être récupérés à l’aide **de SQLGetData**. Si le **texte,** **le ntext**, ou les données **d’image** dans la colonne de résultat est plus grand que la variable du programme, **SQLGetData** retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01004 (données de chaîne, droite tronqué). Les appels successifs à **SQLGetData** renvoient des morceaux successifs des données **de texte** ou **d’image.** Lorsque la fin des données est atteinte, **SQLGetData** retourne SQL_SUCCESS. Chaque extraction retourne un jeu de lignes, ou « ensemble de lignes », si SQL_ATTR_ROW_ARRAY_SIZE est supérieur à 1. Avant d’utiliser **SQLGetData**, vous devez d’abord utiliser **SQLSetPos** pour spécifier une ligne spécifique dans le jeu de ligne comme ligne actuelle.  
  
 La troisième option est d’utiliser un mélange de **SQLBindCol** et **SQLGetData**. Une application pourrait, par exemple, lier les dix premières colonnes d’un ensemble de résultats, puis, sur chaque aller chercher, appeler **SQLGetData** trois fois pour récupérer les données à partir de trois colonnes non liées. Cela serait généralement utilisé lorsqu’un ensemble de résultats contient une ou plusieurs colonnes **de texte** ou **d’image.**  
  
 Selon les options de curseur définies pour l’ensemble de résultats, une application peut également utiliser les options de défilement de **SQLFetchScroll** pour faire défiler l’ensemble de résultats.  
  
 L’utilisation excessive de **SQLBindCol** pour lier une colonne de résultat à une variable de programme est coûteuse parce que **SQLBindCol** amène un conducteur D’ODBC à allouer la mémoire. Lorsque vous liez une colonne de résultat à une variable, cette liaison reste en vigueur jusqu’à ce que vous appeliez [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) pour libérer la poignée de déclaration ou appelez [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) avec *fOption* réglé pour SQL_UNBIND. Les liaisons ne sont pas automatiquement annulées à la fin de l'instruction.  
  
 Cette logique vous permet de gérer avec efficacité l'exécution à maintes reprises de la même instruction avec des paramètres différents. Étant donné que l’ensemble de résultats conserve la même structure, vous pouvez lier le jeu de résultat une fois, traiter toutes les instructions SELECT, puis appeler **SQLFreeStmt** avec *fOption* réglé pour SQL_UNBIND après la dernière exécution. Vous ne devriez pas appeler **SQLBindCol** pour lier les colonnes dans un jeu de résultat sans d’abord appeler **SQLFreeStmt** avec *fOption* réglé pour SQL_UNBIND pour libérer les liaisons précédentes.  
  
 Lorsque vous utilisez **SQLBindCol**, vous pouvez soit faire ligne-sage ou colonne-sage liaison. La liaison selon les lignes est un tantinet plus rapide que la liaison selon les colonnes.  
  
 Vous pouvez utiliser **SQLGetData** pour récupérer des données sur une base colonne par colonne au lieu de lier les colonnes de jeu de résultat à l’aide de **SQLBindCol**. Si un ensemble de résultats ne contient que quelques lignes, l’utilisation **de SQLGetData** au lieu de **SQLBindCol** est plus rapide; autrement, **SQLBindCol** donne la meilleure performance. Si vous ne mettez pas toujours les données dans le même ensemble de variables, vous devriez utiliser **SQLGetData** au lieu de rebinding constamment. Vous ne pouvez utiliser **SQLGetData** que sur les colonnes qui figurent dans la liste de sélections après que toutes les colonnes sont liées à **SQLBindCol**. La colonne doit également apparaître après toutes les colonnes sur lesquelles vous avez déjà utilisé **SQLGetData**.  
  
 Les fonctions ODBC qui traitent du déplacement des données dans ou hors des variables du programme, telles que **SQLGetData**, **SQLBindCol**, et [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), prennent en charge la conversion implicite de type de données. Par exemple, si une application lie une colonne d'entiers à une variable de programme de chaîne de caractères, le pilote convertit automatiquement les données d'entier en caractère avant de les insérer dans la variable de programme.  
  
 La conversion de données dans les applications doit être réduite. À moins que la conversion de données ne soit nécessaire pour le traitement pris en charge par l'application, les applications doivent lier les colonnes et les paramètres à des variables de programme du même type de données. En revanche, si les données doivent être converties d'un type à un autre, il est plus efficace de confier la conversion au pilote plutôt que de l'effectuer dans l'application. Normalement, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client se contente de transférer directement les données des tampons réseau vers les variables de l'application. En confiant la conversion des données au pilote, vous forcez ce dernier à mettre les données en mémoire tampon et à les convertir au moyen de cycles processeur.  
  
 Les variables du programme devraient être suffisamment importantes pour contenir les données transférées à partir d’une colonne, à l’exception du **texte,** **du ntext**, et des données **d’image.** Si une application tente d'extraire les données d'un jeu de résultats et de les placer dans une variable trop petite pour les contenir, le pilote émet un avertissement. Cette opération contraint le pilote à allouer de la mémoire pour le message et le pilote et l'application doivent tous les deux utiliser des cycles processeur pour traiter le message et gérer les erreurs. L'application doit soit allouer une variable suffisamment grande pour accueillir les données extraites, soit faire appel à la fonction SUBSTRING dans la liste de sélection pour réduire la taille de la colonne au sein du jeu de résultats.  
  
 Soyez vigilant lorsque vous utilisez SQL_C_DEFAULT pour définir le type de la variable C. SQL_C_DEFAULT spécifie que le type de la variable C correspond au type de données SQL de la colonne ou du paramètre. Si SQL_C_DEFAULT est spécifiée pour une colonne **ntext**, **nchar**ou **nvarchar,** les données Unicode sont retournées à l’application. Ceci peut entraîner divers problèmes si l'application n'a pas été codée pour gérer des données Unicode. Les mêmes types de problèmes peuvent se produire avec le type de données **unique d’identification** (SQL_GUID).  
  
 **texte**, **ntext**, et les données **d’image** est généralement trop grande pour s’adapter à une variable de programme unique, et est généralement traitée avec **SQLGetData** au lieu de **SQLBindCol**. Lors de l’utilisation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de curseurs serveur, le pilote Native Client ODBC est optimisé pour ne pas transmettre les données pour le **texte**non lié, **ntext**, ou colonnes **d’image** au moment où la ligne est récupérée. Le **texte**, **ntext**, ou les données **d’image** n’est pas réellement récupéré à partir du serveur jusqu’à ce que l’application émet **SQLGetData** pour la colonne.  
  
 Cette optimisation peut être appliquée aux applications de sorte qu’aucun **texte,** **ntext**, ou des données **d’image** n’est affiché pendant qu’un utilisateur fait défiler de haut en bas un curseur. Une fois que l’utilisateur sélectionne une ligne, l’application peut appeler **SQLGetData** pour récupérer le **texte,** **ntext**, ou les données **d’image.** Cela permet d’économiser la transmission du **texte,** **du ntext**, ou des données **d’image** pour l’une des lignes que l’utilisateur ne sélectionne pas et peut enregistrer la transmission de très grandes quantités de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Résultats de traitement &#40;&#41;ODBC](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
