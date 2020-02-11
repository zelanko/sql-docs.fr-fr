---
title: Utilisation de tableaux de paramètres | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cf6b5127bac7aedf9e67918d38020c73a4afe186
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079600"
---
# <a name="using-arrays-of-parameters"></a>Utilisation de tableaux de paramètres
Pour utiliser des tableaux de paramètres, l’application appelle **SQLSetStmtAttr** avec un argument d' *attribut* de SQL_ATTR_PARAMSET_SIZE pour spécifier le nombre de jeux de paramètres. Elle appelle **SQLSetStmtAttr** avec un argument d' *attribut* de SQL_ATTR_PARAMS_PROCESSED_PTR pour spécifier l’adresse d’une variable dans laquelle le pilote peut retourner le nombre d’ensembles de paramètres traités, y compris les ensembles d’erreurs. Elle appelle **SQLSetStmtAttr** avec un argument d' *attribut* de SQL_ATTR_PARAM_STATUS_PTR pour pointer vers un tableau dans lequel retourner les informations d’État pour chaque ligne de valeurs de paramètre. Le pilote stocke ces adresses dans la structure qu’elle gère pour l’instruction.  
  
> [!NOTE]  
>  Dans ODBC 2. *x*, **SQLParamOptions,** a été appelé pour spécifier plusieurs valeurs pour un paramètre. Dans ODBC 3. *x*, l’appel à **SQLParamOptions,** a été remplacé par des appels à **SQLSetStmtAttr** pour définir les attributs SQL_ATTR_PARAMSET_SIZE et SQL_ATTR_PARAMS_PROCESSED_ARRAY.  
  
 Avant d’exécuter l’instruction, l’application définit la valeur de chaque élément de chaque tableau lié. Lorsque l’instruction est exécutée, le pilote utilise les informations qu’elle a stockées pour récupérer les valeurs de paramètres et les envoyer à la source de données ; Si possible, le pilote doit envoyer ces valeurs en tant que tableaux. Bien qu’il soit préférable d’utiliser des tableaux de paramètres en exécutant l’instruction SQL avec tous les paramètres du tableau avec un appel unique à la source de données, cette fonctionnalité n’est pas disponible dans les SGBD actuels. Toutefois, les pilotes peuvent les simuler en exécutant plusieurs fois une instruction SQL, chacun avec un ensemble unique de paramètres.  
  
 Avant qu’une application utilise des tableaux de paramètres, elle doit s’assurer qu’ils sont pris en charge par les pilotes utilisés par l’application. Il existe deux façons d'effectuer cette opération :  
  
-   Utilisez uniquement des pilotes connus pour prendre en charge des tableaux de paramètres. L’application peut coder en dur les noms de ces pilotes, ou l’utilisateur peut être invité à utiliser uniquement ces pilotes. Les applications personnalisées et verticales utilisent généralement un ensemble limité de pilotes.  
  
-   Vérifiez la prise en charge des tableaux de paramètres au moment de l’exécution. Un pilote prend en charge des tableaux de paramètres s’il est possible de définir l’attribut d’instruction SQL_ATTR_PARAMSET_SIZE sur une valeur supérieure à 1. Les applications génériques et les applications verticales vérifient généralement la prise en charge des tableaux de paramètres au moment de l’exécution.  
  
 La disponibilité des nombres de lignes et des jeux de résultats dans l’exécution paramétrable peut être déterminée en appelant **SQLGetInfo** avec les options SQL_PARAM_ARRAY_ROW_COUNTS et SQL_PARAM_ARRAY_SELECTS. Pour les instructions **Insert**, **Update**et **Delete** , l’option SQL_PARAM_ARRAY_ROW_COUNTS indique si les nombres de lignes individuels (un pour chaque jeu de paramètres) sont disponibles (SQL_PARC_BATCH) ou si les nombres de lignes sont cumulés dans un (SQL_PARC_NO_BATCH). Pour les instructions **Select** , l’option SQL_PARAM_ARRAY_SELECTS indique si un jeu de résultats est disponible pour chaque ensemble de paramètres (SQL_PAS_BATCH) ou si un seul jeu de résultats est disponible (SQL_PAS_NO_BATCH). Si le pilote n’autorise pas l’exécution des instructions de génération du jeu de résultats avec un tableau de paramètres, SQL_PARAM_ARRAY_SELECTS retourne SQL_PAS_NO_SELECT. Il s’agit d’une source de données spécifique si les tableaux de paramètres peuvent être utilisés avec d’autres types d’instructions, en particulier parce que l’utilisation de paramètres dans ces instructions serait spécifique à la source de données et ne suivra pas la syntaxe ODBC SQL.  
  
 Le tableau désigné par l’attribut d’instruction SQL_ATTR_PARAM_OPERATION_PTR peut être utilisé pour ignorer les lignes de paramètres. Si un élément du tableau a la valeur SQL_PARAM_IGNORE, le jeu de paramètres correspondant à cet élément est exclu de l’appel de **SQLExecute** ou **SQLExecDirect** . Le tableau désigné par l’attribut SQL_ATTR_PARAM_OPERATION_PTR est alloué et rempli par l’application et lu par le pilote. Si les lignes extraites sont utilisées comme paramètres d’entrée, les valeurs du tableau d’état des lignes peuvent être utilisées dans le tableau des opérations de paramètres.  
  
