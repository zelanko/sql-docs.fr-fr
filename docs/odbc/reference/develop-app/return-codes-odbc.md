---
title: ODBC de Codes de retour | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e5f780f9abc47a367a1825d51b12159292ace5da
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020423"
---
# <a name="return-codes-odbc"></a>Codes de retour dans ODBC
Chaque fonction ODBC retourne un code, connu sous le nom son *code de retour,* qui indique la réussite ou l’échec de la fonction globale. La logique du programme repose en général sur des codes de retour.  
  
 Par exemple, ce qui suit code appelle **SQLFetch** pour récupérer les lignes dans un jeu de résultats. Il vérifie le code de retour de la fonction pour déterminer si la fin du jeu de résultats a été atteinte (SQL_NO_DATA), si les informations d’avertissement a été retournées (SQL_SUCCESS_WITH_INFO), ou si une erreur s’est produite (SQL_ERROR).  
  
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
|SQL_SUCCESS|Fonction s’est terminée correctement. L’application appelle **SQLGetDiagField** pour récupérer des informations supplémentaires à partir de l’enregistrement d’en-tête.|  
|SQL_SUCCESS_WITH_INFO|Fonction s’est terminée avec succès, éventuellement avec une erreur non fatale (avertissement). L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires.|  
|SQL_ERROR|Échec de la fonction. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires. Le contenu de tous les arguments à la fonction de sortie n’est pas défini.|  
|SQL_INVALID_HANDLE|Fonction a échoué en raison d’un handle d’environnement, connexion, instruction ou descripteur non valide. Cela indique une erreur de programmation. Aucune information supplémentaire n’est disponible à partir de **SQLGetDiagRec** ou **SQLGetDiagField**. Ce code est renvoyé uniquement lorsque le handle est un pointeur null ou le type est incorrect, par exemple lorsqu’un descripteur d’instruction est passé pour un argument qui nécessite un handle de connexion.|  
|SQL_NO_DATA|Plus aucune donnée n’était disponible. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires. Un ou plusieurs enregistrements d’état définies par le pilote dans la classe 02xxx peuvent être renvoyés. **Remarque :**  Dans ODBC 2. *x*, cela retourne le code s’appelait SQL_NO_DATA_FOUND.|  
|SQL_NEED_DATA|Plus de données est nécessaire, par exemple lorsque les données de paramètre sont envoyées au moment de l’exécution ou les informations de connexion supplémentaires sont nécessaires. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires, le cas échéant.|  
|SQL_STILL_EXECUTING|Une fonction qui a été démarrée en mode asynchrone est en cours d’exécution. L’application appelle **SQLGetDiagRec** ou **SQLGetDiagField** pour récupérer des informations supplémentaires, le cas échéant.|
