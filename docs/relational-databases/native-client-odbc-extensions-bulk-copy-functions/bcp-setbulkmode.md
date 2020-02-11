---
title: bcp_setbulkmode | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bcp_setbulkmode function
ms.assetid: de56f206-1f7e-4c03-bf22-da9c7f9f4433
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 46da93307d28b5be6aec3fbcbff31322e96ea634
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73782397"
---
# <a name="bcp_setbulkmode"></a>bcp_setbulkmode
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  bcp_setbulkmode vous permet de spécifier le format de colonne dans une opération de copie en bloc, en définissant tous les attributs de colonne dans un appel de fonction unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_setbulkmode (  
   HDBC hdbc,  
   INT property,  
   void * pField,  
   INT cbField,  
   void * pRow,  
   INT cbRow  
);  
```  
  
## <a name="arguments"></a>Arguments  
 *hdbc*  
 Descripteur de connexion ODBC compatible avec la copie en bloc.  
  
 *propriété*  
 Constante de type BYTE. Consultez le tableau dans la section Notes pour obtenir une liste des constantes.  
  
 *pField*  
 Pointeur vers la valeur de marque de fin de champ.  
  
 *cbField*  
 Longueur (en octets) de la valeur de marque de fin de champ.  
  
 *pRow*  
 Pointeur vers la valeur de marque de fin de ligne.  
  
 *cbRow*  
 Longueur, en octets, de la valeur de marque de fin de ligne.  
  
## <a name="returns"></a>Retours  
 SUCCEED ou FAIL  
  
## <a name="remarks"></a>Notes  
 bcp_setbulkmode peut être utilisé pour effectuer une copie en bloc à partir d’une requête ou d’une table. Lorsque bcp_setbulkmode est utilisé pour copier en bloc une instruction de requête, il doit être appelé avant d’appeler bcp_control avec BCP_HINT.  
  
 bcp_setbulkmode est une alternative à l’utilisation de [bcp_setcolfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md) et [bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md), qui vous permettent uniquement de spécifier le format d’une colonne par appel de fonction.  
  
 Le tableau suivant répertorie les constantes du paramètre *property* .  
  
|Propriété|Description|  
|--------------|-----------------|  
|BCP_OUT_CHARACTER_MODE|Spécifie le mode de sortie de caractères.<br /><br /> Correspond à l’option-c dans BCP. EXE et pour bcp_setcolfmt avec **BCP_FMT_TYPE** propriété définie sur **SQLCHARACTER**.|  
|BCP_OUT_WIDE_CHARACTER_MODE|Spécifie le mode de sortie Unicode.<br /><br /> Correspond à l’option-w dans BCP. EXE et bcp_setcolfmt avec **BCP_FMT_TYPE** propriété définie sur **SQLNCHAR**.|  
|BCP_OUT_NATIVE_TEXT_MODE|Spécifie des types natifs pour les types de non-caractères et Unicode pour les types de caractères.<br /><br /> Correspond à l’option-N dans BCP. EXE et bcp_setcolfmt avec **BCP_FMT_TYPE** propriété définie sur **SQLNCHAR** si le type de colonne est une chaîne (valeur par défaut, s’il ne s’agit pas d’une chaîne).|  
|BCP_OUT_NATIVE_MODE|Spécifie les types de base de données natifs.<br /><br /> Correspond à l’option-n dans BCP. EXE et bcp_setcolfmt avec **BCP_FMT_TYPE** propriété définie sur la valeur par défaut.|  
  
 Vous ne devez pas utiliser bcp_setbulkmode avec une séquence d’appels de fonction qui comprend bcp_setcolfmt, bcp_control et bcp_readfmt. Par exemple, vous ne devez pas appeler bcp_control (BCPTEXTFILE) et bcp_setbulkmode.  
  
 Vous pouvez appeler bcp_control et bcp_setbulkmode pour les options de bcp_control qui ne sont pas en conflit avec bcp_setbulkmode. Par exemple, vous pouvez appeler bcp_control (BCPFIRST) et bcp_setbulkmode.  
  
 Si vous tentez d’appeler bcp_setbulkmode avec une séquence d’appels de fonction qui comprend bcp_setcolfmt, bcp_control et bcp_readfmt, l’un des appels de fonction retourne un échec de séquence. Si vous choisissez de corriger l’échec, appelez bcp_init pour réinitialiser tous les paramètres et recommencer.  
  
 Voici quelques exemples d’appels de fonction qui génèrent une erreur de séquence de fonction :  
  
```  
bcp_init("table", DB_IN);  
bcp_setbulkmode();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_setbulkmode();  
bcp_readfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPHINTS, "select ...");  
bcp_setbulkmode();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_setbulkmode();  
bcp_setcolfmt();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_readfmt();  
bcp_setcolfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setbulkmode();  
bcp_control(BCPHINTS, "select ...");  
bcp_readfmt();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_columns();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setcolfmt();  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée quatre fichiers à l'aide de différents paramètres de bcp_setbulkmode.  
  
