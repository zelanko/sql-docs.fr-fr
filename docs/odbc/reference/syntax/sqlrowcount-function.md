---
title: SQLRowCount, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRowCount
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRowCount
helpviewer_keywords:
- SQLRowCount function [ODBC]
ms.assetid: 61e00a8a-9b3b-45b9-b397-7fe818822416
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ccc858603fc5662f380c5d3ae48d777005ddac4
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537160"
---
# <a name="sqlrowcount-function"></a>SQLRowCount (fonction)
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ISO 92  
  
 **Résumé**  
 **SQLRowCount** retourne le nombre de lignes affectées par une **mise à jour**, **insérer**, ou **supprimer** instruction ; une SQL_ADD, SQL_UPDATE_BY_BOOKMARK ou SQL_ Opération DELETE_BY_BOOKMARK dans **SQLBulkOperations**; ou une opération SQL_UPDATE ou SQL_DELETE dans **SQLSetPos**.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLRowCount(  
      SQLHSTMT   StatementHandle,  
      SQLLEN *   RowCountPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle*  
 [Entrée] Descripteur d’instruction.  
  
 *RowCountPtr*  
 [Sortie] Pointe vers une mémoire tampon dans lequel retourner un nombre de lignes. Pour **mise à jour**, **insérer**, et **supprimer** les instructions pour les opérations SQL_ADD, SQL_UPDATE_BY_BOOKMARK et SQL_DELETE_BY_BOOKMARK dans  **SQLBulkOperations**et pour les opérations SQL_UPDATE ou SQL_DELETE dans **SQLSetPos**, la valeur retournée dans **RowCountPtr* est soit le nombre de lignes affectées par le demande ou -1 si le nombre de lignes affectées n’est pas disponible.  
  
 Lorsque **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, **SQLSetPos ou SQLMoreResults** est appelée, le SQL_DIAG_ROW_COUNT champ de la structure de données de diagnostic est défini sur le nombre de lignes, et le nombre de lignes est mis en cache de manière dépend de l’implémentation. **SQLRowCount** retourne la valeur de nombre de lignes mises en cache. La valeur de nombre de lignes mises en cache est valide jusqu'à ce que le descripteur d’instruction est rétabli à l’état alloué ou préparé, l’instruction est exécutée de nouveau, ou **SQLCloseCursor** est appelée. Notez que si une fonction a été appelée dans la mesure où le champ SQL_DIAG_ROW_COUNT a été défini, la valeur retournée par **SQLRowCount** peut être différente de la valeur dans le champ SQL_DIAG_ROW_COUNT, car le champ SQL_DIAG_ROW_COUNT est réinitialisé à 0 par un appel de fonction.  
  
 Pour les autres instructions et les fonctions, le pilote peut définir la valeur retournée dans \* *RowCountPtr*. Par exemple, certaines sources de données peuvent être en mesure de retourner le nombre de lignes retournées par une **sélectionnez** instruction ou une fonction de catalogue avant l’extraction de lignes.  
  
> [!NOTE]  
>  Nombreuses sources de données ne peut pas retourner le nombre de lignes dans un jeu de résultats avant l’extraction pour une interopérabilité maximale, les applications ne doivent pas compter sur ce comportement.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLRowCount** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_ HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLRowCount** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution lorsque le **SQLRowCount** fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.<br /><br /> (DM) la fonction a été appelée avant d’appeler **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** pour la  *Au paramètre StatementHandle*.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le  *Au paramètre StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Si la dernière instruction SQL exécutée sur le descripteur d’instruction n’était pas un **mise à jour**, **insérer**, ou **supprimer** instruction ou si le *opération* argument dans l’appel précédent à **SQLBulkOperations** n’était pas SQL_ADD, SQL_UPDATE_BY_BOOKMARK ou SQL_DELETE_BY_BOOKMARK, ou si le *opération* argument dans l’appel précédent à  **SQLSetPos** n’était pas SQL_UPDATE ou SQL_DELETE, la valeur de **RowCountPtr* est définie par le pilote. Pour plus d’informations, consultez [déterminer le nombre de lignes affectées](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|L’exécution d’une instruction SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécuter une instruction SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
