---
title: 'Étape 3 : Générer et exécuter une instruction SQL | Microsoft Docs'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f0e369b74ef629c5fd7136b9098f579b5ad2b1b4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114262"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>Étape 3 : Construire et exécuter une instruction SQL
La troisième étape consiste à générer et exécuter une instruction SQL, comme indiqué dans l’illustration suivante. Les méthodes utilisées pour effectuer cette étape sont susceptibles de varier considérablement. L’application peut inviter l’utilisateur à entrer une instruction SQL, créez une instruction SQL en fonction de l’entrée d’utilisateur, ou utiliser une instruction SQL codées en dur. Pour plus d’informations, consultez [construire des instructions SQL](../../../odbc/reference/develop-app/constructing-sql-statements.md).  
  
 ![Illustre la création et l’exécution d’une instruction SQL](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 Si l’instruction SQL contient des paramètres, l’application lie les aux variables d’application en appelant **SQLBindParameter** pour chaque paramètre. Pour plus d’informations, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 Une fois l’instruction SQL est créée et tous les paramètres sont liés, l’instruction est exécutée avec **SQLExecDirect**. Si l’instruction doit être exécutée plusieurs fois, il peut être préparé avec **SQLPrepare** et sont exécutés avec **SQLExecute**. Pour plus d’informations, consultez [en exécutant une instruction](../../../odbc/reference/develop-app/executing-a-statement.md).  
  
 L’application peut également renoncer complètement l’exécution une instruction SQL et à la place appeler une fonction pour retourner un jeu de résultats contenant des informations de catalogue, telles que les colonnes disponibles ou les tables. Pour plus d’informations, consultez [utilise des données de catalogue](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Action suivante de l’application varie selon le type d’instruction SQL exécutée.  
  
|Type d’instruction SQL|Passez à|  
|---------------------------|----------------|  
|**Sélectionnez** ou de catalogue (fonction)|[Étape 4 a : Extraire les résultats](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**Mise à jour**, **supprimer**, ou **insérer**|[Étape 4 b : Extraire le nombre de lignes](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|Toutes les autres instructions SQL|Étape 3 : Générer et exécuter une instruction SQL (cette rubrique) ou [étape 5 : Valider la Transaction](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
