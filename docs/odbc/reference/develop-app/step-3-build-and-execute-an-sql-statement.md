---
title: 'Étape 3 : Construire et exécuter une déclaration SQL Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], building and executing statements
- SQL statements [ODBC], building and executing
ms.assetid: 133b8bd4-a3c8-4f7e-93c5-c05283c8e96f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8322cf5e7b4a91bfc5f5f0204cfb25fa4bdad92
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306830"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>Étape 3 : Construire et exécuter une instruction SQL
La troisième étape consiste à construire et à exécuter une déclaration SQL, comme le montre l’illustration suivante. Les méthodes utilisées pour effectuer cette étape sont susceptibles de varier énormément. L’application peut inciter l’utilisateur à entrer une déclaration SQL, construire une déclaration SQL basée sur l’entrée de l’utilisateur, ou utiliser une déclaration SQL codée en dur. Pour plus d’informations, voir [Construire des déclarations SQL](../../../odbc/reference/develop-app/constructing-sql-statements.md).  
  
 ![Présente la génération et l'exécution d'une instruction SQL](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 Si l’instruction SQL contient des paramètres, l’application les lie aux variables d’application en appelant **SQLBindParameter** pour chaque paramètre. Pour plus d’informations, voir [Paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 Une fois la déclaration SQL construite et tous les paramètres liés, la déclaration est exécutée avec **SQLExecDirect**. Si la déclaration sera exécutée plusieurs fois, elle peut être préparée avec **SQLPrepare** et exécutée avec **SQLExecute**. Pour plus d’informations, voir [Exécution d’une déclaration](../../../odbc/reference/develop-app/executing-a-statement.md).  
  
 L’application peut également renoncer à l’exécution d’une déclaration SQL tout à fait et au lieu d’appeler une fonction pour retourner un ensemble de résultat contenant des informations de catalogue, tels que les colonnes ou les tables disponibles. Pour plus d’informations, voir [Utilisations des données de catalogue](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 La prochaine action de l’application dépend du type de relevé SQL exécuté.  
  
|Type de déclaration SQL|Procéder à|  
|---------------------------|----------------|  
|**FONCTION SELECT** ou catalogue|[Étape 4a : Extraire les résultats](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**MISE À JOUR**, **SUPPRIMER**, OU **INSERT**|[Étape 4b : Extraire le nombre de lignes](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|Toutes les autres déclarations SQL|Étape 3 : Construire et exécuter une déclaration SQL (ce sujet) ou [étape 5 : Engagez la transaction](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
