---
title: Codes de retour ODBC | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304310"
---
# <a name="return-codes-odbc"></a>Codes de retour dans ODBC
Chaque fonction dans ODBC retourne un code, connu sous le nom de « *Code de retour »,* qui indique le succès ou l’échec global de la fonction. La logique du programme repose en général sur des codes de retour.  
  
 Par exemple, le code suivant appelle **SQLFetch** pour récupérer les lignes dans un jeu de résultats. Il vérifie le code de retour de la fonction pour déterminer si la fin du jeu de résultats a été atteinte (SQL_NO_DATA), si des informations d’avertissement ont été retournées (SQL_SUCCESS_WITH_INFO) ou si une erreur s’est produite (SQL_ERROR).  
  
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
|SQL_SUCCESS|La fonction s’est terminée avec succès. L’application appelle **SQLGetDiagField** pour récupérer des informations supplémentaires à partir de l’enregistrement d’en-tête.|  
|SQL_SUCCESS_WITH_INFO|La fonction s’est terminée avec succès, éventuellement avec une erreur récupérable (avertissement). L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires.|  
|SQL_ERROR|Échec de la fonction. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires. Le contenu de tous les arguments de sortie de la fonction n’est pas défini.|  
|SQL_INVALID_HANDLE|Échec de la fonction en raison d’un handle d’environnement, de connexion, d’instruction ou de descripteur non valide. Cela indique une erreur de programmation. Aucune information supplémentaire n’est disponible à partir de **SQLGetDiagRec** ou de **SQLGetDiagField**. Ce code est retourné uniquement lorsque le handle est un pointeur null ou qu’il s’agit d’un type incorrect, par exemple lorsqu’un descripteur d’instruction est passé pour un argument qui requiert un handle de connexion.|  
|SQL_NO_DATA|Aucune donnée supplémentaire n’était disponible. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires. Un ou plusieurs enregistrements d’État définis par le pilote dans la classe 02xxx peuvent être retournés. **Remarque :**  Dans ODBC 2. *x*, ce code de retour a été nommé SQL_NO_DATA_FOUND.|  
|SQL_NEED_DATA|Davantage de données sont nécessaires, par exemple lorsque des données de paramètre sont envoyées au moment de l’exécution ou lorsque des informations de connexion supplémentaires sont requises. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires, le cas échéant.|  
|SQL_STILL_EXECUTING|Une fonction qui a été démarrée de manière asynchrone est toujours en cours d’exécution. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires, le cas échéant.|
