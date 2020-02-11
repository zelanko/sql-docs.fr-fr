---
title: SQLSetStmtOption (pilotes de base de données de bureau) | Microsoft Docs
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
ms.openlocfilehash: 20043c96771bf888defa2c8fbeb028aaa18f5abc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67905345"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (pilotes pour les bases de données de poste de travail)

|*fOption*|Commentaires|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Le traitement asynchrone n’est pas pris en charge. Le SQL_ASYNC_ENABLE fOption retourne SQLSTATE S1C00 (pilote non conforme).|  
|SQL_KEYSET_SIZE|La seule taille de jeu de clés valide est 0, car les curseurs mixtes et dynamiques ne sont pas pris en charge. Si cette valeur est définie sur un autre nombre, elle est remplacée par 0 et l’appel retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01S02 ne (valeur d’option modifiée).|  
|SQL_MAX_ROWS|La seule taille d’ensemble de lignes valide est 0, car les pilotes de base de données de bureau ne prennent pas en charge la limitation du nombre de lignes retournées. Si cette valeur est définie sur un autre nombre, elle est remplacée par 0 et l’appel retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01S02 ne (valeur d’option modifiée).|  
|SQL_QUERY_TIMEOUT|Non pris en charge.|  
|SQL_ROW_NUMBER|Non pris en charge.|  
|SQL_SIMULATE_CURSOR|Non pris en charge.|
