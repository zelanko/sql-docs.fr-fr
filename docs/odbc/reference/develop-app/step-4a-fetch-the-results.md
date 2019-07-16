---
title: 'Étape 4a : Extraire les résultats | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], fetching results
- fetches [ODBC], fetching results
ms.assetid: 77d30142-c774-473c-96fb-b364bb92ac60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3ab0bdabe8b2d66bf054f07ea51056a4044b4ae8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114188"
---
# <a name="step-4a-fetch-the-results"></a>Étape 4a : Extraire les résultats
L’étape suivante consiste à extraire les résultats, comme indiqué dans l’illustration suivante.  
  
 ![Présente l’extraction de résultats dans une application ODBC](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 Si l’instruction exécutée dans « étape 3 : Créer et exécuter une instruction SQL » a été un **sélectionnez** instruction ou une fonction de catalogue, l’application appelle d’abord **SQLNumResultCols** pour déterminer le nombre de colonnes dans le jeu de résultats. Cette étape n’est pas nécessaire si l’application a déjà connaît le nombre du résultat de définir les colonnes, par exemple lorsque l’instruction SQL est codé en dur dans une application verticale ou personnalisée.  
  
 Ensuite, l’application récupère le nom, type de données, précision et mise à l’échelle de chaque colonne du jeu de résultats avec **SQLDescribeCol**. Là encore, cela n’est pas nécessaire pour les applications telles que les applications verticales et personnalisées que vous connaissez déjà ces informations. L’application transmet ces informations à **SQLBindCol**, qui lie une variable d’application à une colonne dans le jeu de résultats.  
  
 L’application maintenant appelle **SQLFetch** pour récupérer la première ligne de données et de placer les données à partir de cette ligne dans les variables liées avec **SQLBindCol**. S’il existe des données de longue dans la ligne, il appelle ensuite **SQLGetData** pour récupérer ces données. L’application continue à appeler **SQLFetch** et **SQLGetData** pour récupérer des données supplémentaires. Après avoir terminé l’extraction de données, il appelle **SQLCloseCursor** pour fermer le curseur.  
  
 Pour obtenir une description complète de la récupération des résultats, consultez [récupération des résultats (Basic)](../../../odbc/reference/develop-app/retrieving-results-basic.md) et [récupération des résultats (Avancé)](../../../odbc/reference/develop-app/retrieving-results-advanced.md).  
  
 Maintenant l’application revienne à « étape 3 : Créer et exécuter une instruction SQL » pour exécuter une autre instruction dans la même transaction ; ou passe à « étape 5 : Valider la Transaction » pour valider ou restaurer la transaction.
