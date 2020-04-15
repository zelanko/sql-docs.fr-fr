---
title: SQLSetStmtOption (Desktop Database Drivers) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69b386aee3f95fd047f72510dce7658130ac7aa5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299409"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (pilotes pour les bases de données de poste de travail)

|*fOption*|Commentaires|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Le traitement asynchrone n’est pas pris en charge. Le SQL_ASYNC_ENABLE fOption retournera SQLSTATE S1C00 (Pilote non capable).|  
|SQL_KEYSET_SIZE|La seule taille valide de jeu-clé est 0, parce que les curseurs mixtes et dynamiques ne sont pas pris en charge. Si cette valeur est réglée à n’importe quel autre numéro, elle sera modifiée à 0 et l’appel retournera SQL_SUCCESS_WITH_INFO et SQLSTATE 01S02 (valeur d’option modifiée).|  
|SQL_MAX_ROWS|La seule taille valide de l’ensemble de rangées est 0, parce que les pilotes de base de données de bureau ne prennent pas en charge la limitation du nombre de lignes qui sont retournées. Si cette valeur est réglée à n’importe quel autre numéro, elle sera modifiée à 0 et l’appel retournera SQL_SUCCESS_WITH_INFO et SQLSTATE 01S02 (valeur d’option modifiée).|  
|SQL_QUERY_TIMEOUT|Non pris en charge.|  
|SQL_ROW_NUMBER|Non pris en charge.|  
|SQL_SIMULATE_CURSOR|Non pris en charge.|
