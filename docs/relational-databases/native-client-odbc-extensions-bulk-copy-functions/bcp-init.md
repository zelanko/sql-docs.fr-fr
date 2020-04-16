---
title: bcp_init Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_init
- bcp_initW
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_init function
ms.assetid: 6a25862c-7f31-4873-ab65-30f3abde89d2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9b8e40091f88c4e9fc739f125a2e44715e62c9ee
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "73782688"
---
# <a name="bcp_init"></a>bcp_init
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Initialise l'opération de copie en bloc.  

## <a name="syntax"></a>Syntaxe  
  
```  
RETCODE bcp_init (  
        HDBC hdbc,  
        LPCTSTR szTable,  
        LPCTSTR szDataFile,  
        LPCTSTR szErrorFile,  
        INT eDirection);  
```  

Unicode et ANSI nomment:
- bcp_initA (ANSI)
- bcp_initW (Unicode)

## <a name="arguments"></a>Arguments  
 *hdbc*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *szTable*  
 Nom de la table de base de données depuis ou vers laquelle s'effectue la copie. Ce nom peut aussi inclure le nom de la base de données ou le nom du propriétaire. Par exemple, **pubs.gracie.titles**, **pubs.. titres**, **gracie.titles**, et **les titres** sont tous des noms de table légaux.  
  
 Si *eDirection* est DB_OUT, *szTable* peut également être le nom d’une vue de base de données.  
  
 Si *eDirection* est DB_OUT et qu’une instruction SELECT est spécifiée à [l’aide de bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) avant [bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) est appelée, **bcp_init** *szTable* doit être réglé à NULL.  
  
 *szDataFile*  
 Nom du fichier utilisateur depuis ou vers lequel s'effectue la copie. Si les données sont copiées directement à partir de variables en utilisant [bcp_sendrow,](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)définissez *szDataFile* à NULL.  
  
 *szErrorFile*  
 Nom du fichier d'erreurs à remplir avec les messages de progression, les messages d'erreur et les copies des lignes qui, pour quelque raison que ce soit, n'ont pas pu être copiées d'un fichier utilisateur vers une table. Si NULL est passé sous *forme de szErrorFile*, aucun fichier d’erreur n’est utilisé.  
  
 *eDirection*  
 Direction de la copie, DB_IN ou DB_OUT. DB_IN indique la copie de variables de programme ou d'un fichier utilisateur dans une table. DB_OUT indique la copie d'une table de base de données dans un fichier utilisateur. Vous devez spécifier un nom de fichier utilisateur avec DB_OUT.  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 Appelez **bcp_init** avant d’appeler toute autre fonction de copie en vrac. **bcp_init** effectue les initialisations nécessaires pour une copie en vrac [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]des données entre le poste de travail et .  
  
 La fonction **bcp_init** doit être dotée d’une poignée de connexion ODBC activée pour une utilisation avec des fonctions de copie en vrac. Pour activer la poignée, utilisez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) avec SQL_COPT_SS_BCP réglé pour SQL_BCP_ON sur une poignée de connexion allouée, mais non connectée. La tentative d'assigner l'attribut sur un handle connecté provoque une erreur.  
  
 Lorsqu’un fichier de données est spécifié, **bcp_init** examine la structure de la source de la base de données ou du tableau cible, et non le fichier de données. **bcp_init** spécifie les valeurs de format de données du fichier de données en fonction de chaque colonne dans le tableau de base de données, la vue ou l’ensemble de résultats SELECT. Cette spécification inclut le type de données de chaque colonne, la présence ou l'absence d'un indicateur de longueur ou null et des chaînes d'octet de terminateur dans les données, et la largeur des types de données de longueur fixe. **bcp_init** définit ces valeurs comme suit :  
  
-   Le type de données spécifié est le type de données de la colonne dans la table de base de données, la vue ou le jeu de résultats SELECT. Le type de données est énuméré par les types de données natifs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiés dans sqlncli.h. Les données elles-mêmes sont représentées dans leur forme informatique. Autrement dit, les données d’une colonne de type de données **integer** est représentée par une séquence de quatre byte qui est grand ou peu-endian basé sur l’ordinateur qui a créé le fichier de données.  
  
-   Si un type de données de base de données est de longueur fixe, les données du fichier de données sont également de longueur fixe. Fonctions de copie en vrac qui traitent les données (par exemple, [bcp_exec)](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)analysent les lignes de données en s’attendant à ce que la longueur des données du fichier de données soit identique à la longueur des données spécifiées dans le tableau de base de données, la vue ou la liste de colonnes SELECT. Par exemple, les données d’une colonne de base de données définies comme **char(13)** doivent être représentées par 13 caractères pour chaque rangée de données dans le fichier. Les données de longueur fixe peuvent être préfixées avec un indicateur null si la colonne de base de données autorise les valeurs NULL.  
  
-   Lorsque la séquence d'octet de terminateur est définie, la longueur de la séquence d'octet de terminateur est définie avec la valeur 0.  
  
-   Lors de la copie vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le fichier de données doit avoir les données de chaque colonne de la table de base de données. Lors de la copie depuis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les données de toutes les colonnes de la table de base de données, de la vue ou du jeu de résultats SELECT, sont copiées vers le fichier de données.  
  
-   Lors de la copie vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la position ordinale d'une colonne du fichier de données doit être identique à la position ordinale de la colonne de la table de base de données. Lors de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]la copie à partir de , **bcp_exec** place des données en fonction de la position ordinaire de la colonne dans le tableau de base de données.  
  
-   Si un type de données de base de données est de longueur variable (par exemple, **varbinaire(22)**) ou si une colonne de base de données peut contenir des valeurs nulles, les données du fichier de données sont préfixées par un indicateur de longueur/null. La largeur de l'indicateur varie selon le type de données et la version de la copie en bloc.  
  
 Pour modifier les valeurs de format de données spécifiées pour un fichier de données, appelez [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) et [bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md).  
  
 Les copies en bloc vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être optimisées pour les tables qui ne contiennent pas d'index en définissant le mode de récupération de base de données avec la valeur SIMPLE ou BULK_LOGGED. Pour plus d’informations, voir [Conditions préalables pour l’enregistrement minimal en vrac Import](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md) et ALTER [DATABASE](../../t-sql/statements/alter-database-transact-sql.md).  
  
 Si aucun fichier de données n’est utilisé, vous devez appeler [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) pour spécifier le format [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l’emplacement en mémoire des données pour chaque colonne, puis copier des lignes de données à l’aide [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md).  
  
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
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
