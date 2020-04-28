---
title: SQLSetStmtOption (pilote ODBC Visual FoxPro) | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299399"
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau 1  
  
 Définit les options associées à un descripteur d’instruction, *HSTMT*.  
  
|*fOption*|Valeurs autorisées|Commentaires|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|Si vous tentez de définir ce *fOption*, le pilote retourne l’erreur : « pilote non conforme ». Visual FoxPro ne prend pas en charge l’exécution asynchrone.|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMN ou une valeur 32 bits indiquant la longueur de la structure ou une instance d’une mémoire tampon dans laquelle les colonnes de résultats seront liées.||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Le pilote n’autorise pas les SQL_CONCUR_ROWVER, car Visual FoxPro n’a pas de contrôle de version de ligne basé sur les horodateurs.|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|Le pilote n’autorise pas SQL_CURSOR_KEYSET_DRIVEN ou SQL_CURSOR_DYNAMIC ; Pour plus d’informations, consultez [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) .|  
|SQL_KEYSET_SIZE|Erreur : « pilote non conforme »|Visual FoxPro ne prend pas en charge le modèle de curseur de jeu de clés.|  
|SQL_MAX_LENGTH|0|Si vous tentez de définir cette valeur *fOption* , le pilote retourne l’erreur « pilote non conforme ».|  
|SQL_MAX_ROWS|0|Si vous tentez de définir cette valeur *fOption* , le pilote retourne l’erreur « pilote non conforme ».|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|Si vous tentez de définir cette valeur *fOption* , le pilote retourne l’erreur « pilote non conforme ».|  
|SQL_RETRIEVE_DATA|SQL_RD_ON, SQL_RD_OFF||  
|SQL_ROWSET_SIZE|1 à 4 294 967 296||  
|SQL_SIMULATE_CURSOR|Erreur : « pilote non conforme »||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 Pour plus d’informations, consultez [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) dans le *Guide de référence du programmeur ODBC*.
