---
title: SQLCloseCursor, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCloseCursor
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCloseCursor
helpviewer_keywords:
- SQLCloseCursor function [ODBC]
ms.assetid: 05b0a054-e28d-4e16-b5b0-07418486b372
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 47766dbbb273d9e5e4d42e8df6b5cf3c26bf356a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036041"
---
# <a name="sqlclosecursor-function"></a>SQLCloseCursor, fonction
**Conformité**  
 Version introduite : Conformité aux normes 3.0 de ODBC : ISO 92  
  
 **Résumé**  
 **SQLCloseCursor** ferme un curseur qui a été ouvert dans une instruction et ignore les résultats en attente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLCloseCursor(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle*  
 [Entrée] Descripteur d’instruction.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLCloseCursor** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL _HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLCloseCursor** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|24000|État de curseur non valide|Aucun curseur n’a été ouvert sur le *au paramètre StatementHandle*. (Ceci est retourné uniquement par un ODBC 3. *x* pilote.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion associé à la *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 **SQLCloseCursor** retourne SQLSTATE 24000 (état de curseur non valide) si aucun curseur n’est ouvert. Appel **SQLCloseCursor** équivaut à appeler **SQLFreeStmt** avec l’option SQL_CLOSE, avec l’exception qui **SQLFreeStmt** avec SQL_CLOSE n’a aucun effet le application si aucun curseur n’est ouverte sur l’instruction, tandis que **SQLCloseCursor** retourne SQLSTATE 24000 (état de curseur non valide).  
  
> [!NOTE]  
>  If un ODBC 3. *x* application fonctionne avec une API ODBC 2. *x* pilote appelle **SQLCloseCursor** lorsque aucun curseur n’est ouvert, SQLSTATE 24000 (état de curseur non valide) n’est retourné, car le Gestionnaire de pilotes mappe **SQLCloseCursor** à **SQLFreeStmt** avec SQL_CLOSE.  
  
 Pour plus d’informations, consultez [fermeture du curseur](../../../odbc/reference/develop-app/closing-the-cursor.md).  
  
## <a name="code-example"></a>Exemple de code  
 Consultez [fonction SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md) et [fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Annulation de traitement d’instruction|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Libération d’un descripteur|[SQLFreeHandle, fonction](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|Traitement de plusieurs jeux de résultats|[SQLMoreResults, fonction](../../../odbc/reference/syntax/sqlmoreresults-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
