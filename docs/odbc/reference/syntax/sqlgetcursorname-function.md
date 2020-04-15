---
title: Fonction SQLGetCursorName (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetCursorName
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetCursorName
helpviewer_keywords:
- SQLGetCursorName function [ODBC]
ms.assetid: e6e92199-7bb6-447c-8987-049a4c6ce05d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3ac65dc07897ddc789ee03b06b1bc1f71d37c3c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285547"
---
# <a name="sqlgetcursorname-function"></a>SQLGetCursorName Function
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetCursorName renvoie** le nom du curseur associé à une déclaration spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetCursorName(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CursorName,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   NameLengthPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *CursorName*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nom du curseur.  
  
 Si *CursorName* est NULL, *NameLengthPtr* retournera toujours le nombre total de caractères (à l’exclusion du caractère de non-termination pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *CursorName*.  
  
 *BufferLength*  
 [Entrée] Longueur \*de *CursorName*, en caractères. Si la valeur de * \*CursorName* est une chaîne Unicode (lorsqu’on appelle **SQLGetCursorNameW**), l’argument *BufferLength* doit être un nombre pair.  
  
 *NomLengthPtr*  
 [Sortie] Pointeur à la mémoire dans laquelle retourner le nombre total de caractères (à l’exclusion du caractère de non-termination) disponibles pour revenir dans \* *CursorName*. Si le nombre de caractères disponibles pour revenir est supérieur ou égal \*à *BufferLength*, le nom du curseur dans *CursorName* est tronqué à *BufferLength* moins la longueur d’un caractère de non-termination.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetCursorName renvoie** SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLGetCursorName** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Le \*tampon *CursorName* n’était pas assez grand pour retourner le nom de curseur entier, de sorte que le nom du curseur a été tronqué. La longueur du nom du curseur nontrui est retournée dans*nameLengthPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLGetCursorName** a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY015|Aucun nom de curseur disponible|(DM) Le conducteur était un conducteur ODBC 2 *.x,* il n’y avait pas de curseur ouvert sur la déclaration, et aucun nom de curseur n’avait été réglé avec **SQLSetCursorName**.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur spécifiée dans l’argument *BufferLength* était inférieure à 0.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *StatementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Les noms de curseur ne sont utilisés que dans les mises à jour positionnées et suppriment les déclarations (par exemple, _nom de table_ **UPDATE** ... **Où CURRENT OF** _cursor-name_). Pour plus d’informations, voir [Mise à jour positionnée et supprimer les déclarations](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Si l’application n’appelle pas **SQLSetCursorName** pour définir un nom de curseur, le pilote génère un nom. Ce nom commence par les lettres SQL_CUR.  
  
> [!NOTE]
>  Dans ODBC 2 *.x*, quand il n’y avait pas de curseur ouvert et aucun nom n’avait été fixé par un appel à **SQLSetCursorName**, un appel à **SQLGetCursorName** retourné SQLSTATE HY015 (Aucun nom de curseur disponible). Dans ODBC 3 *.x*, ce n’est plus vrai; peu importe le moment où **SQLGetCursorName** est appelé, le conducteur retourne le nom du curseur.  
  
 **SQLGetCursorName renvoie** le nom d’un curseur, que le nom ait été créé explicitement ou implicitement. Un nom de curseur est implicitement généré si **SQLSetCursorName** n’est pas appelé. **SQLSetCursorName** peut être appelé à renommer un curseur sur une déclaration tant que le curseur est dans un état attribué ou préparé.  
  
 Un nom de curseur qui est réglé explicitement ou implicitement reste défini jusqu’à ce que le *StatementHandle* avec lequel il est associé est supprimé, en utilisant **SQLFreeHandle** avec un *HandleType* de SQL_HANDLE_STMT.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Préparation d’une déclaration pour l’exécution|[Fonction SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Définir un nom de curseur|[SQLSetCursorName, fonction](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
