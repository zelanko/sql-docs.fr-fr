---
title: Connexion à une source de données (ODBC) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eb1f2133aa335f266da75e00638dbb484dae1431
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73784713"
---
# <a name="connecting-to-a-data-source-odbc"></a>Connexion à une source de données (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Après avoir alloué des handles d'environnement et de connexion et avoir défini tous les attributs de connexion, l'application se connecte à la source de données ou au pilote. Trois fonctions vous permettent de vous connecter :  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **SQLBrowseConnect**  
  
 Pour plus d’informations sur l’établissement de connexions à une source de données, y compris les différentes options de chaîne de connexion disponibles, consultez [utilisation de mots clés de chaîne de connexion avec SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
## <a name="sqlconnect"></a>SQLConnect  
 **SQLConnect** est la fonction de connexion la plus simple. Elle accepte trois paramètres : un nom de source de données, un ID d'utilisateur et un mot de passe. Utilisez **SQLConnect** lorsque ces trois paramètres contiennent toutes les informations nécessaires pour se connecter à la base de données. Pour ce faire, générez une liste de sources de données à l’aide de **SQLDataSources**; demander à l’utilisateur une source de données, un ID d’utilisateur et un mot de passe ; puis appelez **SQLConnect**.  
  
 **SQLConnect** suppose qu’un nom de source de données, un ID d’utilisateur et un mot de passe sont suffisants pour se connecter à une source de données et que la source de données ODBC contient toutes les autres informations dont le pilote ODBC a besoin pour établir la connexion. Contrairement à [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) et [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md), **SQLConnect** n’utilise pas de chaîne de connexion.  
  
## <a name="sqldriverconnect"></a>SQLDriverConnect  
 **SQLDriverConnect** est utilisé lorsque plus d’informations que le nom de la source de données, l’ID d’utilisateur et le mot de passe sont requis. L’un des paramètres de **SQLDriverConnect** est une chaîne de connexion contenant des informations spécifiques au pilote. Vous pouvez utiliser **SQLDriverConnect** au lieu de **SQLConnect** pour les raisons suivantes :  
  
-   Pour fournir des informations spécifiques au pilote lors de la connexion.  
  
-   Pour demander que le pilote invite l'utilisateur à fournir des informations sur la connexion.  
  
-   Pour se connecter sans le recours à une source de données ODBC.  
  
 La chaîne de connexion **SQLDriverConnect** contient une série de paires mot clé-valeur qui spécifient toutes les informations de connexion prises en charge par un pilote ODBC. Chaque pilote prend en charge les mots clés ODBC standard (DSN, FILEDSN, DRIVER, UID, PWD et SAVEFILE) en plus des mots clés spécifiques au pilote pour toutes les informations de connexion prises en charge par le pilote. **SQLDriverConnect** peut être utilisé pour se connecter sans source de données. Par exemple, une application conçue pour établir une connexion sans DSN à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut appeler **SQLDriverConnect** avec une chaîne de connexion qui définit l’ID de connexion, le mot de passe, la bibliothèque réseau, le nom du serveur auquel se connecter et la base de données par défaut à utiliser.  
  
 Lorsque vous utilisez **SQLDriverConnect**, il existe deux options pour inviter l’utilisateur à entrer les informations de connexion nécessaires :  
  
-   Boîte de dialogue d'application  
  
     Vous pouvez créer une boîte de dialogue d’application qui demande des informations de connexion, puis appelle **SQLDriverConnect** avec un handle de fenêtre null et *DriverCompletion* défini sur SQL_DRIVER_NOPROMPT. Ces paramètres empêchent le pilote ODBC d'ouvrir sa propre boîte de dialogue. Cette méthode est employée lorsqu'il est vital de contrôler l'interface utilisateur de l'application.  
  
-   Boîte de dialogue du pilote  
  
     Vous pouvez coder l’application pour transmettre un handle de fenêtre valide à **SQLDriverConnect** et définir le paramètre *DriverCompletion* sur SQL_DRIVER_COMPLETE, SQL_DRIVER_PROMPT ou SQL_DRIVER_COMPLETE_REQUIRED. Le pilote génère ensuite une boîte de dialogue pour inviter l'utilisateur à fournir les informations de connexion. Cette méthode simplifie le code de l'application.  
  
## <a name="sqlbrowseconnect"></a>SQLBrowseConnect  
 **SQLBrowseConnect**, comme **SQLDriverConnect**, utilise une chaîne de connexion. Toutefois, en utilisant **SQLBrowseConnect**, une application peut construire une chaîne de connexion complète de manière itérative avec la source de données au moment de l’exécution. L'application peut alors réaliser deux tâches :  
  
-   Créer ses propres boîtes de dialogue pour demander ces informations et conserver ainsi le contrôle de son interface utilisateur.  
  
-   Parcourir le système à la recherche de sources de données qu'un pilote en particulier peut exploiter, et ce éventuellement en plusieurs étapes.  
  
     Par exemple, l'utilisateur peut d'abord rechercher des serveurs sur le réseau, puis après avoir choisi un serveur, recherchez sur ce dernier des bases de données auxquelles le pilote peut accéder.  
  
 Lorsque **SQLBrowseConnect** termine une connexion réussie, il retourne une chaîne de connexion qui peut être utilisée lors des appels suivants à **SQLDriverConnect**.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client retourne toujours SQL_SUCCESS_WITH_INFO sur un **SQLConnect**, **SQLDriverConnect**ou **SQLBrowseConnect**réussi. Quand une application ODBC appelle **SQLGetDiagRec** après l’obtention de SQL_SUCCESS_WITH_INFO, elle peut recevoir les messages suivants :  
  
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
  
 Vous pouvez ignorer les messages 5701 et 5703 ; ils sont fournis uniquement à titre d'information. En revanche, n'ignorez pas le code de retour SQL_SUCCESS_WITH_INFO car des messages autres que 5701 ou 5703 peuvent être retournés. Par exemple, si un pilote se connecte à un serveur exécutant une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance de avec des procédures stockées de catalogue obsolètes, l’une des erreurs retournées via **SQLGetDiagRec** après une SQL_SUCCESS_WITH_INFO est la suivante :  
  
```  
SqlState:   01000  
pfNative:   0  
szErrorMsg: "[Microsoft][SQL Server Native Client]The ODBC  
            catalog stored procedures installed on server  
            my65server are version 06.50.0193; version 07.00.0205  
            or later is required to ensure proper operation.  
            Please contact your system administrator."  
```  
  
 La fonction de gestion des erreurs d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] application pour les connexions doit appeler **SQLGetDiagRec** jusqu’à ce qu’elle retourne SQL_NO_DATA. Il doit ensuite agir sur tous les messages autres que ceux avec un code *pfNative* de 5701 ou 5703.  
  
## <a name="see-also"></a>Voir aussi  
 [Communication avec SQL Server &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