```  
// compile with: sqlncli11.lib odbc32.lib  
  
#include <windows.h>  
#include <stdio.h>  
#include <tchar.h>  
#include <sqlext.h>  
#include "sqlncli.h"  
  
// Global variables  
SQLHENV g_hEnv = NULL;  
SQLHDBC g_hDbc = NULL;  
  
void ODBCCleanUp() {  
   if (g_hDbc) {  
      SQLDisconnect(g_hDbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, g_hDbc);  
      g_hDbc = NULL;  
   }  
   if (g_hEnv) {  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      g_hEnv = NULL;  
   }  
}  
  
BOOL MakeODBCConnection(TCHAR * pszServer) {  
   TCHAR szConnectionString[500];  
   TCHAR szOutConnectionString[500];  
   SQLSMALLINT iLen;  
   SQLRETURN rc;  
  
   _sntprintf_s(szConnectionString, 500, TEXT("DRIVER={SQL Server Native Client 11.0};Server=%s;Trusted_connection=yes;"), pszServer);  
   rc = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE,&g_hEnv);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLAllocHandle(SQL_HANDLE_ENV...) failed\n");  
      return false;  
   }  
   rc = SQLSetEnvAttr(g_hEnv,SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, SQL_IS_UINTEGER);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLSetEnvAttr failed\n");  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      return false;  
   }  
   rc = SQLAllocHandle( SQL_HANDLE_DBC, g_hEnv , &g_hDbc);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLAllocHandle(SQL_HANDLE_DBC...) failed\n");  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      return false;  
   }  
   // Enable BCP  
   rc = SQLSetConnectAttr(g_hDbc, SQL_COPT_SS_BCP, (SQLPOINTER)SQL_BCP_ON, SQL_IS_INTEGER);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLSetConnectAttr(.. SQL_COPT_SS_BCP, (SQLPOINTER)SQL_BCP_ON ...) failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   // connecting ...  
   rc = SQLDriverConnect(g_hDbc,NULL, (SQLTCHAR*)szConnectionString, SQL_NTS, (SQLTCHAR*)szOutConnectionString, 500, &iLen, SQL_DRIVER_NOPROMPT);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLDriverConnect(SQL_HANDLE_DBC...) failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   return true;  
}  
  
BOOL BCPSetBulkMode(TCHAR * pszServer, TCHAR * pszQureryOut, char BCPType, TCHAR * pszDataFile) {  
   SQLRETURN rc;  
  
   if (!MakeODBCConnection(pszServer))  
      return false;  
   rc = bcp_init(g_hDbc, NULL, pszDataFile, NULL, DB_OUT);   // bcp init for queryout  
   if (SUCCEED != rc) {  
      printf("bcp_init failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   // setbulkmode  
   char ColTerm[] = "\t";  
   char RowTerm[] = "\r\n";  
   wchar_t wColTerm[] = L"\t";  
   wchar_t wRowTerm[] = L"\r\n";  
   BYTE * pColTerm = NULL;  
   int cbColTerm = NULL;  
   BYTE * pRowTerm = 0;  
   int cbRowTerm = 0;  
   int bulkmode = -1;  
  
   if (BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if (BCPType == 'w') {   // bcp -w   
         pColTerm = (BYTE*)wColTerm;  
         pRowTerm = (BYTE*)wRowTerm;  
         cbColTerm = 2;  
         cbRowTerm = 4;  
         bulkmode = BCP_OUT_WIDE_CHARACTER_MODE;  
      }  
      else  
         if (BCPType == 'n')   // bcp -n  
            bulkmode = BCP_OUT_NATIVE_MODE;  
         else  
            if (BCPType == 'N')   // bcp -n  
               bulkmode = BCP_OUT_NATIVE_TEXT_MODE;  
            else {  
               printf("unknown bcp mode\n");  
               ODBCCleanUp();  
               return false;  
            }  
            rc = bcp_setbulkmode(g_hDbc, bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (SUCCEED != rc) {  
               printf("bcp_setbulkmode failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            // set queryout TSQL statement  
            rc = bcp_control(g_hDbc, BCPHINTS , pszQureryOut);  
            if (SUCCEED != rc) {  
               printf("bcp_control(..BCP_OPTION_HINTS..) failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBINT nRowsInserted = 0;  
            rc = bcp_exec(g_hDbc, &nRowsInserted);  
            if (SUCCEED != rc) {  
               printf("bcp_exec failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            ODBCCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', TEXT("bcpc.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', TEXT("bcpw.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', TEXT("bcpn.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', TEXT("bcp_N.dat"));  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
