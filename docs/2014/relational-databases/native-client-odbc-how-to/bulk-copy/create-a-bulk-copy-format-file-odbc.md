---
title: Créer un fichier de Format de copie en bloc (ODBC) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- bulk copy [ODBC], data files
ms.assetid: 0572fef3-daf5-409e-b557-c2a632f9a06d
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 03ab22f08f4364bf3cd4852f960d861c9dcdad7d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051949"
---
# <a name="create-a-bulk-copy-format-file-odbc"></a>Créer un fichier de format de copie en bloc (ODBC)
  Cet exemple illustre comment utiliser des fonctions de copie en bloc pour créer un fichier de données et un fichier de format. Cet exemple a été développé pour la version 3.0 d'ODBC ou une version ultérieure.  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, utilisez l'authentification Windows. Si l'authentification Windows n'est pas disponible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Évitez de stocker ces informations dans un fichier. Si vous devez rendre les informations d'identification persistantes, chiffrez-les avec l' [API de chiffrement Win32](http://go.microsoft.com/fwlink/?LinkId=64532).  
  
### <a name="to-create-a-bulk-copy-format-file"></a>Pour créer un fichier de format de copie en bloc  
  
1.  Allouez un handle d'environnement et un handle de connexion.  
  
2.  Définissez SQL_COPT_SS_BCP et SQL_BCP_ON de façon à activer les opérations de copie en bloc.  
  
3.  Connectez-vous à SQL Server.  
  
4.  Appelez [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) pour définir les informations suivantes :  
  
    -   Nom de la table ou de la vue à partir de laquelle ou vers laquelle effectuer la copie en bloc.  
  
    -   Nom du fichier de données qui contient les données à copier dans la base de données ou qui reçoit les données lors de la copie à partir de la base de données.  
  
    -   Nom d'un fichier de données devant recevoir tous les messages d'erreur de copie en bloc (spécifiez NULL si vous ne souhaitez pas de fichier de message).  
  
    -   Direction de la copie : DB_OUT vers le fichier à partir de la table ou vue.  
  
5.  Appelez [bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) pour définir le nombre de colonnes.  
  
6.  Appelez [bcp_colfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) pour chaque colonne à définir les caractéristiques du fichier de données.  
  
7.  Appelez [bcp_writefmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) pour créer un fichier de format décrivant le fichier de données doit être créé par l’opération de copie en bloc.  
  
8.  Appelez [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) pour exécuter l’opération de copie en bloc.  
  
 Une opération de copie en bloc exécutée de cette manière crée à la fois un fichier de données contenant les données copiées en bloc et un fichier de format décrivant la mise en page du fichier de données.  
  
## <a name="example"></a>Exemple  
 Vous aurez besoin d'une source de données ODBC nommée AdventureWorks, dont la base de données par défaut est l'exemple de base de données AdventureWorks. (Vous pouvez télécharger l’exemple de base de données AdventureWorks à partir de la page d’accueil des [exemples et projets de communautés Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkID=85384).) Cette source de données doit être basée sur le pilote ODBC fourni par le système d'exploitation (le nom du pilote est « SQL Server »). Si vous générez et exécutez cet exemple comme une application 32 bits sur un système d'exploitation 64 bits, vous devez créer la source de données ODBC avec l'administrateur ODBC dans %windir%\SysWOW64\odbcad32.exe.  
  
 Cet exemple vous permet de vous connecter à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] par défaut de votre ordinateur. Pour vous connecter à une instance nommée, modifiez la définition de la source de données ODBC pour spécifier l'instance en utilisant le format suivant : serveur\namedinstance. Par défaut, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] est installé dans une instance nommée.  
  
 Exécutez la première liste de code ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) pour créer la table que l'exemple utilisera.  
  
 Compilez la deuxième liste de code (C++) avec odbc32.lib et odbcbcp.lib.  
  
 Exécutez la troisième liste de code ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) pour supprimer la table que l'exemple a utilisée.  
  
```  
use AdventureWorks  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
  
CREATE TABLE BCPDate (cola int, colb datetime)  
insert BCPDate(cola) values(1)   
insert BCPDate(cola) values(2)   
insert BCPDate(cola) values(3)   
insert BCPDate(cola) values(4)  
```  
  
```  
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC;    
  
void Cleanup() {  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // BCP variables.  
   SDWORD cRows;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate ODBC connection handle, set bulk copy mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_OUT);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set the number of output columns.  
   retcode = bcp_columns(hdbc1, 2);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Describe the format of column 1 in the data file.  
   retcode = bcp_colfmt(hdbc1, 1, SQLCHARACTER, -1, 5, NULL, 0, 1);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Describe the format of column 2 in the data file.  
   retcode = bcp_colfmt(hdbc1, 2, SQLCHARACTER, -1, 20, NULL, 0, 2);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Create the format file.  
   retcode = bcp_writefmt(hdbc1, "c:\\BCPFMT.fmt");  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied out = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   return(0);  
}  
```  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Copie en bloc avec les SQL Server ODBC Driver rubriques &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md)   
 [Utilisation de fichiers de données et de format](../../native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
  