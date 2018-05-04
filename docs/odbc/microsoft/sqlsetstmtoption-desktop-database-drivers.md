---
title: SQLSetStmtOption (pilotes d’ordinateur de bureau) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4689c14c5850b99c64379897bebb248f3aea4643
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
