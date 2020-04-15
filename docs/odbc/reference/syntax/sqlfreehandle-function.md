---
title: Fonction SQLFreeHandle (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFreeHandle
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFreeHandle
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
ms.assetid: 17a6fcdc-b05a-4de7-be93-a316f39696a1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0b136dec98a19676aa67c78615d8fe931f62aafa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285770"
---
# <a name="sqlfreehandle-function"></a>Fonction SQLFreeHandle
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLFreeHandle** libère les ressources associées à un environnement, une connexion, une déclaration ou une poignée descripteur spécifiques.  
  
> [!NOTE]
>  Cette fonction est une fonction générique pour libérer les poignées. Il remplace les fonctions ODBC 2.0 **SQLFreeConnect** (pour libérer une poignée de connexion) et **SQLFreeEnv** (pour libérer une poignée d’environnement). **SQLFreeConnect** et **SQLFreeEnv** sont tous deux dépréciés dans ODBC 3 *.x*. **SQLFreeHandle** remplace également la fonction ODBC 2.0 **SQLFreeStmt** (avec *l’option*SQL_DROP) pour libérer une poignée de déclaration. Pour plus d’informations, voir "Commentaires". Pour plus d’informations sur ce que le Gestionnaire de conducteur cartographie cette fonction à quand une application ODBC 3 *.x* travaille avec un pilote ODBC 2 *.x,* voir [Mapping Replacement Functions for Backward Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Le type de poignée à libérer par **SQLFreeHandle**. Il doit s’agir de l’une des valeurs suivantes :   
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN poignée n’est utilisée que par le Gestionnaire du conducteur et le conducteur. Les applications ne doivent pas utiliser ce type de poignée. Pour plus d’informations sur SQL_HANDLE_DBC_INFO_TOKEN, voir [Developing Connection-Pool Awareness in an ODBC Driver](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 Si *HandleType* n’est pas l’une de ces valeurs, **SQLFreeHandle** revient SQL_INVALID_HANDLE.  
  
 *Handle*  
 [Entrée] Le manche à libérer.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_ERROR, ou SQL_INVALID_HANDLE.  
  
 Si **SQLFreeHandle** retourne SQL_ERROR, la poignée est toujours valide.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLFreeHandle** retourne SQL_ERROR, une valeur SQLSTATE associée peut être obtenue à partir de la structure de données diagnostiques pour la poignée que **SQLFreeHandle** a essayé de libérer, mais ne pouvait pas. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLFreeHandle** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) *L’argument de HandleType* était SQL_HANDLE_ENV, et au moins une connexion se trouvait dans un état attribué ou connecté. **SQLDisconnect** et **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DBC doivent être appelés pour chaque connexion avant d’appeler **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_ENV.<br /><br /> (DM) *L’argument de HandleType* était SQL_HANDLE_DBC, et la fonction a été appelée avant d’appeler **SQLDisconnect** pour la connexion.<br /><br /> (DM) L’argument *de HandleType* était SQL_HANDLE_DBC. Une fonction d’exécution asynchrone a été appelée avec *poignée* et la fonction était toujours en exécution quand cette fonction a été appelée.<br /><br /> (DM) *L’argument de HandleType* était SQL_HANDLE_STMT. **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé avec la poignée de déclaration et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.<br /><br /> (DM) *L’argument de HandleType* était SQL_HANDLE_STMT. Une fonction d’exécution asynchrone a été appelée sur la poignée de déclaration ou sur la poignée de connexion associée et la fonction était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) *L’argument de HandleType* était SQL_HANDLE_DESC. Une fonction d’exécution asynchrone a été appelée sur la poignée de connexion associée; et la fonction était encore en cours d’exécution lorsque cette fonction a été appelée.<br /><br /> (DM) Toutes les poignées de filiales et autres ressources n’ont pas été libérées avant **l’appel de SQLFreeHandle.**<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour l’une des poignées de déclaration associées à la *poignée* et *HandleType* a été mis à SQL_HANDLE_STMT ou SQL_HANDLE_DESC retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.|  
|HY013|Erreur de gestion de la mémoire|*L’argument de HandleType* était SQL_HANDLE_STMT ou SQL_HANDLE_DESC, et l’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents ne pouvaient pas être consultés, peut-être en raison de conditions de mémoire basses.|  
|HY017|Utilisation invalide d’une poignée descripteur automatiquement allouée.|(DM) *L’argument de la poignée* a été réglé à la poignée pour un descripteur automatiquement attribué.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) L’argument *de HandleType* était SQL_HANDLE_DESC, et le conducteur était un conducteur ODBC 2 *.x.*<br /><br /> (DM) L’argument *de HandleType* était SQL_HANDLE_STMT, et le conducteur n’était pas un conducteur valide de l’ODBC.|  
  
