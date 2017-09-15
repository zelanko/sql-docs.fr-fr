---
title: "SQLSetStmtOption (pilotes d’ordinateur de bureau) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d1f51805413056a06c6cee769920e1ad878abe5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (pilotes bureau de base de données)
|*fOption*|Commentaires|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Le traitement asynchrone n’est pas pris en charge. La fOption SQL_ASYNC_ENABLE retourne SQLSTATE S1C00 (non compatibles avec le pilote).|  
|SQL_KEYSET_SIZE|La taille du jeu de clés uniquement valide est 0, car mixte et les curseurs dynamiques ne sont pas pris en charge. Si cette valeur est définie à un nombre quelconque, il passe à 0 et l’appel retourne 01 s 02 SQL_SUCCESS_WITH_INFO et SQLSTATE (Option la valeur modifiée).|  
|SQL_MAX_ROWS|La taille de l’ensemble de lignes uniquement valide est 0, car les pilotes de base de données de bureau ne prennent pas en charge limitant le nombre de lignes qui sont retournées. Si cette valeur est définie à un nombre quelconque, il passe à 0 et l’appel retourne 01 s 02 SQL_SUCCESS_WITH_INFO et SQLSTATE (Option la valeur modifiée).|  
|SQL_QUERY_TIMEOUT|Non pris en charge.|  
|SQL_ROW_NUMBER|Non pris en charge.|  
|SQL_SIMULATE_CURSOR|Non pris en charge.|
