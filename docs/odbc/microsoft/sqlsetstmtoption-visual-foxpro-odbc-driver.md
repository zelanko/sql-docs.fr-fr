---
title: SQLSetStmtOption (pilote ODBC de Visual FoxPro) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d7bcecfbd880f53d1067fd68202b62c34fce398
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305821"
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau 1  
  
 Définit les options relatives à un descripteur d’instruction, *hstmt*.  
  
|*fOption*|Valeurs autorisées|Commentaires|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|Si vous tentez de définir cela *fOption*, le pilote retourne l’erreur : « Pilotes non compatibles avec ». Visual FoxPro ne prend pas en charge l’exécution asynchrone.|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMN ou une valeur de 32 bits indiquant la longueur de la structure ou une instance d’une mémoire tampon dans les résultats colonnes seront liés.||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Le pilote n’autorise pas SQL_CONCUR_ROWVER, car Visual FoxPro n’a pas de version de la ligne en fonction des horodatages.|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|Le pilote n’autorise pas SQL_CURSOR_KEYSET_DRIVEN ou type SQL_CURSOR_DYNAMIC ; consultez [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) pour plus d’informations.|  
|SQL_KEYSET_SIZE|Erreur : « Non compatibles avec le pilote »|Visual FoxPro ne prend pas en charge le modèle de curseur keyset.|  
|SQL_MAX_LENGTH|0|Si vous tentez de définir cela *fOption* valeur, le pilote retourne l’erreur « Non compatibles avec le pilote ».|  
|SQL_MAX_ROWS|0|Si vous tentez de définir cela *fOption* valeur, le pilote retourne l’erreur « Non compatibles avec le pilote ».|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|Si vous tentez de définir cela *fOption* valeur, le pilote retourne l’erreur « Non compatibles avec le pilote ».|  
|SQL_RETRIEVE_DATA|SQL_RD_ON, SQL_RD_OFF||  
|SQL_ROWSET_SIZE|1 à 4 294 967 296||  
|SQL_SIMULATE_CURSOR|Erreur : « Non compatibles avec le pilote »||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 Pour plus d’informations, consultez [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) dans le *de référence du programmeur ODBC*.
