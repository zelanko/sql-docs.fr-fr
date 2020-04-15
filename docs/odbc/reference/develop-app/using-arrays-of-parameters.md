---
title: Utilisation de tableaux de paramètres Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 5a28be88-e171-4f5b-bf4d-543c4383c869
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b584dc3d635e9fa8ce3228e4e89b0f24451fe165
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306800"
---
# <a name="using-arrays-of-parameters"></a>Utilisation de tableaux de paramètres
Pour utiliser des tableaux de paramètres, l’application appelle **SQLSetStmtAttr** avec un argument *d’attribut* de SQL_ATTR_PARAMSET_SIZE pour spécifier le nombre d’ensembles de paramètres. Il appelle **SQLSetStmtAttr** avec un argument *d’attribut* de SQL_ATTR_PARAMS_PROCESSED_PTR pour spécifier l’adresse d’une variable dans laquelle le conducteur peut retourner le nombre d’ensembles de paramètres traités, y compris les ensembles d’erreurs. Il appelle **SQLSetStmtAttr** avec un argument *d’attribut* de SQL_ATTR_PARAM_STATUS_PTR de pointer vers un tableau dans lequel retourner l’information d’état pour chaque rangée de valeurs de paramètres. Le conducteur stocke ces adresses dans la structure qu’il maintient pour l’énoncé.  
  
> [!NOTE]  
>  À ODBC 2. *x*, **SQLParamOptions** a été appelé pour spécifier plusieurs valeurs pour un paramètre. À ODBC 3. *x*, l’appel à **SQLParamOptions** a été remplacé par des appels à **SQLSetStmtAttr** pour définir les attributs SQL_ATTR_PARAMSET_SIZE et SQL_ATTR_PARAMS_PROCESSED_ARRAY.  
  
 Avant d’exécuter l’instruction, l’application définit la valeur de chaque élément de chaque tableau lié. Lorsque la déclaration est exécutée, le conducteur utilise les informations qu’il stocke pour récupérer les valeurs de paramètres et les envoyer à la source de données; si possible, le conducteur doit envoyer ces valeurs sous forme de tableaux. Bien que l’utilisation de tableaux de paramètres soit mieux mise en œuvre en exécutant la déclaration SQL avec tous les paramètres du tableau avec un seul appel à la source de données, cette capacité n’est pas largement disponible dans les DBMS aujourd’hui. Cependant, les conducteurs peuvent le simuler en exécutant une déclaration SQL plusieurs fois, chacun avec un seul ensemble de paramètres.  
  
 Avant qu’une application n’utilise des tableaux de paramètres, il doit être sûr qu’ils sont pris en charge par les pilotes utilisés par l’application. Il existe deux façons d'effectuer cette opération :  
  
-   Utilisez uniquement les pilotes connus pour prendre en charge des tableaux de paramètres. L’application peut coder les noms de ces pilotes, ou l’utilisateur peut être chargé d’utiliser uniquement ces pilotes. Les applications personnalisées et les applications verticales utilisent généralement un ensemble limité de pilotes.  
  
-   Vérifiez la prise en charge des tableaux de paramètres au moment de l’exécution. Un conducteur prend en charge des gammes de paramètres s’il est possible de définir l’attribut SQL_ATTR_PARAMSET_SIZE énoncé à une valeur supérieure à 1. Les applications génériques et les applications verticales vérifient généralement la prise en charge des ensembles de paramètres au moment de l’exécution.  
  
 La disponibilité des nombres de rangées et les ensembles de résultats dans l’exécution paramétrée peut être déterminée en appelant **SQLGetInfo** avec les options SQL_PARAM_ARRAY_ROW_COUNTS et SQL_PARAM_ARRAY_SELECTS. Pour les relevés **INSERT**, **UPDATE**et **DELETE,** l’option SQL_PARAM_ARRAY_ROW_COUNTS indique si des nombres de lignes individuelles (un pour chaque paramètre) sont disponibles (SQL_PARC_BATCH) ou si les nombres de rangées sont enroulés en un seul (SQL_PARC_NO_BATCH). Pour les relevés **SELECT,** l’option SQL_PARAM_ARRAY_SELECTS indique si un ensemble de résultats est disponible pour chaque ensemble de paramètres (SQL_PAS_BATCH) ou si un seul ensemble de résultats est disponible (SQL_PAS_NO_BATCH). Si le pilote ne permet pas l’exécution de relevés générateurs de paramètres, SQL_PARAM_ARRAY_SELECTS renvoie SQL_PAS_NO_SELECT. Il est spécifique à la source de données si des tableaux de paramètres peuvent être utilisés avec d’autres types d’énoncés, en particulier parce que l’utilisation de paramètres dans ces énoncés serait spécifique à la source des données et ne suivrait pas la grammaire ODBC SQL.  
  
 Le tableau pointé par l’attribut de l’SQL_ATTR_PARAM_OPERATION_PTR énoncé peut être utilisé pour ignorer les rangées de paramètres. Si un élément du tableau est configuré pour SQL_PARAM_IGNORE, l’ensemble de paramètres correspondant à cet élément est exclu de l’appel **SQLExecute** ou **SQLExecDirect.** Le tableau indiqué par l’attribut SQL_ATTR_PARAM_OPERATION_PTR est attribué et rempli par l’application et lu par le conducteur. Si les lignes récupérées sont utilisées comme paramètres d’entrée, les valeurs du tableau d’état de la ligne peuvent être utilisées dans le tableau de fonctionnement des paramètres.  
  
