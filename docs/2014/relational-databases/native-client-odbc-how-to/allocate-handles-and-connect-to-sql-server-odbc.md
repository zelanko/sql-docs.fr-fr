---
title: Allouer des descripteurs et se connecter à SQL Server (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 322120624c612371b56029c2cf29c9ab457c81b5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63225505"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>Allouer des handles et se connecter à SQL Server (ODBC)
    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>Pour allouer les handles et se connecter à SQL Server  
  
1.  Incluez les fichiers d'en-tête ODBC Sql.h, Sqlext.h, Sqltypes.h.  
  
2.  Incluez le fichier d'en-tête spécifique au pilote [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Odbcss.h.  
  
3.  Appelez [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) avec un `HandleType` de SQL_HANDLE_ENV pour initialiser ODBC et allouer un handle d’environnement.  
  
4.  Appelez [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) avec `Attribute` la valeur SQL_ATTR_ODBC_VERSION et `ValuePtr` définissez sur SQL_OV_ODBC3 pour indiquer que l’application utilisera les appels de fonction ODBC 3. x-format.  
  
5.  Si vous le souhaitez, appelez [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) pour définir d’autres options d’environnement, ou appelez [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403) pour accéder aux options d’environnement.  
  
6.  Appelez [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) avec un `HandleType` de SQL_HANDLE_DBC pour allouer un handle de connexion.  
  
7.  Vous pouvez également appeler [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) pour définir les options de connexion ou appeler [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) pour accéder aux options de connexion.  
  
8.  Appelez SQLConnect pour utiliser une source de données existante à laquelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]se connecter.  
  
     ou  
  
     Appelez [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) pour utiliser une chaîne de connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Une chaîne de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] minimale complète revêt l'une des deux formes :  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     Si la chaîne de connexion n'est pas complète, `SQLDriverConnect` peut demander les informations nécessaires. Cela est contrôlé par la valeur spécifiée pour le paramètre *DriverCompletion* .  
  
     \- ou -  
  
     Appelez plusieurs fois [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md) de manière itérative pour créer la chaîne de connexion et vous connecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]à.  
  
9. Vous pouvez également appeler [SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md) pour obtenir les attributs de pilote et le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comportement de la source de données.  
  
10. Allouez et utilisez les instructions.  
  
11. Appelez SQLDisconnect pour vous déconnecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et rendre le descripteur de connexion disponible pour une nouvelle connexion.  
  
12. Appelez [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) avec un `HandleType` de SQL_HANDLE_DBC pour libérer le handle de connexion.  
  
13. Appelez `SQLFreeHandle` avec un `HandleType` de SQL_HANDLE_ENV pour libérer le handle d'environnement.  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, utilisez l'authentification Windows. Si l'authentification Windows n'est pas disponible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Évitez de stocker ces informations dans un fichier. Si vous devez conserver des informations d’identification, vous devez les chiffrer avec l' [API de chiffrement Win32](https://go.microsoft.com/fwlink/?LinkId=64532).  
  
## <a name="example"></a>Exemple  
 Cet exemple illustre un appel de `SQLDriverConnect` pour se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sans requérir une source de données ODBC existante. En passant une chaîne de connexion incomplète à `SQLDriverConnect`, le pilote ODBC est contraint de demander à l'utilisateur d'entrer les informations manquantes.  
  
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
  
  
