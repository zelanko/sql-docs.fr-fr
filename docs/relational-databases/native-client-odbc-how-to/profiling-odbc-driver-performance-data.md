---
title: Données de performances du pilote de profil (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- driver performance data [ODBC]
ms.assetid: b997790a-8cc6-4800-8867-74c1bef07be3
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: df90080d0c07b87d646c7c67cbe1fd672a2a582f
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73780662"
---
# <a name="profiling-odbc-driver-performance-data"></a>Profilage des données de performances du pilote ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cet exemple présente les options [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifiques aux pilotes ODBC et destinées à l'enregistrement des statistiques de performances. L’exemple crée un fichier : odbcperf. log. cet exemple illustre la création d’un fichier journal de données de performances et l’affichage des données de performances directement à partir de la structure de données SQLPERF (la structure SQLPERF est définie dans odbcss. h.). Cet exemple a été développé pour la version 3.0 d'ODBC ou une version ultérieure.  
  
> [!IMPORTANT]  
>  Lorsque c'est possible, utilisez l'authentification Windows. Si l'authentification Windows n'est pas disponible, invitez les utilisateurs à entrer leurs informations d'identification au moment de l'exécution. Évitez de stocker ces informations dans un fichier. Si vous devez rendre les informations d'identification persistantes, chiffrez-les avec l' [API de chiffrement Win32](https://go.microsoft.com/fwlink/?LinkId=64532).  
  
### <a name="to-log-driver-performance-data-using-odbc-administrator"></a>Pour enregistrer les données de performances du pilote à l'aide de l'Administrateur ODBC  
  
1.  Dans **le panneau de configuration**, double-cliquez sur **Outils d’administration** , puis sur **sources de données (ODBC)** . Vous pouvez également appeler l'exécutable odbcad32.exe.  
  
2.  Cliquez sur l’onglet **DSN utilisateur**, **système DSN**ou **fichier DSN** .  
  
3.  Cliquez sur la source de données dont vous souhaitez consigner les performances.  
  
4.  Cliquez sur **configurer**.  
  
5.  Dans l’Assistant Microsoft SQL Server configurer un DSN, accédez à la page contenant les **statistiques du pilote ODBC du journal dans le fichier journal**.  
  
6.  Sélectionnez **enregistrer les statistiques du pilote ODBC dans le fichier journal**. Dans la zone, tapez le nom du fichier dans lequel les statistiques sont à enregistrer. Si vous le souhaitez, cliquez sur **Parcourir** pour rechercher le journal des statistiques dans le système de fichiers.  
  
### <a name="to-log-driver-performance-data-programmatically"></a>Pour enregistrer les données de performances du pilote par programme  
  
1.  Appelez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) avec SQL_COPT_SS_PERF_DATA_LOG et le chemin d’accès complet et le nom du fichier journal des données de performances. Par exemple :  
  
    ```  
    "C:\\Odbcperf.log"  
    ```  
  
2.  Appelez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) avec SQL_COPT_SS_PERF_DATA et SQL_PERF_START pour commencer l’enregistrement des données de performances.  
  
3.  Vous pouvez également appeler [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) avec SQL_COPT_SS_LOG_NOW et null pour écrire un enregistrement délimité par des tabulations de données de performances dans le fichier journal des données de performances. Vous pouvez effectuer plusieurs fois cette opération en cours d'exécution de l'application.  
  
4.  Appelez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) avec SQL_COPT_SS_PERF_DATA et SQL_PERF_STOP pour arrêter l’enregistrement des données de performances.  
  
### <a name="to-pull-driver-performance-data-into-an-application"></a>Pour extraire les données de performances du pilote dans une application  
  
1.  Appelez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) avec SQL_COPT_SS_PERF_DATA et SQL_PERF_START pour démarrer le profilage des données de performances.  
  
2.  Appelez [SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) avec SQL_COPT_SS_PERF_DATA et l’adresse d’un pointeur vers une structure SQLPERF. Le premier appel définit le pointeur sur l'adresse d'une structure SQLPERF valide qui contient les données de performances actuelles. Le pilote n'actualise pas en permanence les données dans la structure de performance. L’application doit répéter l’appel à [SQLGetConnectAttr](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) chaque fois qu’elle a besoin d’actualiser la structure avec des données de performances plus récentes.  
  
3.  Appelez [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) avec SQL_COPT_SS_PERF_DATA et SQL_PERF_STOP pour arrêter l’enregistrement des données de performances.  
  
## <a name="example"></a>Exemple  
 Vous aurez besoin d'une source de données ODBC nommée AdventureWorks, dont la base de données par défaut est l'exemple de base de données AdventureWorks. (Vous pouvez télécharger l’exemple de base de données AdventureWorks à partir de la page d’hébergement [exemples et projets de la communauté Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkID=85384) .) Cette source de données doit être basée sur le pilote ODBC fourni par le système d’exploitation (le nom du pilote est « SQL Server »). Si vous générez et exécutez cet exemple comme une application 32 bits sur un système d'exploitation 64 bits, vous devez créer la source de données ODBC avec l'administrateur ODBC dans %windir%\SysWOW64\odbcad32.exe.  
  
 Cet exemple vous permet de vous connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par défaut de votre ordinateur. Pour vous connecter à une instance nommée, modifiez la définition de la source de données ODBC pour spécifier l'instance en utilisant le format suivant : serveur\namedinstance. Par défaut, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] est installé dans une instance nommée.  
  
 Compilez avec odbc32.lib.  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // Pointer to the ODBC driver performance structure.  
   SQLPERF *PerfPtr;  
   SQLINTEGER cbPerfPtr;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // This sample use Integrated Security. Please create the SQL Server   
   // DSN by using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log performance statistics.  Specify file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG, &"odbcperf.log", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the performance statistics log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle, then execute command.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Write current statistics to the performance log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG_NOW, (SQLPOINTER)NULL, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Get pointer to current SQLPerf structure.  
   // Print a couple of statistics.  
   retcode =   
      SQLGetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)&PerfPtr, SQL_IS_POINTER, &cbPerfPtr);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLGetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("SQLSelects = %d, SQLSelectRows = %d\n", PerfPtr->SQLSelects, PerfPtr->SQLSelectRows);  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives &#40;au profilage des performances du&#41; pilote ODBC  ODBC](../../relational-databases/native-client-odbc-how-to/profiling-odbc-driver-performance-odbc.md)  
 [Profilage des données de performances du pilote ODBC](../../relational-databases/native-client/odbc/profiling-odbc-driver-performance.md)  
  
  
