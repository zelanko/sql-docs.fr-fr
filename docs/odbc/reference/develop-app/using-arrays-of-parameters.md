---
title: À l’aide de tableaux de paramètres | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 7ff4a76c38f04c7b9b12842ef800bc8a26a27ed9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63312519"
---
# <a name="using-arrays-of-parameters"></a>Utilisation de tableaux de paramètres
Pour utiliser des tableaux de paramètres, l’application appelle **SQLSetStmtAttr** avec un *attribut* argument de SQL_ATTR_PARAMSET_SIZE pour spécifier le nombre de jeux de paramètres. Il appelle **SQLSetStmtAttr** avec un *attribut* argument de SQL_ATTR_PARAMS_PROCESSED_PTR pour spécifier l’adresse d’une variable dans laquelle le pilote peut retourner le nombre de jeux de paramètres traités, erreur y compris des jeux. Il appelle **SQLSetStmtAttr** avec un *attribut* argument de SQL_ATTR_PARAM_STATUS_PTR pour pointer vers un tableau dans lequel retourner les informations d’état pour chaque ligne de valeurs de paramètre. Le pilote stocke ces adresses dans la structure que de l’instruction il tient à jour.  
  
> [!NOTE]  
>  Dans ODBC 2. *x*, **SQLParamOptions** a été appelé pour spécifier plusieurs valeurs pour un paramètre. Dans ODBC 3. *x*, l’appel à **SQLParamOptions** a été remplacé par des appels à **SQLSetStmtAttr** pour définir les attributs SQL_ATTR_PARAMSET_SIZE et SQL_ATTR_PARAMS_PROCESSED_ARRAY .  
  
 Avant d’exécuter l’instruction, l’application définit la valeur de chaque élément de chaque tableau lié. Lorsque l’instruction est exécutée, le pilote utilise les informations stockée pour récupérer les valeurs de paramètre et les envoyer à la source de données ; Si possible, le pilote doit envoyer ces valeurs sous forme de tableaux. Bien que l’utilisation de tableaux de paramètres est mieux implémentée par l’exécution de l’instruction SQL avec tous les paramètres dans le tableau avec un seul appel à la source de données, cette fonctionnalité n’est pas largement disponible dans le SGBD dès aujourd'hui. Toutefois, les pilotes peuvent la simuler en exécutant une instruction SQL plusieurs fois, chacun avec un ensemble unique de paramètres.  
  
 Avant d’une application utilise des tableaux de paramètres, il doit être sûr qu’ils sont pris en charge par les pilotes utilisés par l’application. Pour ce faire, deux possibilités s'offrent à vous :  
  
-   Utiliser uniquement les pilotes prennent en charge les tableaux de paramètres. L’application peut coder en dur les noms de ces pilotes, ou l’utilisateur peut être invité à utiliser uniquement ces pilotes. Applications personnalisées et des applications verticales utilisent généralement un ensemble limité de pilotes.  
  
-   Vérification de la prise en charge des tableaux de paramètres au moment de l’exécution. Un pilote prend en charge les tableaux de paramètres s’il est possible d’affecter à l’attribut d’instruction SQL_ATTR_PARAMSET_SIZE une valeur supérieure à 1. Applications génériques et des applications verticales couramment recherchent prise en charge des tableaux de paramètres en cours d’exécution.  
  
 La disponibilité des nombres de lignes et des jeux de résultats dans l’exécution paramétrable peut être déterminée en appelant **SQLGetInfo** avec les options SQL_PARAM_ARRAY_ROW_COUNTS et SQL_PARAM_ARRAY_SELECTS. Pour **insérer**, **mise à jour**, et **supprimer** instructions, l’option SQL_PARAM_ARRAY_ROW_COUNTS indique si le nombre de lignes individuelles (une pour chaque jeu de paramètres) est disponible (SQL_PARC_BATCH) ou si le nombre de lignes sont ajoutées à un (SQL_PARC_NO_BATCH). Pour **sélectionnez** instructions, l’option SQL_PARAM_ARRAY_SELECTS indique si un jeu de résultats est disponible pour chaque jeu de paramètres (SQL_PAS_BATCH) ou si un jeu de résultats est disponible (SQL_PAS_NO_BATCH). Si le pilote n’autorise pas les instructions de génération de jeu de résultats doit être exécuté avec un tableau de paramètres, SQL_PARAM_ARRAY_SELECTS retourne SQL_PAS_NO_SELECT. Il est spécifique à la source de données si les tableaux de paramètres peuvent être utilisées avec d’autres types d’instructions, en particulier, car l’utilisation de paramètres dans ces instructions spécifiques à la source de données et suivez pas grammaire SQL ODBC.  
  
 Le tableau vers lequel pointé l’attribut d’instruction SQL_ATTR_PARAM_OPERATION_PTR peut servir à ignorer les lignes de paramètres. Si un élément du tableau est défini sur SQL_PARAM_IGNORE, le jeu de paramètres correspondant à cet élément est exclu de la **SQLExecute** ou **SQLExecDirect** appeler. Du tableau pointé par l’attribut SQL_ATTR_PARAM_OPERATION_PTR est alloué et rempli par l’application et lues par le pilote. Si les lignes extraites sont utilisés comme paramètres d’entrée, les valeurs du tableau d’état de ligne peuvent être utilisées dans le tableau d’opération de paramètres.  
  
