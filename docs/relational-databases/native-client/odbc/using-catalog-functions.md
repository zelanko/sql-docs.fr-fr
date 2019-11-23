---
title: Utilisation des fonctions de catalogue | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQLLinkedCatalogs function
- SQL Server Native Client ODBC driver, catalog functions
- SQLLinkedServers function
- catalog functions [ODBC]
- functions [ODBC]
ms.assetid: 7773fb2e-06b5-4c4b-88e9-0ad9132ad273
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5dbbab122d5789f26d9fd5a6c853be4f5a354a96
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73760335"
---
# <a name="using-catalog-functions"></a>Utilisation des fonctions de catalogue
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Toutes les bases de données ont une structure contenant les données stockée dans la base de données. Une définition de cette structure, ainsi que d'autres informations comme les autorisations, est stockée dans un catalogue (implémenté comme ensemble de tables système), également appelé dictionnaire de données.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client permet à une application de déterminer la structure de la base de données par le biais d’appels aux fonctions de catalogue ODBC. Les fonctions de catalogue retournent les informations dans les jeux de résultats et sont implémentées à l'aide de procédures stockées de catalogue pour interroger les tables système du catalogue. Par exemple, une application peut demander un jeu de résultats contenant des informations sur toutes les tables du système ou sur toutes les colonnes d'une table particulière. Les fonctions de catalogue ODBC standard sont utilisées pour obtenir des informations de catalogue à partir du serveur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auquel l'application est connectée.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge les requêtes distribuées dans lesquelles l'accès aux données de plusieurs sources de données OLE DB hétérogènes s'effectue via une requête unique. L'une des méthodes d'accès à une source de données OLE DB distante consiste à définir la source de données comme serveur lié. Pour ce faire, vous pouvez utiliser [sp_addlinkedserver](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md). Une fois que le serveur lié a été défini, les objets de ce serveur peuvent être référencés dans les instructions Transact-SQL en utilisant un nom en quatre parties :  
  
 *linked_server_name.catalog.schema.object_name*.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client prend en charge deux fonctions spécifiques au pilote qui aident à obtenir les informations de catalogue des serveurs liés :  
  
-   **SQLLinkedServers**  
  
     Retourne la liste des serveurs liés définis au serveur local.  
  
-   **SQLLinkedCatalogs**  
  
     Retourne la liste des catalogues contenus dans un serveur lié.  
  
 Une fois que vous avez un nom de serveur lié et un nom de catalogue, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge l’obtention d’informations à partir du catalogue en utilisant un nom en deux parties de _linked_server_name_ **.** _catalogue_ pour *nomcatalogue* sur les fonctions de catalogue ODBC suivantes :  
  
-   **SQLColumnPrivileges**  
  
-   **SQLColumns**  
  
-   **SQLPrimaryKeys**  
  
-   **SQLStatistics**  
  
-   **SQLTablePrivileges**  
  
-   **SQLTables**  
  
 Linked_server_name en deux parties **.** le _catalogue_ est également pris en charge pour *FKCatalogName* et *PKCatalogName* sur [SQLForeignKeys](../../../relational-databases/native-client-odbc-api/sqlforeignkeys.md).  
  
 L'utilisation de SQLLinkedServers et SQLLinkedCatalogs requiert les fichiers suivants :  
  
-   sqlncli.h  
  
     Inclut les prototypes de fonctions et les définitions de constantes pour les fonctions de catalogue du serveur lié. sqlncli.h doit être inclus dans l'application ODBC, ainsi que dans le chemin d'accès Include lorsque l'application est compilée.  
  
-   sqlncli11.lib  
  
     Doit être dans le chemin d'accès de la bibliothèque de l'éditeur de liens et spécifié comme fichier à lier. sqlncli11.lib est distribué avec le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
-   sqlncli11.dll  
  
     Doit être présent lors de l'exécution. sqlncli11.dll est distribué avec le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;ODBC&#41; ](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLColumnPrivileges](../../../relational-databases/native-client-odbc-api/sqlcolumnprivileges.md)   
 [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)   
 [SQLPrimaryKeys](../../../relational-databases/native-client-odbc-api/sqlprimarykeys.md)   
 [SQLTablePrivileges](../../../relational-databases/native-client-odbc-api/sqltableprivileges.md)   
 [SQLTables](../../../relational-databases/native-client-odbc-api/sqltables.md)   
 [SQLStatistics](../../../relational-databases/native-client-odbc-api/sqlstatistics.md)  
  
  
