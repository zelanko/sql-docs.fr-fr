---
description: 'Étape 4a : Extraire les résultats'
title: 'Étape 4a : extraire les résultats | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 91a81809d07faafac6511bb5ec96c97d4f59d654
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491356"
---
# <a name="step-4a-fetch-the-results"></a>Étape 4a : Extraire les résultats
L’étape suivante consiste à extraire les résultats, comme indiqué dans l’illustration suivante.  
  
 ![Présente l'extraction de résultats dans une application ODBC](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 Si l’instruction exécutée à l’étape 3 : générer et exécuter une instruction SQL est une instruction **Select** ou une fonction de catalogue, l’application appelle d’abord **SQLNumResultCols** pour déterminer le nombre de colonnes dans le jeu de résultats. Cette étape n’est pas nécessaire si l’application connaît déjà le nombre de colonnes de jeu de résultats, par exemple lorsque l’instruction SQL est codée en dur dans une application verticale ou personnalisée.  
  
 Ensuite, l’application récupère le nom, le type de données, la précision et l’échelle de chaque colonne de jeu de résultats avec **SQLDescribeCol**. Là encore, cela n’est pas nécessaire pour les applications telles que les applications verticales et personnalisées qui connaissent déjà ces informations. L’application transmet ces informations à **SQLBindCol**, qui lie une variable d’application à une colonne du jeu de résultats.  
  
 L’application appelle désormais **SQLFetch** pour récupérer la première ligne de données et place les données de cette ligne dans les variables liées à **SQLBindCol**. Si la ligne contient des données de type long, elle appelle **SQLGetData** pour récupérer ces données. L’application continue à appeler **SQLFetch** et **SQLGetData** pour récupérer des données supplémentaires. Une fois la récupération des données terminée, elle appelle **SQLCloseCursor** pour fermer le curseur.  
  
 Pour obtenir une description complète de la récupération des résultats, consultez [récupération des résultats (de base)](../../../odbc/reference/develop-app/retrieving-results-basic.md) et [récupération des résultats (avancé)](../../../odbc/reference/develop-app/retrieving-results-advanced.md).  
  
 L’application retourne désormais à l’étape 3 : générer et exécuter une instruction SQL pour exécuter une autre instruction dans la même transaction. ou poursuit à « Step 5 : commit the transaction » pour valider ou restaurer la transaction.
