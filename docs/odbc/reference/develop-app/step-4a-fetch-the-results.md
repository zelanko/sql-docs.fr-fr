---
title: 'Étape 4a : Obtenez les résultats Microsoft Docs'
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
ms.openlocfilehash: c4f810e5c42b54ec871c233ab498936abae610dc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302970"
---
# <a name="step-4a-fetch-the-results"></a>Étape 4a : Extraire les résultats
L’étape suivante consiste à obtenir les résultats, comme le montre l’illustration suivante.  
  
 ![Présente l'extraction de résultats dans une application ODBC](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 Si la déclaration exécutée dans « Étape 3 : Construire et exécuter une déclaration SQL » était une déclaration **SELECT** ou une fonction de catalogue, l’application appelle **d’abord SQLNumResultCols** pour déterminer le nombre de colonnes dans l’ensemble de résultats. Cette étape n’est pas nécessaire si l’application connaît déjà le nombre de colonnes de jeu de résultat, par exemple lorsque l’instruction SQL est codée en dur dans une application verticale ou personnalisée.  
  
 Ensuite, l’application récupère le nom, le type de données, la précision et l’échelle de chaque colonne d’ensemble de résultats avec **SQLDescribeCol**. Encore une fois, ce n’est pas nécessaire pour les applications telles que les applications verticales et personnalisées qui connaissent déjà ces informations. L’application transmet ces informations à **SQLBindCol**, qui lie une variable d’application à une colonne dans l’ensemble de résultats.  
  
 L’application appelle maintenant **SQLFetch** pour récupérer la première rangée de données et placer les données de cette ligne dans les variables liées à **SQLBindCol**. S’il y a de longues données dans la rangée, il appelle ensuite **SQLGetData** pour récupérer ces données. L’application continue d’appeler **SQLFetch** et **SQLGetData** pour récupérer des données supplémentaires. Une fois qu’il a fini d’aller chercher des données, il appelle **SQLCloseCursor** pour fermer le curseur.  
  
 Pour une description complète des résultats de récupération, voir [les résultats de récupération (de base)](../../../odbc/reference/develop-app/retrieving-results-basic.md) et la récupération des résultats [(avancés).](../../../odbc/reference/develop-app/retrieving-results-advanced.md)  
  
 L’application revient maintenant à « Étape 3 : Construire et exécuter une déclaration SQL » pour exécuter une autre déclaration dans la même transaction; ou le produit de « Étape 5 : Engagez la transaction » pour valider ou annuler la transaction.
