---
description: 'Étape 3 : Construire et exécuter une instruction SQL'
title: 'Étape 3 : générer et exécuter une instruction SQL | Microsoft Docs'
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
ms.openlocfilehash: cf99649ca84ab557457a1fb067e06188552b6aad
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461351"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>Étape 3 : Construire et exécuter une instruction SQL
La troisième étape consiste à générer et exécuter une instruction SQL, comme indiqué dans l’illustration suivante. Les méthodes utilisées pour effectuer cette étape sont susceptibles de varier considérablement. L’application peut inviter l’utilisateur à entrer une instruction SQL, générer une instruction SQL basée sur l’entrée de l’utilisateur ou utiliser une instruction SQL codée en dur. Pour plus d’informations, consultez [construction d’instructions SQL](../../../odbc/reference/develop-app/constructing-sql-statements.md).  
  
 ![Présente la génération et l'exécution d'une instruction SQL](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 Si l’instruction SQL contient des paramètres, l’application les lie aux variables d’application en appelant **SQLBindParameter** pour chaque paramètre. Pour plus d’informations, consultez [paramètres d’instruction](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 Après la génération de l’instruction SQL et la liaison de tous les paramètres, l’instruction est exécutée avec **SQLExecDirect**. Si l’instruction est exécutée plusieurs fois, elle peut être préparée avec **SQLPrepare** et exécutée avec **SQLExecute**. Pour plus d’informations, consultez [exécution d’une instruction](../../../odbc/reference/develop-app/executing-a-statement.md).  
  
 L’application peut également renoncer à exécuter entièrement une instruction SQL et appeler à la place une fonction pour retourner un jeu de résultats contenant des informations de catalogue, telles que les colonnes ou les tables disponibles. Pour plus d’informations, consultez [utilisation des données de catalogue](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 L’action suivante de l’application dépend du type d’instruction SQL exécutée.  
  
|Type d’instruction SQL|Passez à|  
|---------------------------|----------------|  
|Fonction **Select** ou Catalog|[Étape 4a : Extraire les résultats](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**Mettre à jour**, **supprimer**ou **Insérer**|[Étape 4b : Extraire le nombre de lignes](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|Toutes les autres instructions SQL|Étape 3 : générer et exécuter une instruction SQL (cette rubrique) ou [étape 5 : valider la transaction](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
