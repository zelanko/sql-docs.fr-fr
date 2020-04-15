---
title: Allouer les poignées et se connecter au serveur SQL (ODBC) Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d26af711c07c4ea296d5351d0fcb0d1f9710706
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294481"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>Allouer des handles et se connecter à SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>Pour allouer les handles et se connecter à SQL Server  
  
1.  Incluez les fichiers d'en-tête ODBC Sql.h, Sqlext.h, Sqltypes.h.  
  
2.  Incluez le fichier d'en-tête spécifique au pilote [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Odbcss.h.  
  
3.  Appelez [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) avec un **HandleType** de SQL_HANDLE_ENV pour initialiser ODBC et allouer une poignée d’environnement.  
  
4.  Appelez [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) avec **l’ensemble d’attributs** à SQL_ATTR_ODBC_VERSION et **ValuePtr** réglé pour SQL_OV_ODBC3 pour indiquer que l’application utilisera des appels de fonction ODBC 3.x-format.  
  
5.  En option, appelez [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) pour définir d’autres options en environnement, ou appelez [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403) pour obtenir des options en environnement.  
  
6.  Appelez [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) avec un **HandleType** de SQL_HANDLE_DBC pour allouer une poignée de connexion.  
  
7.  En option, appelez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) pour définir les options de connexion, ou appelez [SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) pour obtenir des options de connexion.  
  
8.  Appelez SQLConnect pour utiliser une source [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de données existante pour vous connecter à .  
  
     ou  
  
     Appelez [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) pour utiliser une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]chaîne de connexion pour vous connecter à .  
  
     Une chaîne de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] minimale complète revêt l'une des deux formes :  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     Si la chaîne de connexion n’est pas complète, **SQLDriverConnect** peut demander les informations requises. Ceci est contrôlé par la valeur spécifiée pour le *paramètre DriverCompletion.*  
  
     \- ou -  
  
     Appelez [SQLBrowseConnect](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) plusieurs fois d’une manière itérative [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]pour construire la chaîne de connexion et se connecter à .  
  
9. Optionnellement, appelez [SQLGetInfo](../../relational-databases/native-client-odbc-api/sqlgetinfo.md) pour obtenir des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attributs et un comportement du conducteur pour la source de données.  
  
10. Allouez et utilisez les instructions.  
  
11. Appelez SQLDisconnect pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous déconnecter et rendre la poignée de connexion disponible pour une nouvelle connexion.  
  
12. Appelez [SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) avec un **HandleType** de SQL_HANDLE_DBC pour libérer la poignée de connexion.  
  
13. Appelez **SQLFreeHandle** avec un **HandleType** de SQL_HANDLE_ENV pour libérer la poignée de l’environnement.  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, utilisez l'authentification Windows. Si l'authentification Windows n'est pas disponible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Évitez de stocker ces informations dans un fichier. Si vous devez poursuivre vos informations d’identification, vous devez les chiffrer avec [l’API Win32 crypto](https://go.microsoft.com/fwlink/?LinkId=64532).  
  
## <a name="example"></a>Exemple  
 Cet exemple montre un appel à **SQLDriverConnect** pour se connecter à une instance de sans avoir besoin d’une source de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données ODBC existante. En passant une chaîne de connexion incomplète à **SQLDriverConnect**, il provoque le pilote ODBC d’inviter l’utilisateur à entrer les informations manquantes.  
  
```  
#define MAXBUFLEN   255  
  
SQLHENV      henv = SQL_NULL_HENV;  
SQLHDBC      hdbc1 = SQL_NULL_HDBC;  
SQLHSTMT      hstmt1 = SQL_NULL_HSTMT;  
  
SQLCHAR      ConnStrIn[MAXBUFLEN] =  
         "DRIVER={SQL Server Native Client 10.0};SERVER=MyServer";  
  
SQLCHAR      ConnStrOut[MAXBUFLEN];  
SQLSMALLINT   cbConnStrOut = 0;  
  
// Make connection without data source. Ask that driver   
// prompt if insufficient information. Driver returns  
// SQL_ERROR and application prompts user  
// for missing information. Window handle not needed for  
// SQL_DRIVER_NOPROMPT.  
retcode = SQLDriverConnect(hdbc1,      // Connection handle  
                  NULL,         // Window handle  
                  ConnStrIn,      // Input connect string  
                  SQL_NTS,         // Null-terminated string  
                  ConnStrOut,      // Address of output buffer  
                  MAXBUFLEN,      // Size of output buffer  
                  &cbConnStrOut,   // Address of output length  
                  SQL_DRIVER_PROMPT);  
```  
  
  
