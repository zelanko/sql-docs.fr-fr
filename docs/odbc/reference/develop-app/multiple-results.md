---
title: Plusieurs résultats | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLMoreResults function [ODBC], multiple results
- row counts [ODBC]
- multiple results [ODBC]
- result sets [ODBC], multiple results
- SQLGetInfo function [ODBC], multiple results
ms.assetid: a3c32e4b-8fe7-4a33-ae39-ae664001f315
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f8679bea49b63ffd5dc7164942b42ac9eed7e9ab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086364"
---
# <a name="multiple-results"></a>Résultats multiples
Un *résultat* est un élément retourné par la source de données après une instruction est exécutée. ODBC comporte deux types de résultats : jeux de résultats et des nombres de lignes. *Nombres de lignes* sont le nombre de lignes affectées par une mise à jour, supprimer, ou instruction insert. Lots, décrit dans [Batches of SQL Statements](../../../odbc/reference/develop-app/batches-of-sql-statements.md), peut générer plusieurs résultats.  
  
 Le tableau suivant répertorie les **SQLGetInfo** options utilisées par une application pour déterminer si une source de données retourne plusieurs résultats pour chaque type de traitement par lots. En particulier, une source de données peut retourner un nombre de lignes unique pour l’ensemble du lot d’instructions ou le nombre de lignes individuelles pour chaque instruction du lot. Dans le cas d’une instruction de résultat génératrice de jeu exécutée avec un tableau de paramètres, la source de données peut retourner un seul jeu de résultats pour tous les jeux de paramètres ou différents jeux de résultats pour chaque jeu de paramètres.  
  
|Type de lot|Nombre de lignes|Jeux de résultats|  
|----------------|----------------|-----------------|  
|Traitement explicite|SQL_BATCH_ROW_COUNT[a]|--[b]|  
|Procédure|SQL_BATCH_ROW_COUNT[a]|--[b]|  
|Tableaux de paramètres|SQL_PARAM_ARRAYS_ROW_COUNTS|SQL_PARAM_ARRAYS_SELECTS|  
  
 [a] ligne génératrice de nombre d’instructions dans un lot peuvent être pris en charge, mais le retour du nombre de lignes non pris en charge. L’option SQL_BATCH_SUPPORT dans **SQLGetInfo** indique si les instructions de génération de nombre de lignes sont autorisées par lots ; l’option SQL_BATCH_ROW_COUNTS indique si ces nombres de lignes sont retournées à l’application.  
  
 [b] lots explicites et procédures toujours retournent plusieurs jeux de résultats lorsqu’elles incluent plusieurs instructions de génération de jeu de résultats.  
  
> [!NOTE]  
>  L’option SQL_MULT_RESULT_SETS introduite dans ODBC 1.0 fournit uniquement des informations concernant si plusieurs jeux de résultats peut être retournées. En particulier, elle est définie à « Y » si les bits SQL_BS_SELECT_EXPLICIT ou SQL_BS_SELECT_PROC sont renvoyés pour SQL_BATCH_SUPPORT ou si SQL_PAS_BATCH est retournée pour SQL_PARAM_ARRAYS_SELECT.  
  
 Pour traiter plusieurs résultats, une application appelle **SQLMoreResults**. Cette fonction ignore le résultat actuel et rend le résultat suivant disponible. Il retourne SQL_NO_DATA lorsque plus aucun résultat n’est disponibles. Par exemple, supposons que les instructions suivantes sont exécutées en tant que lot :  
  
```  
SELECT * FROM Parts WHERE Price > 100.00;  
UPDATE Parts SET Price = 0.9 * Price WHERE Price > 100.00  
```  
  
 Une fois que ces instructions sont exécutées, l’application extrait les lignes du jeu de résultats créé par le **sélectionnez** instruction. Lorsqu’il n’est plus la récupération de lignes, il appelle **SQLMoreResults** pour rendre disponible le nombre d’éléments qui ont été repriced. Si nécessaire, **SQLMoreResults** ignore des lignes, puis ferme le curseur. L’application appelle ensuite **SQLRowCount** pour déterminer le nombre de parties ont été repriced par le **mise à jour** instruction.  
  
 Il est spécifique au pilote que l’instruction du lot entier est exécutée avant que les résultats soient disponibles. Dans certaines implémentations, c’est le cas ; dans d’autres, en appelant **SQLMoreResults** entraîne l’exécution de l’instruction suivante dans le lot.  
  
 Si une des instructions dans un lot échoue, **SQLMoreResults** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO. Si le lot a été abandonné lors de l’échec de l’instruction ou l’instruction ayant échouée était la dernière instruction du lot, **SQLMoreResults** retourne SQL_ERROR. Si le lot n’a pas été abandonné lors de l’échec de l’instruction et l’instruction en échec n’était pas la dernière instruction du lot, **SQLMoreResults** retourne SQL_SUCCESS_WITH_INFO. SQL_SUCCESS_WITH_INFO indique qu’au moins un jeu de résultats ou nombre a été généré et que le lot n’a pas été abandonné.