## <a name="error-processing"></a>Erreur lors du traitement  
 Si une erreur se produit lors de l’exécution de l’instruction, la fonction d’exécution retourne une erreur et définit la variable de numéro de ligne sur le numéro de la ligne contenant l’erreur. Elle est spécifique à la source de données, que toutes les lignes à l’exception de l’ensemble d’erreurs soient exécutées ou que toutes les lignes avant (mais pas après) soient exécutées. Étant donné qu’il traite des ensembles de paramètres, le pilote définit la mémoire tampon spécifiée par l’attribut d’instruction SQL_ATTR_PARAMS_PROCESSED_PTR sur le numéro de la ligne en cours de traitement. Si tous les jeux à l’exception de l’ensemble d’erreurs sont exécutés, le pilote définit cette mémoire tampon sur SQL_ATTR_PARAMSET_SIZE une fois toutes les lignes traitées.  
  
 Si l’attribut d’instruction SQL_ATTR_PARAM_STATUS_PTR a été défini, **SQLExecute** ou **SQLExecDirect** retourne le tableau d’état des paramètres *,* qui fournit l’état de chaque ensemble de paramètres. Le tableau d’état des paramètres est alloué par l’application et rempli par le pilote. Ses éléments indiquent si l’instruction SQL a été exécutée avec succès pour la ligne de paramètres ou si une erreur s’est produite lors du traitement de l’ensemble de paramètres. Si une erreur s’est produite, le pilote définit la valeur correspondante dans le tableau d’état des paramètres sur SQL_PARAM_ERROR et retourne SQL_SUCCESS_WITH_INFO. L’application peut vérifier le tableau d’État pour déterminer les lignes qui ont été traitées. À l’aide du numéro de ligne, l’application peut souvent corriger l’erreur et reprendre le traitement.  
  
 Le mode d’utilisation du tableau d’état des paramètres est déterminé par les options SQL_PARAM_ARRAY_ROW_COUNTS et SQL_PARAM_ARRAY_SELECTS retournées par un appel à **SQLGetInfo**. Pour les instructions **Insert**, **Update**et **Delete** , le tableau d’état des paramètres est renseigné avec des informations d’état si SQL_PARC_BATCH est retourné pour SQL_PARAM_ARRAY_ROW_COUNTS, mais pas si SQL_PARC_NO_BATCH est retourné. Pour les instructions **Select** , le tableau d’état des paramètres est renseigné si SQL_PAS_BATCH est retourné pour SQL_PARAM_ARRAY_SELECT, mais pas si SQL_PAS_NO_BATCH ou SQL_PAS_NO_SELECT est retourné.  
  
## <a name="data-at-execution-parameters"></a>Paramètres de données en cours d’exécution  
 Si l’une des valeurs du tableau longueur/indicateur est SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC (*longueur*), les données de ces valeurs sont envoyées avec **SQLPutData** de la façon habituelle. Les aspects suivants de ce processus portent un commentaire spécial, car ils ne sont pas évidents :  
  
-   Lorsque le pilote retourne SQL_NEED_DATA, il doit définir l’adresse de la variable de numéro de ligne sur la ligne pour laquelle il a besoin de données. Comme dans le cas à valeur unique, l’application ne peut pas faire d’hypothèses quant à l’ordre dans lequel le pilote demande des valeurs de paramètre dans un ensemble unique de paramètres. Si une erreur se produit dans l’exécution d’un paramètre de données en cours d’exécution, la mémoire tampon spécifiée par l’SQL_ATTR_PARAMS_PROCESSED_PTR attribut d’instruction est définie sur le numéro de la ligne sur laquelle l’erreur s’est produite, l’état de la ligne dans le tableau d’état de ligne spécifié par l’attribut d’instruction SQL_ATTR_PARAM_STATUS_PTR est défini sur SQL_PARAM_ERROR, et l’appel à **SQLExecute**, **SQLExecDirect**, **SQLParamData**ou **SQLPutData** SQL_ERROR retourne Le contenu de cette mémoire tampon n’est pas défini si **SQLExecute**, **SQLExecDirect**ou **SQLParamData** retournent SQL_STILL_EXECUTING.  
  
-   Étant donné que le pilote n’interprète pas la valeur de l’argument *ParameterValuePtr* de **SQLBindParameter** pour les paramètres de données en cours d’exécution, si l’application fournit un pointeur vers un tableau, **SQLParamData** n’extrait pas et ne retourne pas un élément de ce tableau à l’application. Au lieu de cela, elle retourne la valeur scalaire fournie par l’application. Cela signifie que la valeur retournée par **SQLParamData** n’est pas suffisante pour spécifier le paramètre pour lequel l’application doit envoyer des données ; l’application doit également prendre en compte le numéro de ligne actuel.  
  
     Lorsque seuls certains éléments d’un tableau de paramètres sont des paramètres de données en cours d’exécution, l’application doit passer l’adresse d’un tableau dans *ParameterValuePtr* qui contient des éléments pour tous les paramètres. Ce tableau est interprété normalement pour les paramètres qui ne sont pas des paramètres de données en cours d’exécution. Pour les paramètres de données en cours d’exécution, la valeur fournie par **SQLParamData** à l’application, qui pourrait normalement être utilisée pour identifier les données que le pilote demande sur cette occasion, est toujours l’adresse du tableau.
