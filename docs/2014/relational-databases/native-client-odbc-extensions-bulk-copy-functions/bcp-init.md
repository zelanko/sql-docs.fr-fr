---
title: bcp_init | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_init
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_init function
ms.assetid: 6a25862c-7f31-4873-ab65-30f3abde89d2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d482ac020aaaf5ac8f029306441c3e9979f4379
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62689063"
---
# <a name="bcp_init"></a>bcp_init
  Initialise l'opération de copie en bloc.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_init (  
HDBC   
hdbc  
,  
LPCTSTR   
szTable  
,  
LPCTSTR   
szDataFile  
,  
LPCTSTR   
szErrorFile  
,  
INT   
eDirection  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *szTable*  
 Nom de la table de base de données depuis ou vers laquelle s'effectue la copie. Ce nom peut aussi inclure le nom de la base de données ou le nom du propriétaire. Par exemple, **pubs. Gracie. titles**, **pubs.. les titres,** **Gracie. titles**et **titles** sont tous des noms de table autorisés.  
  
 Si *eDirection* est DB_OUT, *szTable* peut également être le nom d’une vue de base de données.  
  
 Si *eDirection* est DB_OUT et qu’une instruction SELECT est spécifiée à l’aide de [bcp_control](bcp-control.md) avant l’appel de [bcp_exec](bcp-exec.md) , **bcp_init**_szTable_ doit avoir la valeur null.  
  
 *szDataFile*  
 Nom du fichier utilisateur depuis ou vers lequel s'effectue la copie. Si les données sont copiées directement à partir de variables à l’aide de [bcp_sendrow](bcp-sendrow.md), affectez la valeur null à *szDataFile* .  
  
 *szErrorFile*  
 Nom du fichier d'erreurs à remplir avec les messages de progression, les messages d'erreur et les copies des lignes qui, pour quelque raison que ce soit, n'ont pas pu être copiées d'un fichier utilisateur vers une table. Si la valeur NULL est transmise en tant que *szErrorFile*, aucun fichier d’erreur n’est utilisé.  
  
 *eDirection*  
 Direction de la copie, DB_IN ou DB_OUT. DB_IN indique la copie de variables de programme ou d'un fichier utilisateur dans une table. DB_OUT indique la copie d'une table de base de données dans un fichier utilisateur. Vous devez spécifier un nom de fichier utilisateur avec DB_OUT.  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 Appelez **bcp_init** avant d’appeler une autre fonction de copie en bloc. **bcp_init** effectue les initialisations nécessaires pour une copie en bloc de données entre la station [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de travail et.  
  
 La fonction **bcp_init** doit être fournie avec un handle de connexion ODBC activé pour une utilisation avec des fonctions de copie en bloc. Pour activer le descripteur, utilisez [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) avec SQL_COPT_SS_BCP défini sur SQL_BCP_ON sur un handle de connexion alloué, mais non connecté. La tentative d'assigner l'attribut sur un handle connecté provoque une erreur.  
  
 Lorsqu’un fichier de données est spécifié, **bcp_init** examine la structure de la source de la base de données ou de la table cible, et non pas le fichier de données. **bcp_init** spécifie des valeurs de format de données pour le fichier de données en fonction de chaque colonne de la table de base de données, de la vue ou du jeu de résultats Select. Cette spécification inclut le type de données de chaque colonne, la présence ou l'absence d'un indicateur de longueur ou null et des chaînes d'octet de terminateur dans les données, et la largeur des types de données de longueur fixe. **bcp_init** définit ces valeurs comme suit :  
  
-   Le type de données spécifié est le type de données de la colonne dans la table de base de données, la vue ou le jeu de résultats SELECT. Le type de données est énuméré par les types de données natifs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiés dans sqlncli.h. Les données elles-mêmes sont représentées dans leur forme informatique. Autrement dit, les données d’une colonne de type de données **Integer** sont représentées par une séquence de quatre octets qui est Big-endian ou Little-endian, en fonction de l’ordinateur qui a créé le fichier de données.  
  
-   Si un type de données de base de données est de longueur fixe, les données du fichier de données sont également de longueur fixe. Les fonctions de copie en bloc qui traitent les données (par exemple, [bcp_exec](bcp-exec.md)) analysent les lignes de données, en attendant que la longueur des données dans le fichier de données soit identique à la longueur des données spécifiées dans la liste de la base de données, de la vue ou de la colonne Select. Par exemple, les données d’une colonne de base de données définie en tant que **char (13)** doivent être représentées par 13 caractères pour chaque ligne de données dans le fichier. Les données de longueur fixe peuvent être préfixées avec un indicateur null si la colonne de base de données autorise les valeurs NULL.  
  
-   Lorsque la séquence d'octet de terminateur est définie, la longueur de la séquence d'octet de terminateur est définie avec la valeur 0.  
  
-   Lors de la copie vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le fichier de données doit avoir les données de chaque colonne de la table de base de données. Lors de la copie depuis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les données de toutes les colonnes de la table de base de données, de la vue ou du jeu de résultats SELECT, sont copiées vers le fichier de données.  
  
-   Lors de la copie vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la position ordinale d'une colonne du fichier de données doit être identique à la position ordinale de la colonne de la table de base de données. Lors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]copie à partir de, **bcp_exec** place les données en fonction de la position ordinale de la colonne dans la table de base de données.  
  
-   Si le type de données d’une base de données est variable en longueur (par exemple, **varbinary (22)**) ou si une colonne de base de données peut contenir des valeurs NULL, les données du fichier de données sont précédées d’un indicateur de longueur/null. La largeur de l'indicateur varie selon le type de données et la version de la copie en bloc.  
  
 Pour modifier les valeurs de format de données spécifiées pour un fichier de données, appelez [bcp_columns](bcp-columns.md) et [bcp_colfmt](bcp-colfmt.md).  
  
 Les copies en bloc vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être optimisées pour les tables qui ne contiennent pas d'index en définissant le mode de récupération de base de données avec la valeur SIMPLE ou BULK_LOGGED. Pour plus d’informations, consultez [Configuration requise pour la journalisation minimale dans l’importation en bloc](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md) et [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql).  
  
 Si aucun fichier de données n’est utilisé, vous devez appeler [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) pour spécifier le format et l’emplacement en mémoire des données de chaque colonne, puis copier les lignes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données dans le [bcp_sendrow](bcp-sendrow.md)à l’aide de.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment utiliser la fonction ODBC bcp_init avec un fichier de format.  
  
 Avant de compiler et d'exécuter le code C++, vous devez procéder comme suit :  
  
-   Créez une source de données ODBC nommée Test. Vous pouvez associer cette source de données à toute base de données.  
  
-   Exécutez l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante sur la base de données :  
  
    ```  
    CREATE TABLE BCPDate (cola int, colb datetime);  
    ```  
  
-   Dans le répertoire dans lequel l'application sera exécutée, ajoutez un fichier nommé Bcpfmt.fmt, puis ajoutez le code suivant au fichier :  
  
    ```  
    8.0  
    2  
    1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
    2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
    ```  
  
-   Dans le répertoire dans lequel l'application sera exécutée, ajoutez un fichier nommé Bcpodbc.bcp, puis ajoutez le code suivant au fichier :  
  
    ```  
    1  
    2  
    ```  
  
 Vous êtes à présent prêt à compiler et exécuter le code C++.  
  
```  
// compile with: odbc32.lib sqlncli11.lib  
#include <stdio.h>  
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
  
   // Allocate ODBC connection handle, set BCP mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetConnectAttr(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security. Create SQL Server DSN using Windows NT authentication.  
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Read the format file.  
   retcode = bcp_readfmt(hdbc1, "BCPFMT.fmt");  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_readfmt(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_exec(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied in = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
