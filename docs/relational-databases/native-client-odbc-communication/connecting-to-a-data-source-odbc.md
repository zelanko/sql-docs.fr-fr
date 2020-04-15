---
title: Connexion à une source de données (ODBC) Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- checking connection states
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- SQLBrowseConnect function
- ODBC applications, connections
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLConnect function
- SQLDriveConnect function
- verifying connection states
- SQL Server Native Client ODBC driver, data sources
- SQL Server Native Client ODBC driver, connections
ms.assetid: ae30dd1d-06ae-452b-9618-8fd8cd7ba074
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ae59e0bdb005d296341970f4582100b15a0dfdf7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307710"
---
# <a name="connecting-to-a-data-source-odbc"></a>Connexion à une source de données (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Après avoir alloué des handles d'environnement et de connexion et avoir défini tous les attributs de connexion, l'application se connecte à la source de données ou au pilote. Trois fonctions vous permettent de vous connecter :  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLBrowseConnect**  
  
 Pour plus d’informations sur l’enregistrement des connexions à une source de données, y compris les différentes options de chaîne de connexion [disponibles, voir Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
## <a name="sqlconnect"></a>SQLConnect  
 **SQLConnect** est la fonction de connexion la plus simple. Elle accepte trois paramètres : un nom de source de données, un ID d'utilisateur et un mot de passe. Utilisez **SQLConnect** lorsque ces trois paramètres contiennent toutes les informations nécessaires pour se connecter à la base de données. Pour ce faire, dressez une liste des sources de données à l’aide de **SQLDataSources**; inciter l’utilisateur à trouver une source de données, un identifiant d’utilisateur et un mot de passe; et ensuite appeler **SQLConnect**.  
  
 **SQLConnect** suppose qu’un nom, un identifiant d’utilisateur et un mot de passe de source de données sont suffisants pour se connecter à une source de données et que la source de données ODBC contient toutes les autres informations dont le conducteur D’ODBC a besoin pour effectuer la connexion. Contrairement à [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) et [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md), **SQLConnect** n’utilise pas de chaîne de connexion.  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
 **SQLDriverConnect** est utilisé lorsque plus d’informations que le nom de source de données, l’identifiant d’utilisateur et le mot de passe sont nécessaires. L’un des paramètres de **SQLDriverConnect** est une chaîne de connexion contenant des informations spécifiques au conducteur. Vous pouvez utiliser **SQLDriverConnect** au lieu de **SQLConnect** pour les raisons suivantes :  
  
-   Pour fournir des informations spécifiques au pilote lors de la connexion.  
  
-   Pour demander que le pilote invite l'utilisateur à fournir des informations sur la connexion.  
  
-   Pour se connecter sans le recours à une source de données ODBC.  
  
 La chaîne de connexion **SQLDriverConnect** contient une série de paires de mots clés qui spécifient toutes les informations de connexion prises en charge par un pilote ODBC. Chaque pilote prend en charge les mots clés ODBC standard (DSN, FILEDSN, DRIVER, UID, PWD et SAVEFILE) en plus des mots clés spécifiques au pilote pour toutes les informations de connexion prises en charge par le pilote. **SQLDriverConnect** peut être utilisé pour se connecter sans source de données. Par exemple, une application conçue pour établir une connexion « sans DSN » à une instance de peut appeler [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQLDriverConnect** avec une chaîne de connexion qui définit l’ID de connexion, le mot de passe, la bibliothèque réseau, le nom du serveur à connecter et la base de données par défaut à utiliser.  
  
 Lors de l’utilisation **de SQLDriverConnect**, il existe deux options pour inciter l’utilisateur pour toute information de connexion nécessaire:  
  
-   Boîte de dialogue d'application  
  
     Vous pouvez créer une boîte de dialogue d’application qui invite à des informations de connexion, puis appelle **SQLDriverConnect** avec une poignée de fenêtre NULL et *DriverCompletion* ensemble à SQL_DRIVER_NOPROMPT. Ces paramètres empêchent le pilote ODBC d'ouvrir sa propre boîte de dialogue. Cette méthode est employée lorsqu'il est vital de contrôler l'interface utilisateur de l'application.  
  
-   Boîte de dialogue du pilote  
  
     Vous pouvez coder l’application pour passer une poignée de fenêtre valide à **SQLDriverConnect** et définir le *paramètre DriverCompletion* pour SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT ou SQL_DRIVER_COMPLETE_REQUIRED. Le pilote génère ensuite une boîte de dialogue pour inviter l'utilisateur à fournir les informations de connexion. Cette méthode simplifie le code de l'application.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
 **SQLBrowseConnect**, comme **SQLDriverConnect**, utilise une chaîne de connexion. Cependant, en utilisant **SQLBrowseConnect**, une application peut construire une chaîne de connexion complète itérativement avec la source de données au moment de l’exécution. L'application peut alors réaliser deux tâches :  
  
-   Créer ses propres boîtes de dialogue pour demander ces informations et conserver ainsi le contrôle de son interface utilisateur.  
  
-   Parcourir le système à la recherche de sources de données qu'un pilote en particulier peut exploiter, et ce éventuellement en plusieurs étapes.  
  
     Par exemple, l'utilisateur peut d'abord rechercher des serveurs sur le réseau, puis après avoir choisi un serveur, recherchez sur ce dernier des bases de données auxquelles le pilote peut accéder.  
  
 Lorsque **SQLBrowseConnect** effectue une connexion réussie, il renvoie une chaîne de connexion qui peut être utilisée lors d’appels ultérieurs à **SQLDriverConnect**.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote Native Client ODBC revient toujours SQL_SUCCESS_WITH_INFO sur un **SQLConnect**réussi , **SQLDriverConnect**, ou **SQLBrowseConnect**. Lorsqu’une application ODBC appelle **SQLGetDiagRec** après avoir obtenu SQL_SUCCESS_WITH_INFO, elle peut recevoir les messages suivants :  
  
 5701  
 Indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a placé le contexte de l'utilisateur dans la base de données par défaut définie dans la source de données ou dans la base de données par défaut définie pour l'ID de connexion employé dans la connexion si la source de données ne disposait pas d'une base de données par défaut.  
  
 5703  
 Indique la langue utilisée sur le serveur.  
  
 L'exemple ci-dessous affiche le message retourné par l'administrateur système lorsqu'une connexion est réussie  :  
  
```  
szSqlState = "01000", *pfNativeError = 5701,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed database context to 'pubs'."  
szSqlState = "01000", *pfNativeError = 5703,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
       Changed language setting to 'us_english'."  
```  
  
 Vous pouvez ignorer les messages 5701 et 5703 ; ils sont fournis uniquement à titre d'information. En revanche, n'ignorez pas le code de retour SQL_SUCCESS_WITH_INFO car des messages autres que 5701 ou 5703 peuvent être retournés. Par exemple, si un pilote se connecte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à un serveur exécutant une instance de procédures stockées obsolètes de catalogue, l’une des erreurs retournées par **SQLGetDiagRec** après une SQL_SUCCESS_WITH_INFO est :  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 La fonction de traitement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des erreurs d’une application pour les connexions devrait appeler **SQLGetDiagRec** jusqu’à ce qu’elle revienne SQL_NO_DATA. Il doit alors agir sur tous les messages autres que ceux avec un code *pfNatif* de 5701 ou 5703.  
  
## <a name="see-also"></a>Voir aussi  
 [Communiquer avec SQL Server &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
