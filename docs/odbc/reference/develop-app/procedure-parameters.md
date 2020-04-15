---
title: Paramètres de procédure (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 35d43ca7cf6e603d7dabca9eacf1e026daa753b7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306954"
---
# <a name="procedure-parameters"></a>Paramètres de procédure
Les paramètres dans les appels de procédure peuvent être des paramètres d’entrée, d’entrée/sortie ou de sortie. Ceci est différent des paramètres dans toutes les autres instructions SQL, qui sont toujours des paramètres d’entrée.  
  
 Les paramètres d’entrée sont utilisés pour envoyer des valeurs à la procédure. Supposons, par exemple, que le tableau Des pièces comporte des colonnes PartID, Description et Prix. La procédure InsertPart peut avoir un paramètre d’entrée pour chaque colonne dans le tableau. Par exemple :  
  
```  
{call InsertPart(?, ?, ?)}  
```  
  
 Un conducteur ne doit pas modifier le contenu d’un tampon d’entrée jusqu’à ce que **SQLExecDirect** ou **SQLExecute** retourne SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_INVALID_HANDLE ou SQL_NO_DATA. Le contenu du tampon d’entrée ne doit pas être modifié pendant que **SQLExecDirect** ou **SQLExecute** retourne SQL_NEED_DATA ou SQL_STILL_EXECUTING.  
  
 Les paramètres d’entrée/sortie sont utilisés à la fois pour envoyer des valeurs aux procédures et récupérer les valeurs des procédures. L’utilisation du même paramètre qu’une entrée et un paramètre de sortie tend à être déroutante et doit être évitée. Supposons, par exemple, qu’une procédure accepte une pièce d’identité de commande et que l’identité du client. Cela peut être défini avec un seul paramètre d’entrée/sortie :  
  
```  
{call GetCustID(?)}  
```  
  
 Il pourrait être préférable d’utiliser deux paramètres : un paramètre d’entrée pour l’ID de commande et un paramètre de sortie ou d’entrée/sortie pour l’ID client :  
  
```  
{call GetCustID(?, ?)}  
```  
  
 Les paramètres de sortie sont utilisés pour récupérer la valeur de retour de procédure et pour récupérer les valeurs des arguments de procédure; procédures que les valeurs de retour sont parfois connus sous le nom *de fonctions*. Supposons, par exemple, que la procédure **GetCustID** vient de mentionner renvoie une valeur qui indique si elle a été en mesure de trouver l’ordre. Dans l’appel suivant, le premier paramètre est un paramètre de sortie utilisé pour récupérer la valeur de retour de procédure, le deuxième paramètre est un paramètre d’entrée utilisé pour spécifier l’ID de commande, et le troisième paramètre est un paramètre de sortie utilisé pour récupérer l’ID du client :  
  
```  
{? = call GetCustID(?, ?)}  
```  
  
 Les conducteurs gèrent les valeurs pour les paramètres d’entrée et d’entrée/sortie dans les procédures qui ne sont pas différents des paramètres d’entrée dans d’autres énoncés SQL. Lorsque l’instruction est exécutée, ils récupèrent les valeurs des variables liées à ces paramètres et les envoient à la source de données.  
  
 Une fois la déclaration exécutée, les conducteurs stockent les valeurs retournées des paramètres d’entrée/sortie et de sortie dans les variables liées à ces paramètres. Ces valeurs retournées ne sont pas garanties d’être fixées jusqu’à ce que tous les résultats retournés par la procédure ont été récupérés et **SQLMoreResults** est retourné SQL_NO_DATA. Si l’exécution de l’instruction entraîne une erreur, le contenu du tampon de paramètres d’entrée/sortie ou le paramètre de sortie n’est pas défini.  
  
 Une demande appelle **SQLProcedure** pour déterminer si une procédure a une valeur de retour. Il appelle **SQLProcedureColumns** pour déterminer le type (valeur de retour, entrée, entrée/sortie, ou sortie) de chaque paramètre de procédure.
