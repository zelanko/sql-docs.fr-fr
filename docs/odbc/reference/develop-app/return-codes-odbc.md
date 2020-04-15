---
title: Codes de retour ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- return codes [ODBC]
- diagnostic information [ODBC], return codes
ms.assetid: e893b719-4392-476f-911a-5ed6da6f7e94
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 15e434025ed1201ca61371c2fb88e70143e131a5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304310"
---
# <a name="return-codes-odbc"></a>Codes de retour dans ODBC
Chaque fonction dans ODBC renvoie un code, connu sous le nom de *code de retour,* qui indique le succès global ou l’échec de la fonction. La logique du programme repose en général sur des codes de retour.  
  
 Par exemple, le code suivant appelle **SQLFetch** pour récupérer les lignes dans un ensemble de résultats. Il vérifie le code de retour de la fonction pour déterminer si la fin de l’ensemble de résultat a été atteinte (SQL_NO_DATA), si des informations d’avertissement ont été retournées (SQL_SUCCESS_WITH_INFO), ou si une erreur s’est produite (SQL_ERROR).  
  
```  
SQLRETURN   rc;  
SQLHSTMT    hstmt;  
  
while ((rc=SQLFetch(hstmt)) != SQL_NO_DATA) {  
   if (rc == SQL_SUCCESS_WITH_INFO) {  
      // Call function to display warning information.  
   } else if (rc == SQL_ERROR) {  
      // Call function to display error information.  
      break;  
   }  
   // Process row.  
}  
```  
  
 Le code de retour SQL_INVALID_HANDLE indique toujours une erreur de programmation et ne doit jamais se rencontrer au moment de l'exécution. Tous les autres codes de retour fournissent des informations d'exécution, bien que SQL_ERROR puisse indiquer une erreur de programmation.  
  
 Le tableau suivant définit les codes de retour.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|SQL_SUCCESS|Fonction complétée avec succès. L’application appelle **SQLGetDiagField** pour récupérer des informations supplémentaires de l’enregistrement d’en-tête.|  
|SQL_SUCCESS_WITH_INFO|Fonction complétée avec succès, peut-être avec une erreur non mortelle (avertissement). L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires.|  
|SQL_ERROR|La fonction a échoué. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires. Le contenu de tous les arguments de sortie de la fonction sont indéfinis.|  
|SQL_INVALID_HANDLE|Fonction échouée en raison d’un environnement invalide, connexion, déclaration, ou poignée descripteur. Cela indique une erreur de programmation. Aucune information supplémentaire n’est disponible auprès de **SQLGetDiagRec** ou **SQLGetDiagField**. Ce code n’est retourné que lorsque la poignée est un pointeur nul ou est le mauvais type, par exemple quand une poignée de déclaration est adoptée pour un argument qui nécessite une poignée de connexion.|  
|SQL_NO_DATA|Plus aucune donnée n’était disponible. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires. Un ou plusieurs enregistrements d’état définis par le conducteur dans la classe 02xxx peuvent être retournés. **Note:**  À ODBC 2. *x*, ce code de retour a été nommé SQL_NO_DATA_FOUND.|  
|SQL_NEED_DATA|D’autres données sont nécessaires, par exemple lorsque des données de paramètres sont envoyées au moment de l’exécution ou que des informations de connexion supplémentaires sont nécessaires. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires, le cas échéant.|  
|SQL_STILL_EXECUTING|Une fonction qui a été commencée asynchronement est toujours en cours d’exécution. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires, le cas échéant.|
