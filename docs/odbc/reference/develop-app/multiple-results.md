---
title: "Plusieurs résultats | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLMoreResults function [ODBC], multiple results
- row counts [ODBC]
- multiple results [ODBC]
- result sets [ODBC], multiple results
- SQLGetInfo function [ODBC], multiple results
ms.assetid: a3c32e4b-8fe7-4a33-ae39-ae664001f315
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e537a1a767d0789333659d1aa26e57e11c42195e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="multiple-results"></a>Plusieurs résultats
A *résultat* est un élément retourné par la source de données après une instruction est exécutée. ODBC comporte deux types de résultats : les jeux de résultats et des nombres de lignes. *Nombre de lignes* sont le nombre de lignes affectées par une instruction update, delete ou insert d’instruction. Les traitements, décrit dans [Batches of SQL Statements](../../../odbc/reference/develop-app/batches-of-sql-statements.md), peut générer plusieurs résultats.  
  
 Le tableau suivant répertorie les **SQLGetInfo** options une application utilise pour déterminer si une source de données retourne plusieurs résultats pour chaque type de traitement par lots. En particulier, une source de données peut retourner un nombre de lignes unique pour l’ensemble du lot d’instructions ou du nombre de lignes individuelles pour chaque instruction du lot. Dans le cas d’une instruction de résultat : génération d’un jeu exécutée avec un tableau de paramètres, la source de données peut retourner un seul jeu de résultats pour tous les jeux de paramètres ou différents jeux de résultats pour chaque jeu de paramètres.  
  
|Type de lot|Le nombre de lignes|Jeux de résultats|  
|----------------|----------------|-----------------|  
|Traitement explicite|SQL_BATCH_ROW_COUNT [a]|--[b].|  
|Procédure|SQL_BATCH_ROW_COUNT [a]|--[b].|  
|Tableaux de paramètres|SQL_PARAM_ARRAYS_ROW_COUNTS|SQL_PARAM_ARRAYS_SELECTS|  
  
 [a] ligne : génération d’un nombre d’instructions dans un lot peuvent être pris en charge, mais retourne le nombre de lignes non pris en charge. L’option SQL_BATCH_SUPPORT dans **SQLGetInfo** indique si les instructions de génération : le nombre de lignes sont autorisées dans les lots ; l’option SQL_BATCH_ROW_COUNTS indique si le nombre de ces lignes est retourné à l’application.  
  
 [b] lots explicites et procédures toujours retournent plusieurs jeux de résultats lorsqu’elles incluent plusieurs instructions de création de jeu de résultats.  
  
> [!NOTE]  
>  L’option SQL_MULT_RESULT_SETS introduite dans ODBC version 1.0 fournit uniquement les informations générales si plusieurs jeux de résultats peut être retournées. En particulier, il est défini à « Y » si les bits SQL_BS_SELECT_EXPLICIT ou SQL_BS_SELECT_PROC sont retournées pour SQL_BATCH_SUPPORT ou SQL_PAS_BATCH est retournée pour SQL_PARAM_ARRAYS_SELECT.  
  
 Pour traiter plusieurs résultats, une application appelle **SQLMoreResults**. Cette fonction ignore le résultat actuel et rend le résultat suivant disponible. Il retourne SQL_NO_DATA lorsque plus aucun résultat n’est disponibles. Par exemple, supposons que les instructions suivantes sont exécutées en tant que lot :  
  
```  
SELECT * FROM Parts WHERE Price > 100.00;  
UPDATE Parts SET Price = 0.9 * Price WHERE Price > 100.00  
```  
  
 Une fois ces instructions sont exécutées, l’application extrait les lignes du jeu de résultats créé par le **sélectionnez** instruction. Lorsqu’il n’est plus l’extraction de lignes, elle appelle **SQLMoreResults** pour rendre disponible le nombre de parties ont été repriced. Si nécessaire, **SQLMoreResults** ignore ces lignes, puis ferme le curseur. L’application appelle ensuite **SQLRowCount** pour déterminer le nombre de parties ont été repriced par le **mise à jour** instruction.  
  
 Il est spécifique au pilote, si l’instruction du lot entier est exécutée avant que les résultats soient disponibles. Dans certaines implémentations, c’est le cas ; dans d’autres, en appelant **SQLMoreResults** entraîne l’exécution de l’instruction suivante dans le lot.  
  
 Si une des instructions dans un lot échoue, **SQLMoreResults** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO. Si le lot a été abandonné lors de l’échec de l’instruction ou l’instruction a échoué était la dernière instruction du lot, **SQLMoreResults** retourne SQL_ERROR. Si le lot n’a pas été abandonné lors de l’échec de l’instruction et l’échec de l’instruction n’a pas la dernière instruction du lot, **SQLMoreResults** retourne SQL_SUCCESS_WITH_INFO. SQL_SUCCESS_WITH_INFO indique qu’au moins un jeu de résultats ou de nombre a été générée et que le lot n’a pas été abandonné.
