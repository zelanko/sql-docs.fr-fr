---
title: Résultats multiples | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d90414b631a7e81a7868ab7974b64ea84a0ea452
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302409"
---
# <a name="multiple-results"></a>Résultats multiples
Une *valeur est* retournée par la source de données après l’exécution d’une instruction. ODBC comporte deux types de résultats : les jeux de résultats et les nombres de lignes. Les *nombres* de lignes sont le nombre de lignes affectées par une instruction Update, Delete ou Insert. Les lots, décrits par [lots d’instructions SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md), peuvent générer plusieurs résultats.  
  
 Le tableau suivant répertorie les options **SQLGetInfo** qu’une application utilise pour déterminer si une source de données retourne plusieurs résultats pour chaque type de lot. En particulier, une source de données peut retourner un seul nombre de lignes pour l’ensemble du lot d’instructions ou des nombres de lignes individuels pour chaque instruction du lot. Dans le cas d’une instruction de génération de jeu de résultats exécutée avec un tableau de paramètres, la source de données peut retourner un seul jeu de résultats pour tous les jeux de paramètres ou tous les jeux de résultats individuels pour chaque ensemble de paramètres.  
  
|Type de lot|Nombre de lignes|Jeux de résultats|  
|----------------|----------------|-----------------|  
|Lot explicite|SQL_BATCH_ROW_COUNT [a]|--[b]|  
|Procédure|SQL_BATCH_ROW_COUNT [a]|--[b]|  
|Tableaux de paramètres|SQL_PARAM_ARRAYS_ROW_COUNTS|SQL_PARAM_ARRAYS_SELECTS|  
  
 [a] les instructions de génération de nombre de lignes dans un lot peuvent être prises en charge, mais le retour du nombre de lignes n’est pas pris en charge. L’option SQL_BATCH_SUPPORT dans **SQLGetInfo** indique si les instructions de génération de nombre de lignes sont autorisées dans les lots ; l’option SQL_BATCH_ROW_COUNTS indique si ces nombres de lignes sont retournés à l’application.  
  
 [b] les traitements et procédures explicites renvoient toujours plusieurs jeux de résultats lorsqu’ils incluent plusieurs instructions de génération de jeu de résultats.  
  
> [!NOTE]  
>  L’option SQL_MULT_RESULT_SETS introduite dans ODBC 1,0 fournit uniquement des informations générales indiquant si plusieurs jeux de résultats peuvent être retournés. En particulier, il est défini sur « Y » si le SQL_BS_SELECT_EXPLICIT ou SQL_BS_SELECT_PROC bits sont retournés pour SQL_BATCH_SUPPORT ou si SQL_PAS_BATCH est retourné pour SQL_PARAM_ARRAYS_SELECT.  
  
 Pour traiter plusieurs résultats, une application appelle **SQLMoreResults**. Cette fonction ignore le résultat actuel et rend le résultat suivant disponible. Elle retourne SQL_NO_DATA lorsqu’aucun autre résultat n’est disponible. Supposons, par exemple, que les instructions suivantes sont exécutées en tant que lot :  
  
```  
SELECT * FROM Parts WHERE Price > 100.00;  
UPDATE Parts SET Price = 0.9 * Price WHERE Price > 100.00  
```  
  
 Une fois ces instructions exécutées, l’application extrait des lignes du jeu de résultats créé par l’instruction **Select** . Lorsqu’il a terminé la récupération de lignes, il appelle **SQLMoreResults** pour mettre à disposition le nombre de parties qui ont été retarifées. Si nécessaire, **SQLMoreResults** ignore les lignes inrécupérées et ferme le curseur. L’application appelle ensuite **SQLRowCount** pour déterminer le nombre de parties retarifées par l’instruction **Update** .  
  
 Il est propre au pilote, que l’intégralité de l’instruction batch soit exécutée avant que les résultats ne soient disponibles. Dans certaines implémentations, c’est le cas ; dans d’autres, l’appel de **SQLMoreResults** déclenche l’exécution de l’instruction suivante dans le lot.  
  
 Si l’une des instructions d’un lot échoue, **SQLMoreResults** retourne soit SQL_ERROR, soit SQL_SUCCESS_WITH_INFO. Si le lot a été abandonné en cas d’échec de l’instruction ou si l’instruction failed était la dernière instruction du lot, **SQLMoreResults** renverra SQL_ERROR. Si le lot n’a pas été abandonné lorsque l’instruction a échoué et que l’instruction failed n’était pas la dernière instruction du lot, **SQLMoreResults** renverra SQL_SUCCESS_WITH_INFO. SQL_SUCCESS_WITH_INFO indique qu’au moins un jeu de résultats ou nombre a été généré et que le lot n’a pas été abandonné.
