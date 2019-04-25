---
title: SQLParamData, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec0038e0ec6c87dba403bbe62441815dfa6d0251
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62465965"
---
# <a name="sqlparamdata-function"></a>SQLParamData, fonction
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ISO 92  
  
 **Résumé**  
 **SQLParamData** est utilisé conjointement avec **SQLPutData** pour fournir des données de paramètre au moment de l’exécution d’instruction et avec **SQLGetData** pour récupérer des données de paramètre de sortie diffusées en continu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQLRETURN SQLParamData(  
     SQLHSTMT       StatementHandle,  
     SQLPOINTER *   ValuePtrPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle*  
 [Entrée] Descripteur d’instruction.  
  
 *ValuePtrPtr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner l’adresse de la *ParameterValuePtr* mémoire tampon spécifiée dans **SQLBindParameter** (pour les données de paramètre) ou l’adresse de la *TargetValuePtr* mémoire tampon spécifiée dans **SQLBindCol** (pour les données de colonne), comme contenue dans le champ d’enregistrement de descripteur SQL_DESC_DATA_PTR.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NEED_DATA, SQL_NO_DATA, SQL_STILL_EXECUTING, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLParamData** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenu en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_ HANDLE_STMT et un *gérer* de *au paramètre StatementHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLParamData** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|07006|Violation de l’attribut de type de données restreint|La valeur de données identifiée par le *ValueType* argument dans **SQLBindParameter** pour le paramètre dépendant n’a pas pu être converti au type de données identifié par le *ParameterType*argument dans **SQLBindParameter**.<br /><br /> La valeur de données retournée pour un paramètre lié comme SQL_PARAM_INPUT_OUTPUT ou SQL_PARAM_OUTPUT pas pu être convertie au type de données identifié par le *ValueType* argument dans **SQLBindParameter**.<br /><br /> (Si les valeurs de données pour une ou plusieurs lignes n’a pas pu être converties, mais une ou plusieurs lignes ont été retournés avec succès, cette fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|22026|Chaîne de données ou longueur non correspondante|Le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo** était « Y », et moins de données a été envoyés pour un paramètre de type long (le type de données a été SQL_LONGVARCHAR, SQL_LONGVARBINARY ou un type de données spécifiques à la source de données de type long) que celle spécifiée avec le *StrLen_or_IndPtr* argument dans **SQLBindParameter**.<br /><br /> Le type d’information SQL_NEED_LONG_DATA_LEN dans **SQLGetInfo** était « Y » et moins de données a été envoyées pour une colonne longue (le type de données a été SQL_LONGVARCHAR, SQL_LONGVARBINARY ou un type de données spécifiques à la source de données de type long) que celle spécifiée dans la mémoire tampon de longueur correspondant à une colonne dans une ligne de données qui a été ajoutées ou mis à jour avec **SQLBulkOperations** ou mis à jour avec **SQLSetPos**.|  
|40001|Échec de la sérialisation|La transaction a été annulée en raison d’un blocage de ressource avec une autre transaction.|  
|40003|Saisie semi-automatique des instructions inconnue|Échec de la connexion associée lors de l’exécution de cette fonction, et l’état de la transaction ne peut pas être déterminé.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer de la mémoire qui est nécessaire pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY008|Opération annulée|Traitement asynchrone a été activé pour le *au paramètre StatementHandle*. La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle*; la fonction a été ensuite appelée à nouveau sur le *au paramètre StatementHandle*.<br /><br /> La fonction a été appelée et avant qu’il exécutée avec succès, **SQLCancel** ou **SQLCancelHandle** a été appelé sur le *au paramètre StatementHandle* d’un thread différent dans un application multithread.|  
|HY010|Erreur de séquence de fonction|(DM) l’appel de fonction précédente n’était pas un appel à **SQLExecDirect**, **SQLExecute**, **SQLBulkOperations**, ou **SQLSetPos** où le retourner le code était SQL_NEED_DATA ou l’appel de fonction précédente était un appel à **SQLPutData**.<br /><br /> L’appel de fonction précédente a été un appel à **SQLParamData**.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le handle de connexion qui est associé à la *au paramètre StatementHandle*. Cette fonction asynchrone était en cours d’exécution lorsque le **SQLParamData** fonction a été appelée.<br /><br /> (DM) une fonction de façon asynchrone en cours d’exécution (pas celui-ci) a été appelée pour le *au paramètre StatementHandle* et était en cours d’exécution quand cette fonction a été appelée.<br /><br /> **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *au paramètre StatementHandle* et SQL_NEED_DATA retourné. **SQLCancel** a été appelée avant l’envoi de données pour tous les paramètres de data-at-execution ou les colonnes.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|(DM) le pilote qui correspond à la *au paramètre StatementHandle* ne prend pas en charge la fonction.|  
|IM017|L’interrogation est désactivée en mode de notification asynchrone|Chaque fois que le modèle de notification est utilisé, l’interrogation est désactivée.|  
|IM018|**SQLCompleteAsync** n’a pas été appelé pour terminer l’opération asynchrone précédente sur ce handle.|Si l’appel de fonction précédente sur le handle retourne SQL_STILL_EXECUTING et si le mode de notification est activé, **SQLCompleteAsync** doit être appelée sur le handle de post-traitement et terminer l’opération.|  
  
 Si **SQLParamData** est appelée lors de l’envoi des données pour un paramètre dans une instruction SQL, elle peut retourner n’importe quel SQLSTATE qui peut être retournée par la fonction appelée pour exécuter l’instruction (**SQLExecute** ou **SQLExecDirect**). Si elle est appelée lors de l’envoi de données pour une colonne en cours de mise à jour ou ajoutée avec **SQLBulkOperations** ou mis à jour avec **SQLSetPos**, elle peut retourner n’importe quel SQLSTATE qui peut être retourné par  **SQLBulkOperations** ou **SQLSetPos**.  
  
## <a name="comments"></a>Commentaires  
 **SQLParamData** peut être appelée pour fournir des données de data-at-execution pour deux utilisations : les données de paramètre qui seront utilisées dans un appel à **SQLExecute** ou **SQLExecDirect**, ou les données de la colonne qui seront utilisée lorsque une ligne est mise à jour ou ajoutée par un appel à **SQLBulkOperations** ou mis à jour par un appel à **SQLSetPos**. Au moment de l’exécution, **SQLParamData** retourne à l’application nécessite le pilote d’un indicateur de données.  
  
 Lorsqu’une application appelle **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos**, le pilote retourne SQL_NEED_ DONNÉES si elle a besoin de données de data-at-execution. Une application appelle ensuite **SQLParamData** pour déterminer les données à envoyer. Si le pilote nécessite des données de paramètre, le pilote retourne dans le  *\*ValuePtrPtr* sortie de la mémoire tampon la valeur de l’application placée dans le tampon de l’ensemble de lignes. L’application peut utiliser cette valeur pour déterminer les données de paramètre demande le pilote. Si le pilote requiert des données de la colonne, le pilote retourne dans le  *\*ValuePtrPtr* mettre en mémoire tampon l’adresse de la colonne a été initialement liée, comme suit :  
  
 *Lié adresse* + *liaison décalage* + ((*numéro de ligne* - 1) x *taille de l’élément*)  
  
 où les variables sont définies comme indiqué dans le tableau suivant.  
  
|Variable|Description|  
|--------------|-----------------|  
|*Limite d’adresse*|L’adresse spécifiée avec le *TargetValuePtr* argument dans **SQLBindCol**.|  
|*Décalage de la liaison*|La valeur stockée à l’adresse spécifiée avec l’attribut d’instruction SQL_ATTR_ROW_BIND_OFFSET_PTR.|  
|*Numéro de ligne*|Le nombre de base 1 de la ligne dans l’ensemble de lignes. Pour les extractions de ligne unique, qui sont la valeur par défaut, il s’agit de 1.|  
|*Taille de l’élément*|La valeur de l’attribut d’instruction SQL_ATTR_ROW_BIND_TYPE pour les mémoires tampons de données et de longueur / d’indicateur.|  
  
 Elle retourne également SQL_NEED_DATA, ce qui est un indicateur à l’application qu’il doit appeler **SQLPutData** pour envoyer les données.  
  
 L’application appelle **SQLPutData** autant de fois que nécessaire pour envoyer les données de data-at-execution de la colonne ou du paramètre. Une fois que toutes les données a été envoyé pour la colonne ou du paramètre, l’application appelle **SQLParamData** à nouveau. Si **SQLParamData** à nouveau retourne SQL_NEED_DATA, données doivent être envoyées pour un autre paramètre ou une colonne. Par conséquent, l’application appelle **SQLPutData**. Si toutes les données de data-at-execution a été envoyé pour tous les paramètres ou colonnes, puis **SQLParamData** retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO, la valeur dans  *\*ValuePtrPtr* n’est pas défini, et l’instruction SQL peut être exécutée ou **SQLBulkOperations** ou **SQLSetPos** appel peut être traité.  
  
 Si **SQLParamData** fournit les données de paramètre pour une recherche mettre à jour ou supprimer l’instruction qui affecte toutes les lignes à la source de données, l’appel à **SQLParamData** retourne SQL_NO_DATA.  
  
 Pour plus d’informations sur les données de paramètre comment data-at-execution sont passées au moment de l’exécution d’instruction, consultez « En passant des valeurs de paramètre » dans [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md) et [envoyer les données de type Long](../../../odbc/reference/develop-app/sending-long-data.md). Pour plus d’informations sur les données de la colonne comment data-at-execution sont mis à jour ou ajoutées, consultez la section « À l’aide de SQLSetPos » dans [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md), « Effectuer en bloc les mises à jour à l’aide de signets » dans [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), et [données de type Long et SQLSetPos et SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md).  
  
 **SQLParamData** peut être appelée pour récupérer les paramètres de sortie diffusées en continu. Lorsque **SQLMoreResults**, **SQLExecute**, **SQLGetData**, ou **SQLExecDirect** retourne SQL_PARAM_DATA_AVAILABLE, appelez **SQLParamData** pour déterminer quel paramètre a la valeur disponible. Pour plus d’informations sur les SQL_PARAM_DATA_AVAILABLE et les paramètres de sortie diffusées en continu, consultez [récupération des paramètres de sortie à l’aide de SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="code-example"></a>Exemple de code  
 Consultez [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Liaison d’une mémoire tampon à un paramètre|[SQLBindParameter, fonction](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Annulation de traitement d’instruction|[SQLCancel, fonction](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Retour d’informations sur un paramètre dans une instruction|[SQLDescribeParam, fonction](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|L’exécution d’une instruction SQL|[SQLExecDirect, fonction](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Exécuter une instruction SQL préparée|[SQLExecute, fonction](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Envoi de données de paramètre au moment de l’exécution|[SQLPutData, fonction](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Récupération des paramètres de sortie à l’aide de SQLGetData ](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
