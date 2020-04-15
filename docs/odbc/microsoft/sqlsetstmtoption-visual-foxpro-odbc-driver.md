---
title: SQLSetStmtOption (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb9677a9ccf307be847089c657964d96904eb20b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299399"
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC: Niveau 1  
  
 Définit les options liées à une poignée de relevé, *hstmt*.  
  
|*fOption*|Valeurs autorisées|Commentaires|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|Si vous tentez de définir cette *fOption*, le pilote retourne l’erreur: "Driver pas capable". Visual FoxPro ne prend pas en charge l’exécution asynchrone.|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMN ou une valeur 32 bits indiquant la longueur de la structure ou une instance d’un tampon dans lequel les colonnes de résultat seront liées.||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Le pilote ne permet pas SQL_CONCUR_ROWVER, parce que Visual FoxPro n’a pas de version en ligne basée sur des téléviseurs horaires.|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|Le conducteur n’autorise pas SQL_CURSOR_KEYSET_DRIVEN ou SQL_CURSOR_DYNAMIC; voir [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) pour plus d’informations.|  
|SQL_KEYSET_SIZE|Erreur: "Driver pas capable"|Visual FoxPro ne prend pas en charge le modèle de curseur keyset.|  
|SQL_MAX_LENGTH|0|Si vous tentez de définir cette valeur *fOption,* le pilote retourne l’erreur "Driver pas capable".|  
|SQL_MAX_ROWS|0|Si vous tentez de définir cette valeur *fOption,* le pilote retourne l’erreur "Driver pas capable".|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|Si vous tentez de définir cette valeur *fOption,* le pilote retourne l’erreur "Driver pas capable".|  
|SQL_RETRIEVE_DATA|SQL_RD_ON, SQL_RD_OFF||  
|SQL_ROWSET_SIZE|1 à 4 294 967 296||  
|SQL_SIMULATE_CURSOR|Erreur: "Driver pas capable"||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 Pour plus d’informations, voir [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) dans la *référence du programmeur ODBC*.
