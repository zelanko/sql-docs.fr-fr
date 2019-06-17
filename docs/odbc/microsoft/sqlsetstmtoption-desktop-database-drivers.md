---
title: SQLSetStmtOption (pilotes pour les postes de travail de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 48dc5dff83e942b894548d44e3673c19ca0746c5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305791"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (pilotes pour les bases de données de poste de travail)

|*fOption*|Commentaires|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Traitement asynchrone n’est pas pris en charge. La fOption SQL_ASYNC_ENABLE retourne SQLSTATE S1C00 (non compatibles avec le pilote).|  
|SQL_KEYSET_SIZE|La taille du jeu de clés uniquement valide est 0, étant donné que mixte et les curseurs dynamiques ne sont pas pris en charge. Si cette valeur est définie à un nombre quelconque, elle est placée sur 0 et l’appel retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01 s 02 (valeur d’Option modifiée).|  
|SQL_MAX_ROWS|La taille de l’ensemble de lignes uniquement valide est 0, car les pilotes de base de données de bureau ne prennent pas en limitant le nombre de lignes qui sont retournées. Si cette valeur est définie à un nombre quelconque, elle est placée sur 0 et l’appel retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01 s 02 (valeur d’Option modifiée).|  
|SQL_QUERY_TIMEOUT|Non pris en charge.|  
|SQL_ROW_NUMBER|Non pris en charge.|  
|SQL_SIMULATE_CURSOR|Non pris en charge.|
