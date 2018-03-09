---
title: SQLSetScrollOptions (le pilote ODBC Visual FoxPro) | Documents Microsoft
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
helpviewer_keywords: SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 43f92a786bf2c4d77ad18c7ed6391abd4eff933d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : partielle  
  
 Conformité d’API ODBC : Niveau 2  
  
 Définit les options qui contrôlent le comportement des curseurs associé à un descripteur d’instruction, *hstmt*.  
  
 Le pilote ODBC Visual FoxPro prend en charge uniquement la valeur SQL_CONCUR_READ_ONLY ; Il ne prend pas en charge la *fConcurrency* SQL_CONCUR_ROWVER de valeur. Le pilote convertit SQL_KEYSET_SIZE type SQL_CURSOR_DYNAMIC et SQL_CURSOR_KEYSET_DRIVEN SQL_SCROLL_STATIC avec l’avertissement ODBC_01S02.  
  
 Pour plus d’informations, consultez [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) dans les *de référence du programmeur ODBC*.