## <a name="comments"></a>Commentaires  
 **SQLFreeHandle** est utilisé pour libérer les poignées pour les environnements, les connexions, les déclarations et les descripteurs, comme décrit dans les sections suivantes. Pour plus d’informations générales sur les poignées, voir [Poignées](../../../odbc/reference/develop-app/handles.md).  
  
 Une application ne doit pas utiliser une poignée après sa libération; le gestionnaire de conducteur ne vérifie pas la validité d’une poignée dans un appel de fonction.  
  
## <a name="freeing-an-environment-handle"></a>Libérer une poignée d’environnement  
 Avant d’appeler **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_ENV, une application doit appeler **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DBC pour toutes les connexions allouées dans l’environnement. Sinon, l’appel à **SQLFreeHandle renvoie** SQL_ERROR et l’environnement et toute connexion active reste valide. Pour plus d’informations, voir [Environment Handles](../../../odbc/reference/develop-app/environment-handles.md) et [Allouer la poignée environnement](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Si l’environnement est un environnement partagé, l’application qui appelle **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_ENV n’a plus accès à l’environnement après l’appel, mais les ressources de l’environnement ne sont pas nécessairement libérées. L’appel à **SQLFreeHandle** décréte le nombre de références de l’environnement. Le compte de référence est maintenu par le gestionnaire de conducteur. S’il n’atteint pas zéro, l’environnement partagé n’est pas libéré, car il est toujours utilisé par un autre composant. Si le nombre de références atteint zéro, les ressources de l’environnement partagé sont libérées.  
  
## <a name="freeing-a-connection-handle"></a>Libérer une poignée de connexion  
 Avant d’appeler **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DBC, une application doit appeler **SQLDisconnect** pour la connexion s’il ya une connexion sur cette poignée *.* Dans le cas contraire, l’appel à **SQLFreeHandle renvoie** SQL_ERROR et la connexion reste valide.  
  
 Pour plus d’informations, voir [Connection Handles](../../../odbc/reference/develop-app/connection-handles.md) et [Disconnecting from a Data Source ou Driver](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="freeing-a-statement-handle"></a>Libération d'un descripteur d'instruction  
 Un appel à **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_STMT libère toutes les ressources qui ont été allouées par un appel à **SQLAllocHandle** avec un *HandleType* de SQL_HANDLE_STMT. Lorsqu’une application appelle **SQLFreeHandle** pour libérer une déclaration qui a des résultats en attente, les résultats en attente sont supprimés. Lorsqu’une application libère une poignée de relevé, le conducteur libère les quatre descripteurs automatiquement attribués associés à cette poignée. Pour plus d’informations, voir [Poignées de déclaration](../../../odbc/reference/develop-app/statement-handles.md) et [libérer une poignée de déclaration](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 Notez que **SQLDisconnect** laisse automatiquement tomber toutes les instructions et les descripteurs ouverts sur la connexion.  
  
## <a name="freeing-a-descriptor-handle"></a>Libérer une poignée descripteur  
 Un appel à **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DESC libère la poignée descripteur dans *Handle*. L’appel à **SQLFreeHandle** ne libère aucune mémoire allouée par l’application qui peut être référencée par un champ de pointeur (y compris SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR) de tout dossier descripteur de *Poignée*. La mémoire allouée par le conducteur pour les champs qui ne sont pas des champs pointeurs est libérée lorsque la poignée est libérée. Lorsqu’une poignée descripteur allouée par l’utilisateur est libérée, toutes les déclarations auxquelles la poignée libérée a été associée sont revenues à leurs poignées descripteur allouées automatiquement respectives.  
  
> [!NOTE]
>  Les conducteurs ODBC 2 *.x* ne prennent pas en charge la libération des poignées descripteur, tout comme ils ne prennent pas en charge l’attribution des poignées descripteur.  
  
 Notez que **SQLDisconnect** laisse automatiquement tomber toutes les instructions et les descripteurs ouverts sur la connexion. Lorsqu’une application libère une poignée de relevé, le conducteur libère tous les descripteurs générés automatiquement associés à cette poignée.  
  
 Pour plus d’informations sur les descripteurs, voir [Descriptors](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Exemple de code  
 Pour des échantillons de code supplémentaires, voir [SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) et [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
### <a name="code"></a>Code  
  
```cpp  
// SQLFreeHandle.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <stdio.h>  
  
int main() {  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
  
   // Initialize the environment, connection, statement handles.  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   // Allocate the environment.  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set environment attributes.  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
  
   // Allocate the connection.  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
   // Set the login timeout.  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
  
   // Let the user select the data source and connect to the database.  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // Free handles, and disconnect.     
   if (hstmt) {   
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
      hstmt = NULL;   
   }  
   if (hdbc) {   
      SQLDisconnect(hdbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
      hdbc = NULL;   
   }  
   if (henv) {   
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
      henv = NULL;   
   }  
}  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Répartition d’une poignée|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Annulation du traitement des relevés|[Fonction DE SQLCance](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Définir un nom de curseur|[SQLSetCursorName, fonction](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Exemple de programme ODBC](../../../odbc/reference/sample-odbc-program.md)
