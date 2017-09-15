---
title: SQLSetStmtOption (le pilote ODBC Visual FoxPro) | Documents Microsoft
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
- SQLSetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9374aed937aed17c0e1157eb6523f9b313473698
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau 1  
  
 Définit les options relatives à un descripteur d’instruction, *hstmt*.  
  
|*fOption*|Valeurs autorisées|Commentaires|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|Si vous essayez de définir cette *fOption*, le pilote retourne l’erreur : « Non compatibles avec le pilote ». Visual FoxPro ne prend pas en charge l’exécution asynchrone.|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMN ou une valeur de 32 bits indiquant la longueur de la structure ou une instance d’une mémoire tampon dans le résultat des colonnes seront liés.||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Le pilote n’autorise pas SQL_CONCUR_ROWVER, car Visual FoxPro n’a pas de version de la ligne en fonction des horodatages.|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|Le pilote n’autorise pas SQL_CURSOR_KEYSET_DRIVEN ou type SQL_CURSOR_DYNAMIC ; consultez [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) pour plus d’informations.|  
|SQL_KEYSET_SIZE|Erreur : « Driver non compatibles avec »|Visual FoxPro ne prend pas en charge le modèle de curseur de jeu de clés.|  
|SQL_MAX_LENGTH|0|Si vous essayez de définir cette *fOption* valeur, le pilote retourne l’erreur « Non compatibles avec le pilote ».|  
|SQL_MAX_ROWS|0|Si vous essayez de définir cette *fOption* valeur, le pilote retourne l’erreur « Non compatibles avec le pilote ».|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|Si vous essayez de définir cette *fOption* valeur, le pilote retourne l’erreur « Non compatibles avec le pilote ».|  
|SQL_RETRIEVE_DATA|SQL_RD_ON, SQL_RD_OFF||  
|SQL_ROWSET_SIZE|1 à 4 294 967 296||  
|SQL_SIMULATE_CURSOR|Erreur : « Driver non compatibles avec »||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 Pour plus d’informations, consultez [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) dans les *de référence du programmeur ODBC*.
