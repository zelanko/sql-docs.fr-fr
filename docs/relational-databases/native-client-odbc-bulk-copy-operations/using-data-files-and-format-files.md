---
title: Utilisation de fichiers de données et de fichiers de format | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e7cf91baeb6771f0abb52fb5b8f4c4dc2bddafe0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73785280"
---
# <a name="using-data-files-and-format-files"></a>Utilisation de fichiers de données et de format
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le programme de copie en bloc le plus simple permet d'effectuer les opérations suivantes :  
  
1.  Appelle [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) pour spécifier la copie en bloc (Set BCP_OUT) à partir d’une table ou d’une vue vers un fichier de données.  
  
2.  Appelle [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) pour exécuter l’opération de copie en bloc.  
  
 Le fichier de données est créé en mode natif ; les données de toutes les colonnes dans une table ou une vue sont stockées dans le fichier de données sous le même format que celui de la base de données. Le fichier peut ensuite être copié en bloc vers un serveur en suivant la même procédure et en définissant DB_IN au lieu de DB_OUT. Cela ne fonctionne que si les tables source et cible ont exactement la même structure. Le fichier de données résultant peut également être entré dans l’utilitaire **BCP** à l’aide du commutateur **/n** (mode natif).  
  
 Pour copier en bloc le jeu de résultats d'une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] plutôt que directement depuis une table ou une vue :  
  
1.  Appelez **bcp_init** pour spécifier la copie en bloc, mais spécifiez NULL pour le nom de la table.  
  
2.  Appelez [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) avec *EOPTION* défini sur valeur BCPHINTS et *iValue* défini sur un pointeur vers une chaîne SQLTCHAR contenant l’instruction Transact-SQL.  
  
3.  Appelez **bcp_exec** pour exécuter l’opération de copie en bloc.  

 L'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] peut être n'importe quelle instruction qui génère un jeu de résultats. Le fichier de données contenant le premier jeu de résultats de l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] est créé. La copie en bloc ignore tous les jeux de résultats après le premier si l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] génère plusieurs jeux de résultats.  
  
 Pour créer un fichier de données dans lequel les données de la colonne sont stockées dans un format différent de celui de la table, appelez [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) pour spécifier le nombre de colonnes qui seront modifiées, puis appelez [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) pour chaque colonne dont vous souhaitez modifier le format. Cette opération est effectuée après l’appel de **bcp_init** mais avant l’appel de **bcp_exec**. **bcp_colfmt** spécifie le format dans lequel les données de la colonne sont stockées dans le fichier de données. Il peut être utilisé lors de la copie en bloc dans ou vers l’extérieur. Vous pouvez également utiliser **bcp_colfmt** pour définir les indicateurs de fin de ligne et de colonne. Par exemple, si vos données ne contiennent pas de caractères de tabulation, vous pouvez créer un fichier délimité par des tabulations à l’aide de **bcp_colfmt** pour définir la tabulation comme marque de fin de chaque colonne.  
  
 Lors de la copie en bloc à partir de **bcp_colfmt**, vous pouvez facilement créer un fichier de format décrivant le fichier de données que vous avez créé en appelant [bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) après le dernier appel à **bcp_colfmt**.  
  
 Lors d’une copie en bloc à partir d’un fichier de données décrit par un fichier de format, lisez le fichier de format en appelant [bcp_readfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) après **bcp_init** mais avant d' **bcp_exec**.  
  
 La fonction **bcp_control** contrôle plusieurs options lors de la copie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en bloc dans à partir d’un fichier de données. **bcp_control** définit des options, telles que le nombre maximal d’erreurs avant l’arrêt, la ligne du fichier sur laquelle démarrer la copie en bloc, la ligne sur laquelle s’arrêter et la taille du lot.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations de copie en bloc &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