## <a name="error-processing"></a>Erreur lors du traitement  
 Si une erreur se produit lors de l’exécution de la déclaration, la fonction d’exécution renvoie une erreur et définit le nombre de lignes variable au nombre de la ligne contenant l’erreur. Il est spécifique aux données si toutes les lignes, sauf l’ensemble d’erreurs, sont exécutées ou si toutes les lignes avant (mais pas après) l’ensemble d’erreurs sont exécutées. Parce qu’il traite des ensembles de paramètres, le conducteur définit le tampon spécifié par l’SQL_ATTR_PARAMS_PROCESSED_PTR’attribut de l’instruction au nombre de la ligne actuellement traitée. Si tous les ensembles, sauf l’ensemble d’erreurs, sont exécutés, le pilote définit ce tampon pour SQL_ATTR_PARAMSET_SIZE après que toutes les lignes sont traitées.  
  
 Si l’attribut de SQL_ATTR_PARAM_STATUS_PTR déclaration a été défini, **SQLExecute** ou **SQLExecDirect** renvoie le *tableau de statut des paramètres,* qui fournit l’état de chaque ensemble de paramètres. Le tableau de l’état des paramètres est attribué par l’application et rempli par le conducteur. Ses éléments indiquent si la déclaration SQL a été exécutée avec succès pour la rangée de paramètres ou si une erreur s’est produite lors du traitement de l’ensemble des paramètres. En cas d’erreur, le conducteur définit la valeur correspondante du tableau d’état du paramètre à SQL_PARAM_ERROR et renvoie SQL_SUCCESS_WITH_INFO. La demande peut vérifier le tableau d’état pour déterminer quelles lignes ont été traitées. En utilisant le numéro de ligne, l’application peut souvent corriger l’erreur et reprendre le traitement.  
  
 La façon dont le tableau d’état des paramètres est utilisé est déterminée par les options SQL_PARAM_ARRAY_ROW_COUNTS et SQL_PARAM_ARRAY_SELECTS retournées par un appel à **SQLGetInfo**. Pour les instructions **INSERT**, **UPDATE**et **DELETE,** le tableau d’état du paramètre est rempli d’informations de statut si SQL_PARC_BATCH est retourné pour SQL_PARAM_ARRAY_ROW_COUNTS, mais pas si SQL_PARC_NO_BATCH est retournée. Pour les relevés **SELECT,** le tableau de statut des paramètres est rempli si SQL_PAS_BATCH est retournée pour SQL_PARAM_ARRAY_SELECT, mais pas si SQL_PAS_NO_BATCH ou SQL_PAS_NO_SELECT est retournée.  
  
## <a name="data-at-execution-parameters"></a>Paramètres de données à l’exécution  
 Si l’une des valeurs de la longueur/tableau d’indicateur est SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC(*longueur)* macro, les données pour ces valeurs sont envoyées avec **SQLPutData** de la manière habituelle. Les aspects suivants de ce processus portent un commentaire particulier parce qu’ils ne sont pas facilement évidents :  
  
-   Lorsque le conducteur retourne SQL_NEED_DATA, il doit définir l’adresse du numéro de ligne variable à la ligne pour laquelle il a besoin de données. Comme dans le cas à valeur unique, la demande ne peut pas faire d’hypothèses sur l’ordre dans lequel le conducteur demandera des valeurs de paramètres dans un seul ensemble de paramètres. Si une erreur se produit dans l’exécution d’un paramètre de données à l’exécution, le tampon spécifié par l’attribut de déclaration SQL_ATTR_PARAMS_PROCESSED_PTR est réglé sur le nombre de la ligne sur laquelle l’erreur s’est produite, l’état de la ligne dans le tableau d’état de la ligne spécifiée par l’attribut de déclaration SQL_ATTR_PARAM_STATUS_PTR est réglé pour SQL_PARAM_ERROR, et l’appel à **SQLExecute**, **SQLExecDirect**, **SQLParamData**, ou **SQLPutData** retourne SQL_ERROR. Le contenu de ce tampon n’est pas défini si **SQLExecute**, **SQLExecDirect**, ou **SQLParamData** retour SQL_STILL_EXECUTING.  
  
-   Étant donné que le conducteur n’interprète pas la valeur de l’argument *de ParameterValuePtr* de **SQLBindParameter** pour les paramètres de données à l’exécution, si l’application fournit un pointeur à un tableau, **SQLParamData** n’extrait pas et ne renvoie pas un élément de ce tableau à l’application. Au lieu de cela, il retourne la valeur scalaire de la demande avait fourni. Cela signifie que la valeur retournée par **SQLParamData** n’est pas suffisante pour spécifier le paramètre pour lequel l’application doit envoyer des données; l’application doit également tenir compte du numéro de ligne actuel.  
  
     Lorsque seuls certains des éléments d’un éventail de paramètres sont des paramètres de données à l’exécution, l’application doit passer l’adresse d’un tableau dans *ParameterValuePtr* qui contient des éléments pour tous les paramètres. Ce tableau est interprété normalement pour les paramètres qui ne sont pas des paramètres de données à l’exécution. Pour les paramètres de données à l’exécution, la valeur que **SQLParamData** apporte à l’application, qui pourrait normalement être utilisée pour identifier les données que le conducteur demande à cette occasion, est toujours l’adresse du tableau.
