---
title: SQLFreeHandle, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFreeHandle
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFreeHandle
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
ms.assetid: 17a6fcdc-b05a-4de7-be93-a316f39696a1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f63af414d59afed2bbe2e8eed3fba7a1362bb4bb
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53203908"
---
# <a name="sqlfreehandle-function"></a>Fonction SQLFreeHandle
**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 **SQLFreeHandle** libère les ressources associées à un descripteur d’environnement, connexion, instruction ou descripteur spécifique.  
  
> [!NOTE]
>  Cette fonction est une fonction générique de libérer les handles. Il remplace les fonctions ODBC 2.0 **SQLFreeConnect** (pour libérer un handle de connexion) et **SQLFreeEnv** (pour libérer un handle d’environnement). **SQLFreeConnect** et **SQLFreeEnv** sont déconseillés dans ODBC 3 *.x*. **SQLFreeHandle** remplace également la fonction ODBC 2.0 **SQLFreeStmt** (avec le SQL_DROP *Option*) de libérer un descripteur d’instruction. Pour plus d’informations, consultez « Commentaires ». Pour plus d’informations sur ce que le Gestionnaire de pilotes mappe cette fonction lorsqu’un ODBC 3 *.x* application fonctionne avec un ODBC 2 *.x* pilote, consultez [mappage des fonctions de remplacement pour vers l’arrière Compatibilité des Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>Arguments  
 *HandleType*  
 [Entrée] Le type de handle à libérer par **SQLFreeHandle**. Doit être une des valeurs suivantes :  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 Handle SQL_HANDLE_DBC_INFO_TOKEN est utilisée uniquement par le Gestionnaire de pilotes et le pilote. Applications ne doivent pas utiliser ce type de handle. Pour plus d’informations sur SQL_HANDLE_DBC_INFO_TOKEN, consultez [développer la reconnaissance des pools de connexion dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
 Si *HandleType* ne fait pas partie de ces valeurs, **SQLFreeHandle** retourne SQL_INVALID_HANDLE.  
  
 *Handle*  
 [Entrée] Le handle à libérer.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
 Si **SQLFreeHandle** retourne SQL_ERROR, le handle est toujours valide.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLFreeHandle** retourne SQL_ERROR, une valeur SQLSTATE associée peut être obtenu à partir de la structure de données de diagnostic pour le handle qui **SQLFreeHandle** a tenté de libérer mais n’était pas possible. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLFreeHandle** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer de la mémoire qui est nécessaire pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) le *HandleType* argument était SQL_HANDLE_ENV et au moins une connexion était dans un état connecté ou non alloué. **SQLDisconnect** et **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DBC doit être appelée pour chaque connexion avant d’appeler **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_ENV.<br /><br /> (DM) le *HandleType* argument était SQL_HANDLE_DBC et la fonction a été appelée avant d’appeler **SQLDisconnect** pour la connexion.<br /><br /> (DM) le *HandleType* SQL_HANDLE_DBC a été l’argument. Une fonction d’exécution asynchrone a été appelée avec *gérer* et la fonction s’exécute toujours quand cette fonction a été appelée.<br /><br /> (DM) le *HandleType* SQL_HANDLE_STMT a été l’argument. **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelée avec le descripteur d’instruction et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.<br /><br /> (DM) le *HandleType* SQL_HANDLE_STMT a été l’argument. Une fonction d’exécution asynchrone a été appelée sur le descripteur d’instruction ou sur le handle de connexion associé et la fonction s’exécute toujours quand cette fonction a été appelée.<br /><br /> (DM) le *HandleType* SQL_HANDLE_DESC a été l’argument. Une fonction d’exécution asynchrone a été appelée sur le handle de connexion associé ; et la fonction s’exécute toujours quand cette fonction a été appelée.<br /><br /> (DM) gère toutes les filiales et autres ressources publiées pas avant **SQLFreeHandle** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelée pour l’une des descripteurs d’instruction associés à la *gérer* et *HandleType* a été défini à SQL_HANDLE_STMT ou SQL_HANDLE_DESC retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.|  
|HY013|Erreur de gestion de mémoire|Le *HandleType* argument était SQL_HANDLE_STMT ou SQL_HANDLE_DESC, et l’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY017|Utilisation non valide d’un handle de descripteur alloué automatiquement.|(DM) le *gérer* argument a été défini sur le handle pour un descripteur alloué automatiquement.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|(DM) le *HandleType* SQL_HANDLE_DESC a été l’argument et le pilote a été un ODBC 2 *.x* pilote.<br /><br /> (DM) le *HandleType* SQL_HANDLE_STMT a été l’argument et le pilote n’a pas un pilote ODBC valid.|  
  
## <a name="comments"></a>Commentaires  
 **SQLFreeHandle** est utilisée pour libérer les handles pour les environnements, les connexions, les instructions et les descripteurs, comme décrit dans les sections suivantes. Pour obtenir des informations générales sur les descripteurs, consultez [Handles](../../../odbc/reference/develop-app/handles.md).  
  
 Une application ne doit pas utiliser un handle après que qu’il a été libéré ; le Gestionnaire de pilotes ne vérifie pas la validité d’une poignée dans un appel de fonction.  
  
## <a name="freeing-an-environment-handle"></a>Libération d’un Handle d’environnement  
 Avant d’appeler **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_ENV, une application doit appeler **SQLFreeHandle** avec un *HandleType*de SQL_HANDLE_DBC pour toutes les connexions attribuées dans l’environnement. Sinon, l’appel à **SQLFreeHandle** retourne SQL_ERROR et de l’environnement et de toute connexion active reste valide. Pour plus d’informations, consultez [environnement gère](../../../odbc/reference/develop-app/environment-handles.md) et [allouer le Handle d’environnement](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 Si l’environnement est un environnement partagé, l’application qui appelle **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_ENV n’a plus accès à l’environnement après l’appel, mais l’environnement ressources ne sont pas nécessairement libérées. L’appel à **SQLFreeHandle** décrémente le décompte de références de l’environnement. Le décompte de références est conservé par le Gestionnaire de pilotes. Si elle ne parvient pas à zéro, l’environnement partagé n’est pas libéré, car il est toujours utilisé par un autre composant. Si le décompte de références atteint zéro, les ressources de l’environnement partagé sont libérées.  
  
## <a name="freeing-a-connection-handle"></a>Libération d’un descripteur de connexion  
 Avant d’appeler **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DBC, une application doit appeler **SQLDisconnect** pour la connexion s’il existe une connexion sur ce gérer *.* Sinon, l’appel à **SQLFreeHandle** retourne SQL_ERROR et la connexion reste valide.  
  
 Pour plus d’informations, consultez [Handles de connexion](../../../odbc/reference/develop-app/connection-handles.md) et [déconnexion d’une Source de données ou le pilote](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
## <a name="freeing-a-statement-handle"></a>Libération d'un descripteur d'instruction  
 Un appel à **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_STMT libère toutes les ressources qui ont été alloués par un appel à **SQLAllocHandle** avec un  *HandleType* de SQL_HANDLE_STMT. Lorsqu’une application appelle **SQLFreeHandle** pour libérer une instruction qui a des résultats en attente, les résultats en attente sont supprimés. Lorsqu’une application libère un descripteur d’instruction, il libère les descripteurs alloués automatiquement quatre associés à ce handle. Pour plus d’informations, consultez [instruction gère](../../../odbc/reference/develop-app/statement-handles.md) et [libération d’un Handle d’instruction](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 Notez que **SQLDisconnect** supprime automatiquement les instructions et les descripteurs ouverts sur la connexion.  
  
## <a name="freeing-a-descriptor-handle"></a>Libération d’un Handle de descripteur  
 Un appel à **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_DESC libère le handle de descripteur dans *gérer*. L’appel à **SQLFreeHandle** ne libère pas de mémoire allouée par l’application qui peut-être être référencée par un champ de pointeur (y compris les SQL_DESC_DATA_PTR, SQL_DESC_INDICATOR_PTR et SQL_DESC_OCTET_LENGTH_PTR) de n’importe quel enregistrement de descripteur de *gérer*. La mémoire allouée par le pilote pour les champs qui ne sont pas des champs de pointeur est libérée lorsque le handle est libéré. Lorsqu’un handle de descripteur alloué par l’utilisateur est libéré, toutes les instructions qui le handle libéré avait été associé à revenir à leurs handles de descripteur alloué automatiquement respectifs.  
  
> [!NOTE]
>  ODBC 2 *.x* pilotes ne prennent pas en charge la libération des handles de descripteur, comme ils ne prennent pas en charge les allouer des handles de descripteur.  
  
 Notez que **SQLDisconnect** supprime automatiquement les instructions et les descripteurs ouverts sur la connexion. Lorsqu’une application libère un descripteur d’instruction, il libère tous les descripteurs de généré automatiquement associés à ce handle.  
  
 Pour plus d’informations sur les descripteurs, consultez [descripteurs](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="code-example"></a>Exemple de code  
 Pour obtenir des exemples de code supplémentaire, consultez [SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) et [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
### <a name="code"></a>Code  
  
```  
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
|Allocation d’un handle|[SQLAllocHandle, fonction](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|Annulation de traitement d’instruction|[SQLCance Functionl](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Définition d’un nom de curseur|[SQLSetCursorName, fonction](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Exemple de programme ODBC](../../../odbc/reference/sample-odbc-program.md)
