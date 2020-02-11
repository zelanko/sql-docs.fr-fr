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
ms.openlocfilehash: f85512a1686df26cad739dc906e49cc5499f62e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912304"
---
# <a name="procedure-parameters"></a>Paramètres de procédure
Les paramètres dans les appels de procédure peuvent être des paramètres d’entrée, d’entrée/sortie ou de sortie. Cela diffère des paramètres dans toutes les autres instructions SQL, qui sont toujours des paramètres d’entrée.  
  
 Les paramètres d’entrée sont utilisés pour envoyer des valeurs à la procédure. Supposons, par exemple, que la table des pièces contient des colonnes PartId, description et Price. La procédure InsertPart peut avoir un paramètre d’entrée pour chaque colonne de la table. Par exemple :  
  
```  
{call InsertPart(?, ?, ?)}  
```  
  
 Un pilote ne doit pas modifier le contenu d’une mémoire tampon d’entrée jusqu’à ce que **SQLExecDirect** ou **SQLExecute** retourne SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_NO_DATA. Le contenu de la mémoire tampon d’entrée ne doit pas être modifié lorsque **SQLExecDirect** ou **SQLExecute** retourne SQL_NEED_DATA ou SQL_STILL_EXECUTING.  
  
 Les paramètres d’entrée/sortie sont utilisés à la fois pour envoyer des valeurs à des procédures et pour récupérer des valeurs à partir de procédures. L’utilisation du même paramètre qu’un paramètre d’entrée et un paramètre de sortie a tendance à être confus et doit être évitée. Supposons, par exemple, qu’une procédure accepte un ID de commande et renvoie l’ID du client. Cela peut être défini avec un seul paramètre d’entrée/sortie :  
  
```  
{call GetCustID(?)}  
```  
  
 Il peut être préférable d’utiliser deux paramètres : un paramètre d’entrée pour l’ID de commande et un paramètre de sortie ou d’entrée/sortie pour l’ID de client :  
  
```  
{call GetCustID(?, ?)}  
```  
  
 Les paramètres de sortie sont utilisés pour récupérer la valeur de retour de la procédure et pour récupérer des valeurs à partir des arguments de procédure. les procédures qui retournent des valeurs sont parfois appelées *fonctions*. Par exemple, supposons que la procédure **GetCustID** indiquée ici retourne une valeur qui indique si elle a pu trouver la commande. Dans l’appel suivant, le premier paramètre est un paramètre de sortie utilisé pour récupérer la valeur de retour de la procédure, le deuxième paramètre est un paramètre d’entrée utilisé pour spécifier l’ID d’ordre et le troisième paramètre est un paramètre de sortie utilisé pour récupérer l’ID de client :  
  
```  
{? = call GetCustID(?, ?)}  
```  
  
 Les pilotes gèrent les valeurs des paramètres d’entrée et d’entrée/sortie dans les procédures de la même façon que les paramètres d’entrée d’autres instructions SQL. Lorsque l’instruction est exécutée, elle récupère les valeurs des variables liées à ces paramètres et les envoie à la source de données.  
  
 Une fois l’instruction exécutée, les pilotes stockent les valeurs retournées des paramètres d’entrée/sortie et de sortie dans les variables liées à ces paramètres. Il n’est pas garanti que ces valeurs retournées soient définies tant que tous les résultats retournés par la procédure n’ont pas été récupérés et **SQLMoreResults** n’a pas retourné SQL_NO_DATA. Si l’exécution de l’instruction génère une erreur, le contenu de la mémoire tampon du paramètre d’entrée/sortie ou de la mémoire tampon du paramètre de sortie n’est pas défini.  
  
 Une application appelle **SQLProcedure** pour déterminer si une procédure a une valeur de retour. Elle appelle **SQLProcedureColumns** pour déterminer le type (valeur de retour, entrée, entrée/sortie ou sortie) de chaque paramètre de procédure.