## <a name="error-processing"></a>Erreur lors du traitement  
 Si une erreur se produit lors de l’exécution de l’instruction, la fonction de l’exécution retourne une erreur et définit la variable de numéro de ligne sur le numéro de la ligne contenant l’erreur. Il est spécifique à la source de données si toutes les lignes sauf l’ensemble de l’erreur sont exécutées ou si toutes les lignes avant (mais pas après) l’ensemble de l’erreur sont exécutées. Étant donné qu’il traite des jeux de paramètres, le pilote définit la mémoire tampon spécifiée par l’attribut d’instruction SQL_ATTR_PARAMS_PROCESSED_PTR pour le numéro de la ligne en cours de traitement. Si tous les jeux excepté l’ensemble de l’erreur sont exécutées, le pilote affecte cette mémoire tampon SQL_ATTR_PARAMSET_SIZE après que toutes les lignes sont traitées.  
  
 Si l’attribut d’instruction SQL_ATTR_PARAM_STATUS_PTR a été défini, **SQLExecute** ou **SQLExecDirect** retourne le *tableau d’état de paramètre,* qui fournit l’état chaque ensemble de paramètres. Le tableau d’état de paramètre doit être alloué par l’application et rempli par le pilote. Ses éléments indiquent si l’instruction SQL a été exécutée avec succès pour la ligne de paramètres ou si une erreur s’est produite lors du traitement de l’ensemble des paramètres. Si une erreur s’est produite, le pilote définit la valeur correspondante dans le tableau d’état de paramètre à SQL_PARAM_ERROR et retourne SQL_SUCCESS_WITH_INFO. L’application peut vérifier le tableau d’état pour déterminer les lignes qui ont été traités. Utilisez le numéro de ligne, l’application peut souvent corriger l’erreur et reprendre le traitement.  
  
 Comment le tableau de statut de paramètre est utilisé est déterminé par les options SQL_PARAM_ARRAY_ROW_COUNTS et SQL_PARAM_ARRAY_SELECTS retournées par un appel à **SQLGetInfo**. Pour **insérer**, **mise à jour**, et **supprimer** instructions, le tableau d’état de paramètres est rempli avec les informations d’état si SQL_PARC_BATCH est retournée pour SQL_PARAM_ARRAY_ ROW_COUNTS, mais pas si SQL_PARC_NO_BATCH est retourné. Pour **sélectionnez** instructions, le tableau d’état de paramètre est renseigné si SQL_PAS_BATCH est retournée pour SQL_PARAM_ARRAY_SELECT, mais pas si SQL_PAS_NO_BATCH ou SQL_PAS_NO_SELECT est retourné.  
  
## <a name="data-at-execution-parameters"></a>Paramètres de Data-at-Execution  
 Si une des valeurs dans le tableau de longueur / d’indicateur est SQL_DATA_AT_EXEC ou le résultat de la SQL_LEN_DATA_AT_EXEC (*longueur*) (macro), les données pour ces valeurs sont envoyées avec **SQLPutData** à l’accoutumée. Les aspects suivants de ce processus portent les commentaires spéciaux, car ils ne sont pas immédiatement évidents :  
  
-   Lorsque le pilote retourne SQL_NEED_DATA, il doit définir l’adresse de la variable de numéro de ligne à la ligne pour laquelle il a besoin de données. Comme dans le cas d’une valeur unique, l’application ne peut pas faire d’hypothèses concernant l’ordre dans lequel le pilote demandera des valeurs de paramètre dans un seul ensemble de paramètres. Si une erreur se produit dans l’exécution d’un paramètre data-at-execution, la mémoire tampon spécifiée par l’attribut d’instruction SQL_ATTR_PARAMS_PROCESSED_PTR est défini sur le nombre de la ligne sur laquelle l’erreur s’est produite, l’état de la ligne dans le tableau d’état de ligne spécifié par l’attribut d’instruction SQL_ATTR_PARAM_STATUS_PTR est définie à SQL_PARAM_ERROR et l’appel à **SQLExecute**, **SQLExecDirect**, **SQLParamData**, ou  **SQLPutData** retourne SQL_ERROR. Le contenu de cette mémoire tampon n’est pas défini si **SQLExecute**, **SQLExecDirect**, ou **SQLParamData** retourner SQL_STILL_EXECUTING.  
  
-   Étant donné que le pilote n’interprète pas la valeur dans le *ParameterValuePtr* argument de **SQLBindParameter** pour les paramètres de data-at-execution, si l’application fournit un pointeur vers un tableau,  **SQLParamData** ne pas extraire et retourner un élément de ce tableau à l’application. Au lieu de cela, elle retourne que la valeur scalaire de l’application avait fourni. Cela signifie que la valeur retournée par **SQLParamData** est insuffisant spécifier le paramètre pour lequel l’application doit envoyer des données ; l’application doit également prendre en compte le nombre actuel de la ligne.  
  
     Lorsque seuls certains des éléments du tableau de paramètres sont les paramètres de data-at-execution, l’application doit passer l’adresse d’un tableau dans *ParameterValuePtr* qui contient les éléments de tous les paramètres. Ce tableau est interprété normalement pour les paramètres qui ne sont pas des paramètres de data-at-execution. Pour les paramètres de data-at-execution, la valeur qui **SQLParamData** fournit à l’application, qui peut normalement être utilisée pour identifier les données que le pilote demande à cette occasion, est toujours l’adresse du tableau.
