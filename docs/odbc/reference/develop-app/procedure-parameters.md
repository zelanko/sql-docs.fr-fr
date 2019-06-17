---
title: Paramètres de procédure | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- procedure parameters [ODBC]
ms.assetid: 54fd857e-d2cb-467d-bb72-121e67a8e88d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cab0fea9c39e4946122698f2476668464e556c1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62861529"
---
# <a name="procedure-parameters"></a>Paramètres de procédure
Paramètres dans les appels de procédure peuvent être entrés, d’entrée/sortient ou paramètres de sortie. Cela diffère des paramètres dans tous les autres instructions de SQL, qui sont toujours des paramètres d’entrée.  
  
 Paramètres d’entrée sont utilisés pour envoyer les valeurs à la procédure. Par exemple, supposons que la table des parties a colonnes PartID, Description et prix. La procédure InsertPart peut avoir un paramètre d’entrée pour chaque colonne dans la table. Exemple :  
  
```  
{call InsertPart(?, ?, ?)}  
```  
  
 Un pilote ne doit pas modifier le contenu du tampon d’entrée jusqu'à ce que **SQLExecDirect** ou **SQLExecute** retourne SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_NO_DATA. Le contenu de la mémoire tampon d’entrée ne doit pas être modifié pendant **SQLExecDirect** ou **SQLExecute** retourne SQL_NEED_DATA ou SQL_STILL_EXECUTING.  
  
 Paramètres d’entrée/sortie sont utilisés pour envoyer des valeurs à des procédures et récupérer des valeurs à partir de procédures. À l’aide de la même paramètre comme entrée et un paramètre de sortie a tendance à prêter à confusion et doit être évitée. Par exemple, supposons une procédure accepte un ID de commande et retourne l’ID du client. Cela peut être défini avec un seul paramètre d’entrée/sortie :  
  
```  
{call GetCustID(?)}  
```  
  
 Il peut être préférable d’utiliser deux paramètres : un paramètre d’entrée pour l’ID de commande et une sortie ou le paramètre d’entrée/sortie pour l’ID de client :  
  
```  
{call GetCustID(?, ?)}  
```  
  
 Paramètres de sortie sont utilisées pour récupérer la valeur de retour de procédure et récupérer des valeurs d’arguments de procédure ; les procédures qui retournent des valeurs sont parfois appelés *fonctions*. Par exemple, supposons que le **GetCustID** procédure précité retourne une valeur qui indique si elle a été en mesure de trouver l’ordre. Dans l’appel suivant, le premier paramètre est un paramètre de sortie utilisé pour récupérer la valeur de retour de procédure, le deuxième paramètre est un paramètre d’entrée permet de spécifier l’ID de commande, et le troisième paramètre est un paramètre de sortie utilisé pour récupérer l’ID de client :  
  
```  
{? = call GetCustID(?, ?)}  
```  
  
 Pilotes de gérer les valeurs d’entrée et d’entrée/sortient paramètres dans les procédures ne différemment des paramètres d’entrée dans d’autres instructions SQL. Lorsque l’instruction est exécutée, ils récupéreront les valeurs des variables liées à ces paramètres et les envoyer à la source de données.  
  
 Une fois que l’instruction a été exécutée, pilotes de stockent les valeurs renvoyées d’entrée/sortie et les paramètres de sortie dans les variables liées à ces paramètres. Ces retourné ne sont pas garantis que les valeurs pour définir jusqu'à ce que tous les résultats retournés par la procédure qui ont été extraites et **SQLMoreResults** a retourné SQL_NO_DATA. Si l’exécution de l’instruction entraîne une erreur, le contenu de la mémoire tampon de paramètre d’entrée/sortie ou de la mémoire tampon de paramètre de sortie n’est pas défini.  
  
 Une application appelle **SQLProcedure** pour déterminer si une procédure a une valeur de retour. Il appelle **SQLProcedureColumns** pour déterminer le type (valeur de retour, d’entrée, d’entrée/sortie ou de sortie) de chaque paramètre de procédure.
