---
description: Extraction des données de résultat
title: Extraction des données de résultat | Microsoft Docs
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 97781af1d4bc7dbde4c26f6a64b02ea3024c42aa
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97438264"
---
# <a name="fetching-result-data"></a>Extraction des données de résultat
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Une application ODBC offre trois options pour l'extraction des données de résultat.  
  
 La première option est basée sur [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md). Avant de récupérer le jeu de résultats, l’application utilise **SQLBindCol** pour lier chaque colonne du jeu de résultats à une variable de programme. Une fois les colonnes liées, le pilote transfère les données de la ligne actuelle dans les variables liées aux colonnes de l’ensemble de résultats chaque fois que l’application appelle **SQLFetch** ou [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Le pilote gère les conversions de données si la colonne du jeu de résultats et la variable de programme possèdent des types de données différents. Si l’application a SQL_ATTR_ROW_ARRAY_SIZE défini sur une valeur supérieure à 1, elle peut lier des colonnes de résultats à des tableaux de variables, qui seront tous renseignés sur chaque appel à **SQLFetchScroll**.  
  
 La deuxième option est basée sur [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md). L’application n’utilise pas **SQLBindCol** pour lier des colonnes de jeu de résultats à des variables de programme. Après chaque appel à **SQLFetch**, l’application appelle **SQLGetData** une fois pour chaque colonne du jeu de résultats. **SQLGetData** demande au pilote de transférer des données d’une colonne de jeu de résultats spécifique vers une variable de programme spécifique et spécifie les types de données de la colonne et de la variable. Le pilote peut ainsi convertir des données si la colonne de résultat et la variable de programme possèdent des types de données différents. Les colonnes **Text**, **ntext** et **image** sont généralement trop volumineuses pour tenir dans une variable de programme, mais elles peuvent toujours être récupérées à l’aide de **SQLGetData**. Si les données **Text**, **ntext** ou **image** de la colonne de résultats sont plus volumineuses que la variable de programme, **SQLGetData** retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01004 (données de chaîne tronquées à droite). Les appels successifs à **SQLGetData** retournent des blocs successifs des données **Text** ou **image** . Lorsque la fin des données est atteinte, **SQLGetData** retourne SQL_SUCCESS. Chaque extraction retourne un jeu de lignes, ou « ensemble de lignes », si SQL_ATTR_ROW_ARRAY_SIZE est supérieur à 1. Avant d’utiliser **SQLGetData**, vous devez d’abord utiliser **SQLSetPos** pour spécifier une ligne spécifique dans l’ensemble de lignes en tant que ligne actuelle.  
  
 La troisième option consiste à utiliser une combinaison de **SQLBindCol** et **SQLGetData**. Une application peut, par exemple, lier les dix premières colonnes d’un jeu de résultats, puis, à chaque extraction, appeler **SQLGetData** trois fois pour extraire les données de trois colonnes indépendantes. Cela est généralement utilisé lorsqu’un jeu de résultats contient une ou plusieurs colonnes **Text** ou **image** .  
  
 En fonction des options de curseur définies pour le jeu de résultats, une application peut également utiliser les options de défilement de **SQLFetchScroll** pour faire défiler le jeu de résultats.  
  
 L’utilisation excessive de **SQLBindCol** pour lier une colonne de jeu de résultats à une variable de programme est coûteuse, car **SQLBindCol** force un pilote ODBC à allouer de la mémoire. Lorsque vous liez une colonne de résultats à une variable, cette liaison reste en vigueur jusqu’à ce que vous appeliez [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) pour libérer le descripteur d’instruction ou que vous appeliez [SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) avec *fOption* défini sur SQL_UNBIND. Les liaisons ne sont pas automatiquement annulées à la fin de l'instruction.  
  
 Cette logique vous permet de gérer avec efficacité l'exécution à maintes reprises de la même instruction avec des paramètres différents. Étant donné que le jeu de résultats conserve la même structure, vous pouvez lier le jeu de résultats une fois, traiter toutes les instructions SELECT, puis appeler **SQLFreeStmt** avec *fOption* défini sur SQL_UNBIND après la dernière exécution. Vous ne devez pas appeler **SQLBindCol** pour lier les colonnes d’un jeu de résultats sans appeler d’abord **SQLFreeStmt** avec *fOption* défini sur SQL_UNBIND pour libérer toutes les liaisons précédentes.  
  
 Lorsque vous utilisez **SQLBindCol**, vous pouvez effectuer une liaison selon les lignes ou selon les colonnes. La liaison selon les lignes est un tantinet plus rapide que la liaison selon les colonnes.  
  
 Vous pouvez utiliser **SQLGetData** pour récupérer des données colonne par colonne au lieu de lier des colonnes de jeu de résultats à l’aide de **SQLBindCol**. Si un jeu de résultats contient uniquement quelques lignes, l’utilisation de **SQLGetData** au lieu de **SQLBindCol** est plus rapide. dans le cas contraire, **SQLBindCol** offre les meilleures performances. Si vous ne placez pas toujours les données dans le même ensemble de variables, vous devez utiliser **SQLGetData** au lieu de relier constamment. Vous pouvez uniquement utiliser **SQLGetData** sur les colonnes qui figurent dans la liste de sélection une fois toutes les colonnes liées à **SQLBindCol**. La colonne doit également apparaître après toutes les colonnes sur lesquelles vous avez déjà utilisé **SQLGetData**.  
  
 Les fonctions ODBC qui gèrent le déplacement des données dans ou hors des variables de programme, telles que **SQLGetData**, **SQLBindCol** et [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), prennent en charge la conversion de type de données implicite. Par exemple, si une application lie une colonne d'entiers à une variable de programme de chaîne de caractères, le pilote convertit automatiquement les données d'entier en caractère avant de les insérer dans la variable de programme.  
  
 La conversion de données dans les applications doit être réduite. À moins que la conversion de données ne soit nécessaire pour le traitement pris en charge par l'application, les applications doivent lier les colonnes et les paramètres à des variables de programme du même type de données. En revanche, si les données doivent être converties d'un type à un autre, il est plus efficace de confier la conversion au pilote plutôt que de l'effectuer dans l'application. Normalement, le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client se contente de transférer directement les données des tampons réseau vers les variables de l'application. En confiant la conversion des données au pilote, vous forcez ce dernier à mettre les données en mémoire tampon et à les convertir au moyen de cycles processeur.  
  
 Les variables de programme doivent être suffisamment volumineuses pour contenir les données transférées à partir d’une colonne, à l’exception des données **Text**, **ntext** et **image** . Si une application tente d'extraire les données d'un jeu de résultats et de les placer dans une variable trop petite pour les contenir, le pilote émet un avertissement. Cette opération contraint le pilote à allouer de la mémoire pour le message et le pilote et l'application doivent tous les deux utiliser des cycles processeur pour traiter le message et gérer les erreurs. L'application doit soit allouer une variable suffisamment grande pour accueillir les données extraites, soit faire appel à la fonction SUBSTRING dans la liste de sélection pour réduire la taille de la colonne au sein du jeu de résultats.  
  
 Soyez vigilant lorsque vous utilisez SQL_C_DEFAULT pour définir le type de la variable C. SQL_C_DEFAULT spécifie que le type de la variable C correspond au type de données SQL de la colonne ou du paramètre. Si SQL_C_DEFAULT est spécifié pour une colonne **ntext**, **nchar** ou **nvarchar** , les données Unicode sont retournées à l’application. Ceci peut entraîner divers problèmes si l'application n'a pas été codée pour gérer des données Unicode. Les mêmes types de problèmes peuvent se produire avec le type de données **uniqueidentifier** (SQL_GUID).  
  
 les données **Text**, **ntext** et **image** sont généralement trop volumineuses pour tenir dans une seule variable de programme, et sont généralement traitées avec **SQLGetData** au lieu de **SQLBindCol**. Lors de l’utilisation de curseurs côté serveur, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client est optimisé pour ne pas transmettre les données des colonnes non liées **Text**, **ntext** ou **image** au moment où la ligne est extraite. Les données **Text**, **ntext** ou **image** ne sont pas réellement récupérées à partir du serveur tant que l’application n’émet pas **SQLGetData** pour la colonne.  
  
 Cette optimisation peut être appliquée aux applications afin qu’aucune donnée **Text**, **ntext** ou **image** ne soit affichée pendant qu’un utilisateur fait défiler un curseur. Une fois que l’utilisateur a sélectionné une ligne, l’application peut appeler **SQLGetData** pour extraire les données **Text**, **ntext** ou **image** . Cela permet d’économiser la transmission des données **Text**, **ntext** ou **image** pour les lignes que l’utilisateur ne sélectionne pas et peut enregistrer la transmission de très grandes quantités de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des résultats &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
