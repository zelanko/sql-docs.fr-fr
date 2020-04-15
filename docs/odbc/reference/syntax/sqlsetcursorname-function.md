---
title: Fonction SQLSetCursorName (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetCursorName
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetCursorName
helpviewer_keywords:
- SQLSetCursorName function [ODBC]
ms.assetid: 4e055946-12d4-4589-9891-41617a50f34e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6a3bcd07a39401d49be04d141e50c671179efb16
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287339"
---
# <a name="sqlsetcursorname-function"></a>SQLSetCursorName, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLSetCursorName** associe un nom de curseur à une déclaration active. Si une application n’appelle pas **SQLSetCursorName**, le conducteur génère des noms de curseur au besoin pour le traitement des relevés SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLSetCursorName(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CursorName,  
     SQLSMALLINT   NameLength);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *CursorName*  
 [Entrée] Nom du curseur. Pour un traitement efficace, le nom du curseur ne doit pas inclure d’espaces de tête ou de fuite dans le nom du curseur, et si le nom du curseur comprend un identifiant délimité, le délimitateur doit être positionné comme le premier personnage dans le nom du curseur.  
  
 *NameLength*  
 [Entrée] Longueur dans les caractères de *'CursorName*.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetCursorName** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLSetCursorName** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Le nom du curseur a dépassé la limite maximale, de sorte que seul le nombre maximal autorisé de caractères a été utilisé.|  
|24 000|État de curseur non valide|La déclaration correspondant à *StatementHandle* se trouvait déjà dans un état exécuté ou placé par un curseur.|  
|34000|Nom de curseur non valide|Le nom du curseur spécifié dans*le CursorName* était invalide parce qu’il dépassait la longueur maximale telle que définie par le conducteur, ou qu’il a commencé par « SQLCUR » ou « SQL_CUR ».|  
|3C000|Nom du curseur en double|Le nom du curseur spécifié dans*le CursorName* existe déjà.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY009|Utilisation invalide du pointeur nul|(DM) L’argument *CursorName* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction aynchrone était encore en cours d’exécution lorsque la fonction **SQLSetCursorName** a été appelée.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) L’argument *NameLength* était inférieur à 0, mais pas égal à SQL_NTS.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Les noms de curseur ne sont utilisés que dans les mises à jour positionnées et suppriment les déclarations (par exemple, _nom de table_ **UPDATE** ... **Où CURRENT OF** _cursor-name_). Pour plus d’informations, voir [Mise à jour positionnée et supprimer les déclarations](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Si l’application n’appelle pas **SQLSetCursorName** pour définir un nom de curseur, lors de l’exécution d’une déclaration de requête, le conducteur génère un nom qui commence par les lettres SQL_CUR et ne dépasse pas 18 caractères de longueur.  
  
 Tous les noms de curseur dans la connexion doivent être uniques. La longueur maximale d’un nom de curseur est définie par le conducteur. Pour une interopérabilité maximale, il est recommandé que les applications limitent les noms de curseur à pas plus de 18 caractères. Dans ODBC 3 *.x*, si un nom de curseur est un identifiant cité, il est traité d’une manière sensible aux cas et il peut contenir des caractères que la syntaxe de SQL ne permettrait pas ou traiterait spécialement, comme des blancs ou des mots-clés réservés. Si un nom de curseur doit être traité d’une manière sensible aux cas, il doit être adopté comme un identifiant cité.  
  
 Un nom de curseur qui est réglé explicitement ou implicitement reste défini jusqu’à ce que la déclaration avec laquelle il est associé est supprimée, en utilisant **SQLFreeHandle**. **SQLSetCursorName** peut être appelé à renommer un curseur sur une déclaration tant que le curseur est dans un état attribué ou préparé.  
  
## <a name="code-example"></a>Exemple de code  
 Dans l’exemple suivant, une application utilise **SQLSetCursorName** pour définir un nom de curseur pour une déclaration. Il utilise ensuite cette instruction pour récupérer les résultats de la table CUSTOMERS. Enfin, il effectue une mise à jour positionnée pour modifier le numéro de téléphone de John Smith. Notez que l’application utilise différentes poignées de relevés pour les instructions **SELECT** et **UPDATE.**  
  
 Pour un autre exemple de code, voir [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```cpp  
#define NAME_LEN 50  
#define PHONE_LEN 10  
  
SQLHSTMT     hstmtSelect,  
SQLHSTMT     hstmtUpdate;  
SQLRETURN    retcode;  
SQLHDBC      hdbc;  
SQLCHAR      szName[NAME_LEN], szPhone[PHONE_LEN];  
SQLINTEGER   cbName, cbPhone;  
  
/* Allocate the statements and set the cursor name. */  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmtSelect);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmtUpdate);  
SQLSetCursorName(hstmtSelect, "C1", SQL_NTS);  
  
/* SELECT the result set and bind its columns to local buffers. */  
  
SQLExecDirect(hstmtSelect,  
      "SELECT NAME, PHONE FROM CUSTOMERS",  
      SQL_NTS);  
SQLBindCol(hstmtSelect, 1, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
SQLBindCol(hstmtSelect, 2, SQL_C_CHAR, szPhone, PHONE_LEN, &cbPhone);  
  
/* Read through the result set until the cursor is */  
/* positioned on the row for John Smith. */  
  
do  
 retcode = SQLFetch(hstmtSelect);  
while ((retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) &&  
   (strcmp(szName, "Smith, John") != 0));  
  
/* Perform a positioned update of John Smith's name. */  
  
if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
   SQLExecDirect(hstmtUpdate,  
   "UPDATE EMPLOYEE SET PHONE=\"2064890154\" WHERE CURRENT OF C1",  
   SQL_NTS);  
}  
```  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Retour d’un nom curseur|[SQLGetCursorName Function](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Définition des options de défilement du curseur|[SQLSetScrollOptions, fonction](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
