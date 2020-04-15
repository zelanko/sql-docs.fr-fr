---
title: Fonction SQLFreeStmt (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFreeStmt
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFreeStmt
helpviewer_keywords:
- SQLFreeStmt function [ODBC]
ms.assetid: 03408162-8b63-4470-90c4-e6c7d8d33892
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e252769c26a5491100094b1243b9c2c6bb67d94d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285699"
---
# <a name="sqlfreestmt-function"></a>Fonction SQLFreeStmt
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLFreeStmt** arrête le traitement associé à une déclaration spécifique, ferme tous les curseurs ouverts associés à l’instruction, écarte les résultats en attente, ou, par option, libère toutes les ressources associées à la poignée de déclaration.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLFreeStmt(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Option);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration  
  
 *Option*  
 [Entrée] L’une des options suivantes :  
  
 SQL_ CLOSE : Ferme le curseur associé à *StatementHandle* (si l’on a été défini) et rejette tous les résultats en attente. L’application peut rouvrir ce curseur plus tard en exécutant une déclaration **SELECT** à nouveau avec les mêmes valeurs de paramètres ou différentes. Si aucun curseur n’est ouvert, cette option n’a aucun effet pour l’application. **SQLCloseCursor** peut également être appelé pour fermer un curseur. Pour plus d’informations, voir [Closing the Cursor](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
 SQL_DROP: Cette option est dépréciée. Un appel à **SQLFreeStmt** avec une *option* de SQL_DROP est cartographié dans le Driver Manager à [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
 SQL_UNBIND: Définit le champ SQL_DESC_COUNT de l’ARD à 0, libérant tous les tampons de colonne liés par **SQLBindCol** pour le *StatementHandle*donné . Cela ne déliera pas la colonne de signets; pour ce faire, le champ SQL_DESC_DATA_PTR de l’ARD pour la colonne de signets est réglé à NULL. Notez que si cette opération est effectuée sur un descripteur explicitement attribué qui est partagé par plus d’une déclaration, l’opération aura une incidence sur les liaisons de toutes les déclarations qui partagent le descripteur. Pour plus d’informations, voir [Aperçu des résultats de récupération (de base)](../../../odbc/reference/develop-app/retrieving-results-basic.md).  
  
 SQL_RESET_PARAMS: Définit le champ SQL_DESC_COUNT de l’APD à 0, libérant tous les paramètres tampons définis par **SQLBindParameter** pour le *StatementHandle*donné . Si cette opération est effectuée sur un descripteur explicitement attribué qui est partagé par plus d’une déclaration, cette opération aura une incidence sur les liaisons de toutes les déclarations qui partagent le descripteur. Pour plus d’informations, voir [Paramètres contraignants](../../../odbc/reference/develop-app/binding-parameters-odbc.md).  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLFreeStmt** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLFreeStmt** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque **SQLFreeStmt** a été appelé.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avec *Option* set to SQL_RESET_PARAMS avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY092 HY092|Type d’option hors de portée|(DM) La valeur spécifiée pour l’argument *Option* n’était pas :<br /><br /> SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Appeler **SQLFreeStmt** avec l’option SQL_CLOSE équivaut à appeler **SQLCloseCursor**, sauf que **SQLFreeStmt** avec SQL_CLOSE n’affecte pas l’application si aucun curseur n’est ouvert sur la déclaration. Si aucun curseur n’est ouvert, un appel à **SQLCloseCursor** renvoie SQLSTATE 24000 (État de curseur invalide).  
  
 Une application ne doit pas utiliser une poignée de déclaration après sa libération; le gestionnaire de conducteur ne vérifie pas la validité d’une poignée dans un appel de fonction.  
  
## <a name="example"></a>Exemple  
 C’est une bonne pratique de programmation pour les poignées gratuites. Toutefois, pour plus de simplicité, l’échantillon suivant n’inclut pas le code qui libère les poignées allouées. Pour un exemple de la façon de libérer les poignées, voir [SQLFreeHandle Function](../../../odbc/reference/syntax/sqlfreehandle-function.md).  
  
```cpp  
// SQLFreeStmt.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   // declare and initialize the environment, connection, statement handles  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1024 + 1, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
   retCode = SQLFreeStmt(hstmt, SQL_UNBIND);  
   retCode = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);  
}  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Répartition d’une poignée|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Fermeture d’un curseur|[SQLCloseCursor, fonction](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|Libérer une poignée|[Fonction SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Définir un nom de curseur|[SQLSetCursorName, fonction](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
