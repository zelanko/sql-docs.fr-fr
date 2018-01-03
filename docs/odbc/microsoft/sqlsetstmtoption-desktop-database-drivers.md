---
title: "SQLSetStmtOption (pilotes d’ordinateur de bureau) | Documents Microsoft"
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
helpviewer_keywords: SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7257763af32ba14cfe68222467bcacc73c959e2f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
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
