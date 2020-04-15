---
title: Fonction SQLParamData (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLParamData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLParamData
helpviewer_keywords:
- SQLParamData function [ODBC]
ms.assetid: 68fe010d-9539-4e5b-a260-c8d32423b1db
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ed149e125e3231d670c6ddbd4569ff5ccee5c15
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306920"
---
# <a name="sqlparamdata-function"></a>SQLParamData, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLParamData** est utilisé avec **SQLPutData** pour fournir des données de paramètres au moment de l’exécution des relevés, et avec **SQLGetData** pour récupérer les données de paramètres de sortie en streaming.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLParamData(  
     SQLHSTMT       StatementHandle,  
     SQLPOINTER *   ValuePtrPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *ValeurPtrPtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner l’adresse du tampon *ParameterValuePtr* spécifié dans **SQLBindParameter** (pour les données de paramètres) ou l’adresse du tampon *TargetValuePtr* spécifié dans **SQLBindCol** (pour les données de colonne), tel que contenu dans le champ d’enregistrement SQL_DESC_DATA_PTR descripteur.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLParamData** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLParamData** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation restreinte d’attribut de type de données|La valeur des données identifiée par *l’argument valueType* dans **SQLBindParameter** pour le paramètre lié n’a pas pu être convertie au type de données identifié par *l’argument de ParameterType* dans **SQLBindParameter**.<br /><br /> La valeur des données retournée pour un paramètre lié comme SQL_PARAM_INPUT_OUTPUT ou SQL_PARAM_OUTPUT n’a pas pu être convertie au type de données identifié par l’argument *ValueType* dans **SQLBindParameter**.<br /><br /> (Si les valeurs de données pour une ou plusieurs lignes ne pouvaient pas être converties, mais qu’une ou plusieurs lignes ont été retournées avec succès, cette fonction revient SQL_SUCCESS_WITH_INFO.)|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|22026|Chaîne de données ou longueur non correspondante|Le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo** était « Y », et moins de données ont été envoyées pour un long paramètre (le type de données était SQL_LONGVARCHAR, SQL_LONGVARBINARY, ou un type de données de données spécifiques à de longues sources de données) que ce qui a été spécifié avec *l’argument StrLen_or_IndPtr* dans **SQLBindParameter**.<br /><br /> Le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo** était "Y", et moins de données ont été envoyées pour une longue colonne (le type de données a été SQL_LONGVARCHAR, SQL_LONGVARBINARY, ou un type de données spécifiques à la source de données longues) que ce qui a été spécifié dans le tampon de longueur correspondant à une colonne dans une rangée de données qui a été ajoutée ou mise à jour avec **SQLBulkOperations** ou mis à jour avec **SQLSetPos**.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’une impasse dans les ressources avec une autre transaction.|  
|40003|Achèvement de l’énoncé inconnu|La connexion associée a échoué lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY008 HY008|Opération annulée|Le traitement asynchrone a été activé pour le *StatementHandle*. La fonction a été appelée, et avant qu’elle ne termine son exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle;* la fonction a ensuite été appelée à nouveau sur le *StatementHandle*.<br /><br /> La fonction a été appelée, et avant qu’il ait terminé l’exécution, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *StatementHandle* à partir d’un thread différent dans une application multitâli.|  
|HY010|Erreur de séquence de fonction|(DM) L’appel de fonction précédent n’était pas un appel à **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, ou **SQLSetPos** où le code de retour a été SQL_NEED_DATA, ou l’appel de fonction précédente était un appel à **SQLPutData**.<br /><br /> L’appel de fonction précédent était un appel à **SQLParamData**.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLParamData** a été appelée.<br /><br /> (DM) Une fonction d’exécution asynchrone (pas celle-ci) a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. **SQLCancel** a été appelé avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur qui correspond à la *DéclarationHandle* ne prend pas en charge la fonction.|  
|IM017|Le sondage est désactivé en mode notification asynchrone|Chaque fois que le modèle de notification est utilisé, le sondage est désactivé.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur cette poignée.|Si la fonction précédente fait appel aux retours de poignée SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelé sur la poignée pour effectuer le post-traitement et terminer l’opération.|  
  
 Si **SQLParamData** est appelé lors de l’envoi de données pour un paramètre dans une déclaration SQL, il peut retourner n’importe quel SQLSTATE qui peut être retourné par la fonction appelée pour exécuter la déclaration (**SQLExecute** ou **SQLExecDirect**). S’il s’agit d’envoyer des données pour une colonne mise à jour ou ajoutée avec **SQLBulkOperations** ou mise à jour avec **SQLSetPos**, il peut retourner n’importe quel SQLSTATE qui peut être retourné par **SQLBulkOperations** ou **SQLSetPos**.  
  
## <a name="comments"></a>Commentaires  
 **SQLParamData** peut être appelé à fournir des données de données à l’exécution pour deux utilisations: les données de paramètres qui seront utilisés dans un appel à **SQLExecute** ou **SQLExecDirect**, ou des données de colonne qui seront utilisés lors d’une ligne est mise à jour ou ajouté par un appel à **SQLBulkOperations** ou mis à jour par un appel à **SQLSetPos**. Au moment de l’exécution, **SQLParamData** retourne à l’application un indicateur des données dont le conducteur a besoin.  
  
 Lorsqu’une application appelle **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos**, le conducteur retourne SQL_NEED_DATA s’il a besoin de données de données à l’exécution. Une application appelle ensuite **SQLParamData** pour déterminer quelles données envoyer. Si le conducteur a besoin de * \** données de paramètres, le pilote retourne dans le tampon de sortie ValuePtrPtr la valeur que l’application a mise dans le tampon rowset. L’application peut utiliser cette valeur pour déterminer les données de paramètres que le conducteur demande. Si le conducteur a besoin de données de colonne, le conducteur retourne dans le * \*tampon ValuePtrPtr* l’adresse à laquelle la colonne était initialement liée, comme suit :  
  
 *Compensation* + *de liaison d’adresse* liée ((numéro de*rangée* - 1) x *taille d’élément*)  
  
 lorsque les variables sont définies comme indiquées dans le tableau suivant.  
  
|Variable|Description|  
|--------------|-----------------|  
|*Adresse liée*|L’adresse spécifiée avec l’argument *TargetValuePtr* dans **SQLBindCol**.|  
|*Compensation de liaison*|La valeur stockée à l’adresse spécifiée avec l’attribut SQL_ATTR_ROW_BIND_OFFSET_PTR déclaration.|  
|*Row Number*|Le numéro à 1 base de la rangée dans le rame. Pour les allers-meur à une seule ligne, qui sont la valeur par défaut, c’est 1.|  
|*Taille de l’élément*|La valeur de l’attribut de l’SQL_ATTR_ROW_BIND_TYPE énoncé pour les données et les tampons de longueur/indicateur.|  
  
 Il renvoie également SQL_NEED_DATA, ce qui est un indicateur de l’application qu’il devrait appeler **SQLPutData** pour envoyer les données.  
  
 L’application appelle **SQLPutData** autant de fois que nécessaire pour envoyer les données de données à l’exécution pour la colonne ou le paramètre. Après que toutes les données ont été envoyées pour la colonne ou le paramètre, l’application appelle **SQLParamData** à nouveau. Si **SQLParamData** retourne à nouveau SQL_NEED_DATA, les données doivent être envoyées pour un autre paramètre ou colonne. Par conséquent, l’application appelle à nouveau **SQLPutData**. Si toutes les données de données sur les données d’exécution ont été envoyées pour tous les paramètres ou colonnes, **SQLParamData** retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, la valeur de * \*ValuePtrPtr* n’est pas définie, et la déclaration SQL peut être exécutée ou **l’appel SQLBulkOperations** ou **SQLSetPos** peut être traité.  
  
 Si **SQLParamData** fournit des données de paramètres pour une mise à jour recherchée ou supprime une déclaration qui n’affecte aucune ligne à la source de données, l’appel à **SQLParamData** renvoie SQL_NO_DATA.  
  
 Pour plus d’informations sur la façon dont les données de paramètres de données à l’exécution sont transmises au moment de l’exécution des relevés, voir « Valeurs de paramètres de passage » dans [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) et [envoyer de longues données.](../../../odbc/reference/develop-app/sending-long-data.md) Pour plus d’informations sur la façon dont les données de la colonne de données à l’exécution sont mises à jour ou ajoutées, voir la section "Using SQLSetPos" dans [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), "Performing Bulk Updates Using Bookmarks" dans [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), et [Long Data et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
 **SQLParamData** peut être appelé pour récupérer les paramètres de sortie en streaming. Lorsque **SQLMoreResults**, **SQLExecute**, **SQLGetData**, ou **SQLExecDirect** retourne SQL_PARAM_DATA_AVAILABLE, appelez **SQLParamData** pour déterminer quel paramètre a une valeur disponible. Pour plus d’informations sur SQL_PARAM_DATA_AVAILABLE et les paramètres de sortie en streaming, voir [Les paramètres de sortie de récupération à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="code-example"></a>Exemple de code  
 Voir [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lier un tampon à un paramètre|[Fonction SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Annulation du traitement des relevés|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Retour d’informations sur un paramètre dans une déclaration|[Fonction SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|Exécution d’une déclaration SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécution d’une déclaration SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Envoi de données de paramètres au moment de l’exécution|[Fonction SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
