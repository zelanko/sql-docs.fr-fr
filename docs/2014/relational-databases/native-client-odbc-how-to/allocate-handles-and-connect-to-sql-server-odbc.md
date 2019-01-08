---
title: Allouer des Handles et se connecter à SQL Server (ODBC) | Microsoft Docs
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
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53376353"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a>Allouer des handles et se connecter à SQL Server (ODBC)
    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a>Pour allouer les handles et se connecter à SQL Server  
  
1.  Incluez les fichiers d'en-tête ODBC Sql.h, Sqlext.h, Sqltypes.h.  
  
2.  Incluez le fichier d'en-tête spécifique au pilote [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Odbcss.h.  
  
3.  Appelez [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) avec un `HandleType` de SQL_HANDLE_ENV pour initialiser ODBC et allouer un handle d’environnement.  
  
4.  Appelez [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) avec `Attribute` défini à SQL_ATTR_ODBC_VERSION et `ValuePtr` défini à SQL_OV_ODBC3 pour indiquer l’application utilisera les appels de fonction au format 3.x ODBC.  
  
5.  Le cas échéant, appelez [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) pour définir l’autre environnement options ou appel [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403) pour obtenir des options d’environnement.  
  
6.  Appelez [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) avec un `HandleType` de SQL_HANDLE_DBC pour allouer un handle de connexion.  
  
7.  Le cas échéant, appelez [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) pour définir les options de connexion ou d’appel [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) pour obtenir des options de connexion.  
  
8.  Appelez SQLConnect pour utiliser une source de données existante pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     ou  
  
     Appelez [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) à utiliser une chaîne de connexion pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Une chaîne de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] minimale complète revêt l'une des deux formes :  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     Si la chaîne de connexion n'est pas complète, `SQLDriverConnect` peut demander les informations nécessaires. Cela est contrôlé par la valeur spécifiée pour le *DriverCompletion* paramètre.  
  
     \- ou -  
  
     Appelez [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md) plusieurs fois de manière itérative pour générer la chaîne de connexion et de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
9. Le cas échéant, appelez [SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md) pour obtenir les attributs de pilote et le comportement pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source de données.  
  
10. Allouez et utilisez les instructions.  
  
11. Appelez SQLDisconnect pour vous déconnecter de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et libérer la connexion gérer pour une nouvelle connexion.  
  
12. Appelez [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) avec un `HandleType` de SQL_HANDLE_DBC pour libérer le handle de connexion.  
  
13. Appelez `SQLFreeHandle` avec un `HandleType` de SQL_HANDLE_ENV pour libérer le handle d'environnement.  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, utilisez l'authentification Windows. Si l'authentification Windows n'est pas disponible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Évitez de stocker ces informations dans un fichier. Si vous devez rendre les informations d'identification persistantes, chiffrez-les avec l' [API de chiffrement Win32](https://go.microsoft.com/fwlink/?LinkId=64532).  
  
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
  
  
