---
title: Résultats multiples Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302409"
---
# <a name="multiple-results"></a>Résultats multiples
Un *résultat* est quelque chose retourné par la source de données après une déclaration est exécutée. ODBC a deux types de résultats : les ensembles de résultats et les nombres de lignes. *Les dénombrements* de lignes sont le nombre de lignes affectées par une mise à jour, une suppression ou une insérer. Les lots, [décrits dans Batches of SQL Statements](../../../odbc/reference/develop-app/batches-of-sql-statements.md), peuvent générer de multiples résultats.  
  
 Le tableau suivant répertorie les options **SQLGetInfo** qu’une application utilise pour déterminer si une source de données renvoie plusieurs résultats pour chaque type de lot. En particulier, une source de données peut retourner un nombre de lignes unique pour l’ensemble du lot d’instructions ou de nombres de lignes individuelles pour chaque relevé dans le lot. Dans le cas d’une déclaration génératrice de résultats exécutée avec un tableau de paramètres, la source de données peut retourner un ensemble de résultats unique pour tous les ensembles de paramètres ou d’ensembles de résultats individuels pour chaque ensemble de paramètres.  
  
|Type de lot|Nombres de rangées|Jeux de résultats|  
|----------------|----------------|-----------------|  
|Lot explicite|SQL_BATCH_ROW_COUNT[a]|--[b]|  
|Procédure|SQL_BATCH_ROW_COUNT[a]|--[b]|  
|Arrays de paramètres|SQL_PARAM_ARRAYS_ROW_COUNTS|SQL_PARAM_ARRAYS_SELECTS|  
  
 [a] Les énoncés générateurs de comptage dans un lot peuvent être pris en charge, mais le retour des comptes de ligne n’est pas pris en charge. L’option SQL_BATCH_SUPPORT dans **SQLGetInfo** indique si les relevés générateurs de nombres de rangées sont autorisés en lots; l’option SQL_BATCH_ROW_COUNTS indique si ces nombres de lignes sont retournés à la demande.  
  
 [b] Les lots et procédures explicites renvoient toujours les ensembles de résultats multiples lorsqu’ils incluent plusieurs énoncés générateurs de résultats.  
  
> [!NOTE]  
>  L’option SQL_MULT_RESULT_SETS introduite dans ODBC 1.0 ne fournit que des informations générales sur la possibilité de retourner plusieurs ensembles de résultats. En particulier, il est réglé sur le « Y » si les SQL_BS_SELECT_EXPLICIT ou les SQL_BS_SELECT_PROC bits sont retournés pour SQL_BATCH_SUPPORT ou si SQL_PAS_BATCH est retournée pour SQL_PARAM_ARRAYS_SELECT.  
  
 Pour traiter plusieurs résultats, une application appelle **SQLMoreResults**. Cette fonction écarte le résultat actuel et rend le prochain résultat disponible. Il revient SQL_NO_DATA quand plus de résultats ne sont disponibles. Supposons, par exemple, que les déclarations suivantes soient exécutées en lots :  
  
```  
SELECT * FROM Parts WHERE Price > 100.00;  
UPDATE Parts SET Price = 0.9 * Price WHERE Price > 100.00  
```  
  
 Une fois ces déclarations exécutées, l’application récupère des lignes à partir de l’ensemble de résultat créé par la déclaration **SELECT.** Quand il est fait aller chercher des rangées, il appelle **SQLMoreResults** pour mettre à disposition le nombre de pièces qui ont été réécoupées. Si nécessaire, **SQLMoreResults** jette des rangées non verrouillées et ferme le curseur. L’application appelle ensuite **SQLRowCount** pour déterminer combien de pièces ont été réécoupées par la déclaration **UPDATE.**  
  
 Il est spécifique au conducteur si l’ensemble de l’instruction de lot est exécuté avant que les résultats soient disponibles. Dans certaines mises en œuvre, c’est le cas; dans d’autres, appeler **SQLMoreResults** déclenche l’exécution de la déclaration suivante dans le lot.  
  
 Si l’une des déclarations d’un lot échoue, **SQLMoreResults** retournera soit SQL_ERROR, soit SQL_SUCCESS_WITH_INFO. Si le lot a été avorté lorsque la déclaration a échoué ou que la déclaration a échoué était la dernière déclaration dans le lot, **SQLMoreResults** retournera SQL_ERROR. Si le lot n’a pas été avorté lorsque la déclaration a échoué et que la déclaration a échoué n’était pas la dernière déclaration dans le lot, **SQLMoreResults** retournera SQL_SUCCESS_WITH_INFO. SQL_SUCCESS_WITH_INFO indique qu’au moins un ensemble de résultats ou un nombre a été généré et que le lot n’a pas été avorté.
